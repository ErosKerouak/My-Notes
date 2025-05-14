
---

#  Pasta 05-Códigos

Esta pasta reúne trechos de **código comentado**, algoritmos, funções próprias, testes computacionais e anotações relacionadas à programação.  
Aqui ficam os registros que explicam, organizam e documentam os scripts usados ao longo de projetos acadêmicos, pessoais e técnicos.

---

##  Tipos de notas esperadas

- **Funções e rotinas úteis** com explicações
- **Exemplos comentados** de uso de bibliotecas (ex: `numpy`, `xarray`, `verde`, `matplotlib`)
- **Testes de código**, benchmarking, validações
- **Snippets reutilizáveis** (ex: leitura de NetCDF, visualização de DataArray, interpolação de pontos, etc.)
- **Mini tutoriais** ou referências pessoais sobre ferramentas específicas (ex: `git`, `bash`, `qgis-expressions.md`)

---

##  Organização sugerida

Você pode:

- Criar uma nota por função/tópico (ex: `interpolacao-equivalente.md`, `filtragem-xarray.md`)
- Usar prefixos para agrupar temas:
  - `py-` → código em Python
  - `bash-` → shell scripts
  - `sql-` → expressões SQL/QGIS
  - `git-` → comandos e rotinas de versionamento

---

##  Boas práticas

- Adicione um cabeçalho explicando a função ou contexto do código
- Inclua comentários dentro dos blocos de código
- Use o destaque de sintaxe Markdown (ex: ` ```python `)
- Prefira nomes de arquivos claros e legíveis

---

###  Exemplo de estrutura de nota

```markdown
# Interpolação com fontes equivalentes (Verde)

Este código faz interpolação a partir de pontos dispersos com o método das Fontes Equivalentes usando a biblioteca `verde`.

```python
import verde as vd

# Fit the model
spline = vd.EquivalentSources(depth=10000).fit(coordinates, data)

# Predict on a grid
grid = spline.grid(region, shape=(100, 100))
````

##  Observações

- Testado com dados gravimétricos reais
    
- Útil para reconstruir superfícies potenciais com ruído
    

##  Relacionado a

[[04-Pesquisa/interpolacao-ams.md]]



---

##  Integração com o Vault

A pasta `05-Códigos` serve como base técnica e computacional para:

- `01-Projetos` → execução de scripts e notebooks
- `04-Pesquisa` → testes, métodos, análises e processamento
- `10-Ensino` → exemplos e explicações em contexto didático


---
