Eu estou colocando o dicionario `paths` em todos os notebooks, logo antes dos dicionarios `inputs` e `outputs`. Pensei que seria mais elegante deixar `paths` em um modulo separado, talvez um arquivo `paths.json`.
Com base nisso, tive outras ideias. 
Primeiramente, poderiamos ter uma função/script `.py` que gere `paths.json` automaticamente. A função receberia como parametro de entrada o caminho do arquivo `.py` para a pasta a partir da qual queremos os caminhos, o caminho do arquivo `.py` para a raiz do diretorio, e o caminho onde queremos salvar `paths.json`. 
Por exemplo:

```python
make_paths(origin="./", root="../", json_path="paths.json")
```  
Supondo que o arquivo `.py` esteja na pasta `code`, isso salvaria `paths.json` na pasta `code`, com os caminhos relativos das demais pastas do diretorio de trabalho para a pasta `code`. 
Como um dicionario, a estrutura base desse `paths.json` seria mais ou menos assim:

```python
paths = {
        "origin":{
                "base": "./"
        },
        "root":{
                "base": "../",
                "data":{
                        "base": "../data/",
                        "raw":{
                                "base": "../data/raw/"
                        },
                        "processed":{
                                "base": "../data/processed/"
                        },
                        "results":{
                                "base": "../data/results/"
                        }
                },
                "paper":{
                        "base": "../paper/",
                        "figures":{
                                "base": "../paper/figures/"
                        },
                        "variables":{
                                "base": "../paper/variables"
                        }
                }
        }    
}
```

Acredito que isso será bem util na automação da montagem do makefile. Eu pretendo deixar o makefile na raiz do diretorio. Para isso, acho que vai ajudar ter dois arquivos `paths.json`, um referente a pasta code, e um referente a raiz do repositorio.

Agora, sobre a função `get_path`, acho ela será necessaria. Imagine escrever:

```python
inputs = {
    "fabdem_ortho": paths["root"]["data"]["processed"]["dem"] + "fabdem_orthometric.nc",
    "fabdem_ellip": paths["root"]["data"]["processed"]["dem"] + "fabdem_ellipsoidal.nc",
    "srtm_ortho": paths["root"]["data"]["processed"]["dem"] + "srtm15plus_ortometrico.nc",
    "srtm_ellip": paths["root"]["data"]["processed"]["dem"] + "srtm15plus_elipsoidal.nc",
    "geoid_sam": paths["root"]["data"]["processed"]["geoid"] + "SAM_GEOID2023.nc"
}
```

horrivel. 

Melhor ter uma função `get_path`, mas quero que ela funcione dessa forma:

```python
processed_dem = get_path("root", "data", "processed", "dem")
processed_geoid = get_path("root", "data", "processed", "geoid")

inputs = {
    "fabdem_ortho": processed_dem + "fabdem_orthometric.nc",
    "fabdem_ellip": processed_dem + "fabdem_ellipsoidal.nc",
    "srtm_ortho": processed_dem + "srtm15plus_ortometrico.nc",
    "srtm_ellip": processed_dem + "srtm15plus_elipsoidal.nc",
    "geoid_sam": processed_geoid + "SAM_GEOID2023.nc"
}
```

Talves as funções `get_path` e `make_paths` poderião fazer parte de uma classe, juntamente com outras funções auxiliares: `add_path`, `print_paths`, `drop_path`, `clear_paths`, `redefine_paths` etc. 
Ao chamar a classe, será preciso definir `origin` e `root`. Isso já irrá gerar um arquivo `paths.json` automaticamente em `origin`, caso ainda não exista um. O arquivo `paths.json` ínicial pode ser gerado "vazio", por exemplo:

```json
{
     paths:{
             "origin":{
                     "base": "./"
             },
             "root":{
                     "base": "../"
             }    
           }
}
```

Usar a função `get_path`, pode automatimamente adicinar um caminho em `paths.json` a partir de "origin" ou "root"(provalbelmente chamendo a função `add_path`), caso o cominho ainda não exista. Assim `paths.json` será construido conforme for sendo usado.  


Eu tenho algumas ideias, quero que vc me ajude a implementar. Mas vamos bem devagar, quero fazer uma ferramenta que eu possa usar em outros projetos futuramente, e que também possa ser util para outras pessoas. Preciso entender o que estou fazendo.

Eu já criei essa classe `PathManager`, a principio minha ideia é que a criação do makefile seja um método dessa classe.

---

