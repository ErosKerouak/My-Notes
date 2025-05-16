
---
**Data:** 16-05-2025  

**Linguagem:** #Bash  

**Tags:** #cheatsheet #apt #linux #pacotes

---

### Instalação e remoção de pacotes

- `sudo apt install nome-do-pacote` → Instala um pacote.  
- `sudo apt remove nome-do-pacote` → Remove o pacote, mas mantém arquivos de configuração.  
- `sudo apt purge nome-do-pacote` → Remove o pacote **e** os arquivos de configuração.  
- `sudo apt reinstall nome-do-pacote` → Reinstala o pacote.

---

### Atualização do sistema

- `sudo apt update` → Atualiza a lista de pacotes disponíveis (índices dos repositórios).  
- `sudo apt upgrade` → Atualiza todos os pacotes instalados para versões mais recentes.  
- `sudo apt full-upgrade` → Atualiza pacotes e pode remover/instalar outros para resolver dependências.  
- `sudo apt dist-upgrade` → Sinônimo de `full-upgrade` (nome legado).

---

### Pesquisa e informações

- `apt search nome` → Busca pacotes disponíveis com nome ou descrição relacionados.  
- `apt show nome-do-pacote` → Exibe detalhes do pacote (versão, dependências, descrição, etc).  
- `apt list --installed` → Lista todos os pacotes instalados.  
- `apt list nome-do-pacote` → Lista o status de um pacote específico.

---

### Limpeza e manutenção

- `sudo apt autoremove` → Remove pacotes órfãos (instalados automaticamente e não mais necessários).  
- `sudo apt clean` → Remove os arquivos `.deb` baixados em `/var/cache/apt/archives/`.  
- `sudo apt autoclean` → Remove apenas os pacotes `.deb` antigos e obsoletos.

---

### Fontes de pacotes

- `/etc/apt/sources.list` → Arquivo principal com os repositórios do sistema.  
- `/etc/apt/sources.list.d/` → Diretório com arquivos adicionais de repositórios.

---

### Dicas úteis

- Combine `update` com `upgrade`:  
  `sudo apt update && sudo apt upgrade`  
- Sempre leia a saída de `apt` com atenção antes de confirmar uma operação.  
- Use `-y` para confirmar automaticamente (`sudo apt install nome -y`), mas com cautela.  
- Use `sudo dpkg -l` para listar pacotes via `dpkg`.

---

