
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
Complete com a explicação 
- `ssh-keygen -t ed25519 -C "seuemail@example.com"` → Comando para gerar uma nova chave SSH.
- `git remote add origin SSH_DO_REPOSITORIO` → Define o repositório remoto.
- `git push origin main` → Envia os *commits* locais para o repositório remoto na *branch main*.
- `git push -u origin main` → Define a *branch main* como padrão para *git push*.
- `git pull origin main` → Baixa as atualizações do repositório remoto.
- `git pull --rebase origin main` → Baixa os commits remotos e reaplica os commits locais por cima deles, mantendo um histórico linear e evitando  merge.
- `git pull --no-rebase origin main` → Isso fará um merge automático entre as mudanças locais e remotas, **se não houver conflitos**.

---

### Lidando com Conflitos no `git pull`
O erro ocorre quando você tem modificações locais em arquivos que também foram alterados no repositório remoto. O Git evita sobrescrever essas mudanças automaticamente. Há três estratégias principais:

- `git add . && git commit -m "mensagem"` → **Commita as mudanças locais**, então use `git pull` normalmente para mesclar com o remoto.
- `git stash && git pull && git stash pop` → **Salva temporariamente** suas alterações com `stash`, faz o `pull`, e depois reaplica as mudanças.
- `git reset --hard HEAD && git pull` → **Descarta completamente** as alterações locais (sem chance de recuperação) e atualiza com o remoto.

**Atenção:** Sempre revise com `git status` antes de decidir. Use `git diff` para inspecionar suas mudanças antes de apagá-las.

---

### Usando `git stash`
O comando `git stash` é útil para guardar temporariamente alterações locais não comitadas, permitindo que você troque de branch ou atualize o repositório sem perder seu progresso atual.

- `git stash` → Salva as alterações locais (inclusive modificações em arquivos rastreados) e limpa o diretório de trabalho.
- `git stash list` → Lista os stashes salvos.
- `git stash pop` → Recupera e remove o stash mais recente, reaplicando as alterações.
- `git stash apply` → Recupera o stash mais recente **sem removê-lo** da lista.
- `git stash drop` → Remove o stash mais recente da lista.
- `git stash clear` → Remove **todos** os stashes.

Use `git stash` com cuidado: ele **não salva arquivos não rastreados** por padrão. Para salvar tudo:

- `git stash -u` → Inclui arquivos não rastreados (`untracked files`).
- `git stash -a` → Inclui arquivos ignorados (`.gitignore`), além dos não rastreados.

---

###  Relacionado a

- [[bash-cheatsheet]]
- [[conda-cheatsheet]]
