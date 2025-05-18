
---

**Data:** 15-05-2025  
**Linguagem/Ferramenta:** #Vim 
**Tags:** #cheatsheet #programming #comandos #referencia  

---

## **1. Modo Normal** 

---

#### **Navegação (essenciais):**

**Caractere por caractere:**
- `h` → Move o cursor para a esquerda  
- `l` → Move o cursor para a direita  
- `j` → Move o cursor para baixo  
- `k` → Move o cursor para cima

**Em relação as linhas:**

- `0` → Vai para o início da linha  
- `^` → Vai para o primeiro caractere não vazio da linha  
- `$` → Vai para o final da linha  

**Em relação as palavras:**

- `w` → Vai para o início da próxima palavra  
- `b` → Vai para o início da palavra anterior  
- `e` → Vai para o final da palavra  

**Em relação ao arquivo:**

- `gg` → Vai para o início do arquivo  
- `G` → Vai para o final do arquivo  
- `nG` → Vai para a linha _n_
>
- `Ctrl-d` → Rola meia tela para baixo  
- `Ctrl-u` → Rola meia tela para cima  

---

#### Gerenciamento de splits:

**Navegar entre splits:**

- `Ctrl + w h` → Move para o **split da esquerda**
- `Ctrl + w l` → Move para o **split da direita**
- `Ctrl + w j` → Move para o **split de baixo**
- `Ctrl + w k` → Move para o **split de cima**
- `Ctrl + w w` → Alterna para o **próximo split**
- `Ctrl + w t` → Vai para o **primeiro split**
- `Ctrl + w b` → Vai para o **último split**
    
**Redimensionar splits:**

- `Ctrl + w +` → Aumenta a altura do split
- `Ctrl + w -` → Diminui a altura do split
- `Ctrl + w >` → Aumenta a largura
- `Ctrl + w <` → Diminui a largura
- `Ctrl + w =` → Equaliza todos os tamanhos

**Fechar splits:**

- `:q` → Fecha o split atual
- `Ctrl + w c` → Fecha o split atual
- `Ctrl + w o` → Fecha **todos os outros splits** (só mantém o atual)

> 🧠 Dica para memorizar, tudo começa com `Ctrl + w` → isso ativa os comandos de "window", depois você usa uma letra: `h`, `j`, `k`, `l`, `+`, `-`, `=`, etc.

---


####  **Criar e gerenciar abas:**

- `:tabnew` → Abre uma nova aba vazia
    
- `:tabnew arquivo.txt` → Abre `arquivo.txt` em nova aba
    
- `:tabedit arquivo.txt` → Abre `arquivo.txt` em nova aba (atalho de `:tabnew`)
    
- `:tabclose` → Fecha a aba atual
    
- `:tabonly` → Fecha todas as abas exceto a atual
    


 **Navegar entre abas:**

- `gt` → Vai para a **próxima aba**
    
- `gT` → Vai para a **aba anterior**
    
- `n gt` → Vai para a aba de número `n` (ex: `2gt` → vai para a segunda aba)
    
- `:tabs` → Lista todas as abas abertas
    



 **Visualização de múltiplos arquivos**

Como cada aba pode ter **vários splits dentro dela**, você pode:

1. Abrir um arquivo com `:tabnew arquivo1.txt`
    
2. Dentro da aba, dividir a tela com `:vsplit arquivo2.txt`
    
3. Criar uma nova aba com `:tabnew arquivo3.txt`
    

Assim, você terá:

- **Aba 1:** arquivo1.txt + arquivo2.txt em split
    
- **Aba 2:** arquivo3.txt sozinho

---

#### **Edição (essenciais):**

**Atalhos básicos de edição:**

- `u` → Desfaz a última ação
- `Ctrl-r` → Refaz a última ação
- `.` → Repete o último comando de edição
>
- `r{char}` → Substitui o caractere sob o cursor por `{char}`
- `~` → Alterna entre maiúscula/minúscula no caractere
- `J` → Junta a linha atual com a próxima

**Excluir e/ou recortar:**

- `x` → Apaga o caractere sob o cursor
- `dd` → Recorta (deleta) a linha atual
- `dw` → Recorta até o final da palavra
- `d$` → Recorta do cursor até o final da linha

**Copiar:**

- `yy` → Copia a linha atual
- `yw` → Copia a palavra
- `y$` → Copia do cursor até o final da linha

**Colar:**

- `p` → Cola **após** o cursor
- `P` → Cola **antes** do cursor

---

#### **Prefixos numéricos (multiplicadores)**

- `n{comando}` → Executa o comando `{comando}` **n vezes seguidas**
    

**Exemplos práticos:**

- `5h` → Move 5 posições para a esquerda
- `3j` → Move 3 linhas para baixo
- `10l` → Move 10 posições para a direita
- `7k` → Move 7 linhas para cima
- `3w` → Pula 3 palavras à frente
- `2dd` → Apaga 2 linhas
- `4p` → Cola 4 vezes
- `5u` → Desfaz 5 ações
- `6.` → Repete o último comando 6 vezes
	

> 💡 Essa lógica funciona com **quase todos os comandos de movimento e edição** no modo normal. É uma das bases da fluidez no uso do Vim.

---

## **2. Modo de Comando**

---

#### **Gerenciamento de arquivos**

