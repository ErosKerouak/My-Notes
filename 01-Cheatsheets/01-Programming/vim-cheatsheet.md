
---

**Data:** 15-05-2025  
**Linguagem/Ferramenta:** #Vim 
**Tags:** #cheatsheet #programming #comandos #referencia  

---

### Modos do Vim

- `i` → Entra no modo de inserção (inserir texto antes do cursor).  
- `a` → Insere texto **após** o cursor.  
- `I` → Insere no início da linha.  
- `A` → Insere no final da linha.  
- `Esc` → Sai do modo de inserção e retorna ao modo normal.  
- `:` → Entra no modo de comandos.

---

### Navegação

- `h` → Move o cursor para a esquerda.  
- `l` → Move o cursor para a direita.  
- `j` → Move o cursor para baixo.  
- `k` → Move o cursor para cima.  
- `w` → Pula para o início da próxima palavra.  
- `b` → Volta para o início da palavra anterior.  
- `0` → Vai para o início da linha.  
- `^` → Vai para o primeiro caractere não em branco.  
- `$` → Vai para o fim da linha.  
- `gg` → Vai para o início do arquivo.  
- `G` → Vai para o fim do arquivo.  
- `:n` → Vai para a linha `n`.

---

### Inserção e Edição

- `x` → Apaga o caractere sob o cursor.  
- `dd` → Apaga a linha atual.  
- `yy` → Copia (yank) a linha atual.  
- `p` → Cola após o cursor.  
- `P` → Cola antes do cursor.  
- `u` → Desfaz a última ação.  
- `Ctrl + r` → Refaz (redo).  
- `r<char>` → Substitui o caractere atual por `<char>`.  
- `cw` → Substitui (change word).  
- `ciw` → Substitui palavra inteira.

---

### Busca e Substituição

- `/palavra` → Busca por "palavra" para frente.  
- `?palavra` → Busca por "palavra" para trás.  
- `n` → Próxima ocorrência.  
- `N` → Ocorrência anterior.  
- `:%s/velho/novo/g` → Substitui "velho" por "novo" no arquivo todo.  
- `:s/velho/novo/g` → Substitui "velho" por "novo" na linha atual.

---

### Salvar e Sair

- `:w` → Salva (write).  
- `:q` → Sai (quit).  
- `:wq` ou `ZZ` → Salva e sai.  
- `:q!` → Sai sem salvar.  
- `:x` → Salva se houver modificações e sai.

---

### Visual Mode

- `v` → Inicia seleção por caractere.  
- `V` → Inicia seleção por linha.  
- `Ctrl + v` → Inicia seleção em bloco (coluna).  
- `y` → Copia o texto selecionado.  
- `d` → Corta (deleta) o texto selecionado.  
- `>` / `<` → Indenta ou desindenta bloco.

---

### Dividir a tela com splits


---

### Dicas úteis

- `.` → Repete o último comando de edição.  
- `:set number` → Exibe números de linha.  
- `:set relativenumber` → Números relativos (boa prática para navegação).  
- `:noh` → Limpa destaque de busca.  
- `:help comando` → Acessa a ajuda do Vim.

---