Estou terminando de tabular os inputs e outputs de cada notebook, para isso estou usando o método `get_path` da classe `PathManager`. Conforme uso `get_path`, uma arvore vai se construído no arquivo "paths.json".

Para começar, quero fazer uma melhoria. 
Vamos definir dois parâmetros para `get_path`: `path` e `file`. `path` deve ser uma tupla, sem limite de elementos, por exemplo:

`path = ("root", "data", "processed", "grav_data")`

Já `file` deve ser uma string unica, por exemplo:

`file = "filtered_grav_database.csv"`

Ao executar:

`pm.get_path(path = ("root", "data", "processed", "grav_data"), file = "filtered_grav_database.csv")`

A saída seria uma string: 

`"../data/processed/grav_data/filtered_grav_database.csv"´

Como está agora `get_path` retorna apenas o caminho das pastas, e eu estou concatenado o nome do arquivo separadamente. É importante que `file` seja opcional, as vezes eu preciso apenas do caminho da pasta.

A arvore de caminhos começa da seguinte forma: 

```python
paths = {
	"origin": {"base": "./"},
	"root": {"base": "../"}
}
```
Quando uso `get_path`, o código verifica se o caminho já foi registrado em `paths.json`, caso não, um novo caminho é adicionado. Por exemplo, se eu rodar:

```python
pm.get_path("root", "data", "raw", "geoid")
```

A arvore de caminhos vai ficar:

```python
paths = {
	"origin": {"base": "./"},
	"root": {"base": "../",
		"data": {"base": "../data/",
			"raw": {"base": "../data/raw/",
				"geoid": {"base": "../data/raw/geoid/"}
			}
		}
	}
}
```
O valor retornado por `get_path` equivale ao valor da chave `"base"` do ultimo nó.

Com a mudança que quero implementar, os arquivos tão vão ficar registrados em "paths.json". Por exemplo, ao rodar:

```python
pm.get_path(path = ("root", "data", "raw", "geoid"), file = "SAM_GEOID2023.txt")
```

A arvore de caminhos vai ficar:

```python
paths = {
	"origin": {"base": "./"},
	"root": {
		"base": "../",
		"data": {
			"base": "../data/",
			"raw": {
				"base": "../data/raw/",
				"geoid": {
					"base": "../data/raw/geoid/",
					"SAM_GEOID2023.txt": "../data/raw/geoid/SAM_GEOID2023.txt"
				}
			}
		}
	}
}
```

Quando o parâmetro `file` for passado para `get_path, a nova entrada na arvore será uma atribuição simples, não um novo dicionario como é padrão para as pastas.

Agora eu expliquei o quero fazer. Em seguida vou passar código da classe `PathManager`, e vc me ajuda a implementar. Não precisa aplicar as mudanças , me explique o que eu tenho que fazer.


```python

import json

import os

from pathlib import Path

  

class PathManager:

def __init__(self, origin="./", root="../"):

# Diretórios-base

self.origin = Path(origin).resolve()

self.root = Path(root).resolve()

  

# Estrutura inicial mínima

self.paths = {

"origin": {"base": self._as_posix_relative(self.origin, self.origin)},

"root": {"base": self._as_posix_relative(self.root, self.origin)}

}

  

# paths.json sempre no diretório definido em paths['origin']['base']

base_dir = (self.origin / Path(self.paths["origin"]["base"])).resolve()

self.json_path = base_dir / "paths.json"

  

# Carrega ou cria o arquivo

self.load_or_create_paths()

  

def load_or_create_paths(self):

"""Carrega paths.json se existir, ou cria um novo."""

if self.json_path.exists():

with open(self.json_path, "r") as f:

self.paths = json.load(f)

else:

# Garante que o diretório exista

self.json_path.parent.mkdir(parents=True, exist_ok=True)

self.save()

  

def save(self):

"""Grava self.paths em paths.json."""

with open(self.json_path, "w") as f:

json.dump(self.paths, f, indent=4)

  

def get_path(self, *keys):

"""

Retorna o caminho relativo concatenado,

inferindo e salvando em paths.json caso não exista.

Preenche também bases de nós intermediários se estiverem vazias.

"""

# Navega na árvore e garante nós

d = self.paths

for key in keys:

if key not in d:

d[key] = {"base": None}

d = d[key]

if "base" not in d:

d["base"] = None

  

# Atualiza todas as bases de prefixos que estão None

for i in range(1, len(keys)+1):

prefix = keys[:i]

# Acesso ao d_prefix

d_prefix = self.paths

for k in prefix:

d_prefix = d_prefix[k]

if d_prefix.get("base") is None:

d_prefix["base"] = self._infer_path(*prefix)

  

# Salva uma única vez

self.save()

  

# Retorna o caminho do nó final

final = self.paths

for key in keys:

final = final[key]

return final["base"]

  

def _infer_path(self, *keys):

"""

Inferir o caminho POSIX relativo a partir das chaves:

1. Pega base em paths[first]["base"]

2. Concatena as chaves seguintes como subdiretórios

3. Retorna caminho relativo a origin, com '/' no final

"""

first = keys[0]

# caminho base absoluto dentro de origin

base = (self.origin / self.paths[first]["base"]).resolve()

# adiciona subdirs

for key in keys[1:]:

base = base / key

# calcula caminho relativo ao origin

rel = os.path.relpath(base, self.origin)

return rel.replace("\\", "/").rstrip("/") + "/"

  

def _as_posix_relative(self, path, start):

"""

Converte um Path em string POSIX relativa a outro Path, com '/' final.

"""

rel = os.path.relpath(path, start)

return rel.replace("\\", "/").rstrip("/") + "/"

  

def print_paths(self):

import pprint

pprint.pprint(self.paths)

  

def clear_paths(self):

"""Reseta self.paths às entradas básicas e salva."""

self.paths = {

"origin": {"base": self._as_posix_relative(self.origin, self.origin)},

"root": {"base": self._as_posix_relative(self.root, self.origin)}

}

self.save()
```