- `:w` → Salva o arquivo atual
- `:q` → Sai do Vim
- `:wq` → Salva e sai
- `:x` → Salva e sai (igual a `:wq`)
- `:q!` → Sai **sem salvar** as alterações
- `:w nome.txt` → Salva com um nome diferente
- `:e nome.txt` → Abre outro arquivo
- `:r nome.txt` → Insere o conteúdo de outro arquivo no cursor

---

#### **Busca de texto**

- `/palavra` → Busca "palavra" para frente
- `?palavra` → Busca "palavra" para trás
- `n` → Vai para a próxima ocorrência
- `N` → Vai para a ocorrência anterior
- `:noh` → Remove o destaque da busca atual

---

#### **Substituição de texto (básico)**

- `:s/velho/novo` → Substitui **a primeira ocorrência** na linha atual
- `:s/velho/novo/g` → Substitui **todas** as ocorrências na linha atual
- `:%s/velho/novo/g` → Substitui todas as ocorrências no arquivo
- `:%s/velho/novo/gc` → Substitui todas com **confirmação interativa**

---

#### **Ajuda e documentação**

* `:help` → Abre a ajuda geral do Vim
* `:help comando` → Abre a ajuda para um comando específico (ex: `:help y`)

---

#### **Execução de comandos externos**

- `:!ls` → Executa o comando `ls` no terminal
- `:!python3 script.py` → Roda um script diretamente do Vim
- `:!clear` → Limpa a tela do terminal

---

#### **Abrir splits**

- `:split` → Divide a tela **horizontalmente** (acima/abaixo) com o mesmo arquivo
    
- `:vsplit` → Divide a tela **verticalmente** (lado a lado) com o mesmo arquivo
    
- `:split arquivo.txt` → Abre `arquivo.txt` em split horizontal
    
- `:vsplit arquivo.txt` → Abre `arquivo.txt` em split vertical
    

> 💡 Abre no **modo de comando**, então sempre requer `Enter`

---

## **3. Modo Visual **

O modo visual é ativado a partir do **modo normal** com os seguintes comandos:

---

#### **Ativar o modo visual**

- `v` → Entra no **modo visual caractere a caractere**
    
- `V` → Entra no **modo visual por linha inteira**
    
- `Ctrl + v` → Entra no **modo visual em bloco (coluna)**
    

---

#### **Ações possíveis no modo visual**

Depois de selecionar o texto com `hjkl` (ou qualquer comando de navegação), você pode:

- `y` → Copiar a seleção
    
- `d` → Cortar (apagar) a seleção
    
- `x` → Cortar caractere(s) selecionado(s)
    
- `p` → Colar substituindo a seleção
    
- `~` → Inverter maiúscula/minúscula dos caracteres selecionados
    
- `>` → Indentar a seleção à direita
    
- `<` → Indentar a seleção à esquerda
    
- `=` → Reindentar a seleção automaticamente
    
- `:` → Executar um comando `:` sobre a seleção (ex: `:sort`)
    

>  No modo visual, o `:` abre o modo de comando e aplica o comando somente à seleção.

---

#### **Encerrar o modo visual**

- `Esc` → Sai do modo visual sem aplicar alterações
    

---

### **Exemplos práticos**

- `vjjy` → Seleciona 3 linhas e copia
    
- `V2j>` → Seleciona 3 linhas e indenta
    
- `Ctrl+v3jI#` → Com `Ctrl+v`, seleciona 3 linhas e insere `#` no início de cada uma (modo visual em bloco + `I`)
    

---

## **4 Modo de Inserção**

> O **modo de inserção** não tem comandos no sentido tradicional — você apenas **digita texto livremente**, como em um editor comum.  
> Porém, existem **vários comandos no modo normal** que colocam você **dentro do modo de inserção**, e cada um tem um propósito diferente.
---

#### **Comandos que entram no modo de inserção**

> Todos esses comandos são executados no **modo normal** e fazem o Vim entrar no **modo de inserção** a partir de diferentes posições ou com efeitos distintos.

- `i` → Entra no modo de inserção na **posição atual do cursor**
    
- `I` → Entra no modo de inserção **no início da linha (antes do primeiro caractere não vazio)**
    
- `a` → Entra no modo de inserção **após o caractere atual**
    
- `A` → Entra no modo de inserção **no fim da linha**
    
- `o` → Abre uma **nova linha abaixo** e entra no modo de inserção
    
- `O` → Abre uma **nova linha acima** e entra no modo de inserção
    
- `s` → Substitui o **caractere atual** e entra no modo de inserção
    
- `S` → Substitui a **linha inteira** e entra no modo de inserção (igual a `cc`)
    
- `cc` → Apaga a linha e entra no modo de inserção
    
- `C` → Apaga do cursor até o fim da linha e entra no modo de inserção
    
- `R` → Entra no **modo de substituição contínua** (overwrite mode)
    
- `gi` → Vai para o **último ponto onde você usou o modo de inserção** e retorna a ele
    

---

####  Observações

- `i`, `a`, `o` → São os mais básicos e usados no dia a dia
    
- `R` → É o único que ativa o **modo de substituição**, diferente do modo de inserção normal
    
- `gi` → Útil para voltar rapidamente à última edição
    
- `s`, `S`, `cc`, `C` → Combinam substituição + inserção, muito eficientes com prática
    

---
