
---

**Data:** 16-05-2025  
**Linguagem:** #Bash  
**Tags:** #cheatsheet #dpkg #linux #deb #pacotes

---

### Instalação e remoção de pacotes `.deb`

- `sudo dpkg -i pacote.deb` → Instala um pacote `.deb` local.  
- `sudo dpkg -r nome-do-pacote` → Remove o pacote, mantendo os arquivos de configuração.  
- `sudo dpkg -P nome-do-pacote` → Remove o pacote **e** os arquivos de configuração.  

---

### Verificação e reparo

- `sudo dpkg --configure -a` → Conclui instalações interrompidas ou incompletas.  
- `sudo apt install -f` → Corrige dependências quebradas causadas por `dpkg`.  

---

### Consulta de pacotes

- `dpkg -l` → Lista todos os pacotes instalados.  
- `dpkg -l | grep nome` → Filtra por nome ou parte do nome do pacote.  
- `dpkg -s nome-do-pacote` → Mostra o status (versão, descrição, dependências).  
- `dpkg -L nome-do-pacote` → Lista todos os arquivos instalados por um pacote.  
- `dpkg -S caminho/arquivo` → Informa a qual pacote pertence um arquivo.  

---

### Extração de conteúdo sem instalar

- `dpkg-deb -c pacote.deb` → Lista o conteúdo de um pacote `.deb`.  
- `dpkg-deb -x pacote.deb destino/` → Extrai os arquivos do pacote para a pasta `destino`.

---

### Dicas úteis

- Sempre verifique se o pacote `.deb` possui dependências — o `dpkg` **não resolve dependências automaticamente**.  
- Após usar `dpkg -i`, rode `sudo apt install -f` para resolver dependências, se necessário.  
- Combine `dpkg -S` com caminhos de erro para rastrear problemas de arquivos ausentes.

---
