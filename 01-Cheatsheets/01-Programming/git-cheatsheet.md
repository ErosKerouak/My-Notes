
**Data:** 15-05-2025  
**Linguagem/Ferramenta:** #Bash #Git
**Tags:** #cheatsheet #programming #comandos #referencia  

---

### Configuração Inicial

- `git config --global user.name "Seu Nome"` → Define seu nome para *commits*.
- `git config --global user.email "seuemail@example.com"` → Define seu e-mail para *commits*

---

### Criar ou Clonar um Repositório

- `git init` → Cria um novo repositório *Git* no diretório atual.
- `git clone URL_DO_REPOSITORIO` → Baixa um repositório remoto para sua máquina.

---

### Verificar o Status do Repositório

- `git status` → Mostra arquivos modificados, não rastreados e pendentes de *commit*.
- `git log` → Mostra o histórico de *commits*. 
- `git diff` → Mostra as diferenças entre arquivos modificados.

---

### Adicionar e Confirmar Alterações

- `git add arquivo` → Adiciona um arquivo específico para o próximo *commit*.
- `git add .` → Adiciona todos os arquivos modificados.
- `git commit` → Confirma as alterações adicionadas ao repositório.

---

### Trabalhando com Repositórios Remotos

- `ssh-keygen -t ed25519 -C "seuemail@example.com"` → Comando para gerar uma nova chave SSH.
- `git remote add origin SSH_DO_REPOSITORIO` → Define o repositório remoto.
- `git push origin main` → Envia os *commits* locais para o repositório remoto na *branch main*.
- `git push -u origin main` → Define a *branch main* como padrão para *git push*.
- `git pull origin main` → Baixa as atualizações do repositório remoto.

---

###  Relacionado a

- [[bash-cheatsheet]]
- [[conda-cheatsheet]]