---

Eu estou colocando os `inputs` e os `outputs` no primeiro bloco de cada notebook, seguindo essa forma:

```python

from PathManager import PathManager  
# Crie o gerenciador de caminhos
pm = PathManager(origin="./", root="../")

raw_geoid = ("root", "data", "raw", "geoid")
processed_geoid = ("root", "data", "processed", "geoid")
paper_figures = ("root", "paper", "figures")

inputs = {
"SAM_GEOID2023.txt": pm.get_path(raw_geoid, "SAM_GEOID2023.txt"),
"geoid_EGM2008.gdf": pm.get_path(raw_geoid, "geoid_EGM2008.gdf"),
"geoid_EGM96.gdf": pm.get_path(raw_geoid, "geoid_EGM96.gdf")
}

outputs = {
"SAM_GEOID2023.nc": pm.get_path(processed_geoid, "SAM_GEOID2023.nc"),
"EGM2008.nc": pm.get_path(processed_geoid, "EGM2008.nc"),
"EGM96.nc": pm.get_path(processed_geoid, "EGM96.nc"),
"SAM_GEOID2023.png": pm.get_path(paper_figures, "SAM_GEOID2023.png"),
"EGM2008.png": pm.get_path(paper_figures, "EGM2008.png"),
"EGM96.png": pm.get_path(paper_figures, "EGM96.png")
}

pm.print_paths()
```

Quero que o makefile tenha uma regra para cada notebook, tendo os `outputs` como alvo e `inputs`, juntamente com o `arquivo.ipynb`, como dependências. Pensei em uma classe `register_make_rule`, que recebe os dicionarios `inputs` e `outputs` e retorna a regra. Alem de `inputs` e `outputs`, a classe `register_make_rule` deve ter um parâmetro `nb_path`, para o caminho de `arquivo.ipynb`. Acho que `outputs` e `nb_path` devem ser obrigatórios, e `inputs` pode ser opcional.

Assim como `get_path` registra os caminhos automaticamente em `paths.json`, `register_make_rule` registraria a regra em um arquivo, que como `paths.json` seria criado automaticamente em `origin` na primeira vez que `register_make_rule` fosse usada.

Não tenho certeza se o arquivo para registrar as regras deve já ser um `Makefile`, talvez fosse melhor se as regras fossem sendo registradas como um grafo em um arquivo `make_rules.json`. A construção do Makefile poderia ser executada por uma classe `build_makefile`, que, a partir do arquivo `make_rules.json`, já faria um Makefile completo com `make all` e `make clean`.

Talvez os grafos parra `make all` e `make clean` pudessem também estar em `make_rules.json`, sendo atualizados automaticamente conforme novas regras são adicionadas. Quando uma nova regra for adicionada, a classe `register_make_rule` deve atualizar `make_rules.json` seguindo algumas regras. Muitos outputs voltam como inputs, é importante que o encadeamento das regras mantenha um fluxo funcional.

Em resumo, a ideia é que a base para o Makefile possa ser construída executando o primeiro bloco de cada notebooke, apenas incluído a linha de código: 

```python
pm.register_make_rule(nb_path, outputs, inputs)
```




Para facilitar as coisas, podíamos até incluir o caminho de `arquivo.ipynb` no dicionario `inputs`.

Ao invés de um




```Makefile
alvo: dependencias
	jupyter nbconvert --to notebook --execute --inplace --ExecutePreprocessor.timeout=-1 code/`arquivo.ipynb`
```


Para facilitar composição dos dicionários `inputs` e `outputs`, seria util ter uma classe: `get_path_dictionary`.
A classe `get_path` recebe os parâmetros `path`, uma tupla de strings, e `file` uma string.
A classe `get_path_dictionary` deve receber uma lista de tuplas contendo (`path`, `file`), e retornar um dicionario. A chave de cada elemento pode ser igual a `file`, ou o ultimo nó em `path` quando `file` não é fornecido. Já o valor de cada elemento sera dado por `get_path(path, file)`


("root", "data", "raw", "geoid"), "SAM_GEOID2023.txt"

---

Estou começando a achar que a classe `PathManager` está desnecessariamente complexa, principalmente porque quando comecei não sabia exatamente aonde eu queria chegar. Mas agora, com as ideias mais estruturadas, comecei a ver alguns problemas.

Uma das coisas que percebi, é que o arquivo `paths.json` não vai servir para nada. É legal, poderia ser bastante util, mas não será util para o que eu quero fazer, pelo menos não da forma que quero fazer. O arquivo `make_rules.json` que de fato vai ser importante. Mas vou deixar isso como está por enquanto, o resultado de `paths.json` fica legal visualmente LOL.

Outra coisa que me dei conta, escrever: `("root", "data", "raw", "geoid")`, é mais verborrágico do que escrever `"../data/raw/geoid/"`. Para a primeira forma precisa de 32 caracteres, para a segunda precisa só de 20. Inicialmente, quis fazer o método `get_path` porque me incomodava repetir o mesmo caminho varias vezes quando estava tabulando os inputs e outputs, mas a emenda saiu pior do que o soneto. Uma solução que pensei, vamos fazer com que `get_path` e o método `get_path_dictionary`, possam aceitar no parâmetro `path` tanto uma tupla `("root", "data", "raw", "geoid")`, quanto uma string `"../data/raw/geoid/"`. Ou seja, poderia ser usado tanto:

```python
raw_geoid = ("root", "data", "raw", "geoid")

entries = [
    (raw_geoid, "SAM_GEOID2023.txt"),
    (raw_geoid, "geoid_EGM96.gdf"),
    (raw_geoid, "geoid_EGM2008.gdf")
]

inputs = pm.get_path_dictionary(entries)
```

quanto:

```python
raw_geoid = "../data/raw/geoid/"

entries = [
    (raw_geoid, "SAM_GEOID2023.txt"),
    (raw_geoid, "geoid_EGM96.gdf"),
    (raw_geoid, "geoid_EGM2008.gdf")
]

inputs = pm.get_path_dictionary(entries)
```
Acredito que isso possa ser implementado com um `if`. Se `path` for uma tupla, o código continua agindo da mesma forma que agora. Se `path` for uma string, significa que o usuário passou um caminho. Nesse caso, é preciso decompor os nós de `path`, para que ele e seu `file` (caso haja um `file`) sejam incluídos corretamente em `paths.json`.

Por ultimo, são mais ideias de incremento do que correções. Primeiramente, vamos promover o parâmetro `nb_path` a função construtora da classe. Afinal, o objetivo principal de `PathManager` é criar Makefiles para notebooks jupyter. Diante disso, os métodos `get_path_dictionary` e `register_make_rule` são os mais importantes da classe, e tive a ideia de mais dois métodos que vão combinar a funcionalidade de ambos. Vamos implementar os métodos, `register_inputs` e `register_outputs`. Ambos devem retornar um dicionario a partir de uma lista de tuplas, exatamente da forma que `get_path_dictionary` faz. A diferença é que eles vão ao mesmo tempo atualizar o arquivo `make_rules.json`, da mesma forma que `register_make_rule`. Ao criar o gerenciador de caminhos com:

```python
pm = PathManager(nb_path="notebook.ipynb", origin="./", root="../")
```

Isso pode automaticamente incluir uma regra em `make_rules.json`, inicialmente com as chaves `"outputs"` e `"inputs"` vazias:

```json
{

"rules": {

"./notebook.ipynb": {

"notebook": "./notebook.ipynb",

"outputs": [

],

"inputs": [
]

}
}

```

Então, ao rodar o método: `register_outputs` a chave `"outputs"` é preenchida, e ao rodar `register_inputs` a chave `"inputs"` é preenchida.


Para isso, acho que devemos tornar a função `register_make_rule` mais versátil, para usa-la como função auxiliar. Ela só precisa de um parâmetro obrigatório `nb_path`. Os parâmetros `inputs` e `outputs` podem ambos serem opcionais. Quando um ou ambos não forem passados, ela simplesmente deixara a chave vazia. A função `register_make_rule` pode ser chamada pela função construtora da classe apenas com `nb_path`, pela função `register_inputs` com `nb_path` e `inputs`, e pela função `register_outputs` com `nb_path` e `outputs`.

```python
def register_make_rule(self, nb_path: str, outputs: dict, inputs: dict = None):

# 1. Caminho do arquivo make_rules.json

rules_path = self.origin / "make_rules.json"

# 2. Carrega o conteúdo existente ou inicializa

if rules_path.exists():

with open(rules_path, "r") as f:

rules = json.load(f)

else:

rules = {"rules": {}, "make_all": [], "make_clean": []}

  

# 3. Prepara a nova regra

rule = {

"notebook": nb_path,

"outputs": list(outputs.values()),

"inputs": list(inputs.values()) if inputs else []

}

# 4. Atualiza a regra no grafo

rules["rules"][nb_path] = rule

  

# 5. Atualiza make_all e make_clean

all_outputs = set(rules.get("make_all", []))

all_outputs.update(rule["outputs"])

rules["make_all"] = sorted(all_outputs)

rules["make_clean"] = sorted(all_outputs) # por enquanto são iguais

  

# 6. Salva o arquivo

with open(rules_path, "w") as f:

json.dump(rules, f, indent=4)
```





Se quiser, podemos agora seguir para implementar os métodos `register_inputs` e `register_outputs`, que usarão exatamente essa função como base. Vamos?


Os meus noteboks estão na pasta `code`, uma pasta acima da raiz do diretório. Por isso, todos caminhos relativos são registrados tendo `code` como origem. Isso será um problema caso eu queira criar o makefile na raiz do diretório. A função `build_makefile` pode ter um parâmetro `makefile_path` que pode receber os valores `origin` ou `root`. Se `makefile_path=origin`, o arquivo Makefile é salvo em `origin` como os caminhos como estão em `make_rules.json`. Se `makefile_path=root` um segundo parâmetro deve ser passado `origin_name`. Nesse caso, todo começo de caminho `"../"` devera ser substituído por `"./"`, ou nada `""`, e todo começo de caminho `"./"` deve ser subistituido por `"origin_name/"`. Por exemplo, isso no arquivo make_rules.json:

```json
{

"notebook": "./01-process_geoid.ipynb",

"outputs": [

"../data/processed/geoid/SAM_GEOID2023.nc",

"../data/processed/geoid/EGM2008.nc",

"../data/processed/geoid/EGM96.nc",

"../paper/figures/SAM_GEOID2023.png",

"../paper/figures/EGM2008.png",

"../paper/figures/EGM96.png"

],

"inputs": [

"../data/raw/geoid/SAM_GEOID2023.txt",

"../data/raw/geoid/geoid_EGM2008.gdf",

"../data/raw/geoid/geoid_EGM96.gdf"

]

}
```

Ao executar:
```python
pm.build_makefile(makefile_path=root, origin_name="code")
```

Deve virar isso:

```Makefile
01-process_geoid = \ data/processed/geoid/SAM_GEOID2023.nc \ data/processed/geoid/EGM2008.nc \ data/processed/geoid/EGM96.nc \ paper/figures/SAM_GEOID2023.png \ paper/figures/EGM2008.png \ paper/figures/EGM96.png 01-process_geoid_INPUTS = \ code/01-process_geoid.ipynb \ data/raw/geoid/SAM_GEOID2023.txt \ data/raw/geoid/geoid_EGM2008.gdf\ data/raw/geoid/geoid_EGM96.gdf $(01-process_geoid): $(01-process_geoid_INPUTS) jupyter nbconvert --to notebook --inplace --ExecutePreprocessor.timeout=-1 --execute code/01-process_geoid.ipynb
```
no makefile

caminhos começados por



build_makefile()