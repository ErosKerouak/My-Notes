
---

**Linguagem:** #Bash  
**Tags:** #cheatsheet #comandos

---

### Manipulação de Arquivos e Diretórios

- `pwd` → Mostra o diretório atual (caminho absoluto).
- `ls` → Lista arquivos e pastas do diretório atual.
- `ls -l` → Lista arquivos com detalhes (permissões, tamanho, data).
- `ls -a` → Lista arquivos, incluindo ocultos (. e ..).
- `cd pasta/` → Acessa um diretório.
- `cd ..` → Volta um diretório.
- `mkdir nome_pasta` → Cria uma pasta.
- `rmdir nome_pasta` → Remove uma pasta vazia.
- `rm arquivo.txt` → Remove um arquivo.
- `rm -r pasta/` → Remove uma pasta e todo o seu conteúdo.
- `cp arquivo.txt destino/` → Copia um arquivo.
- `mv arquivo.txt destino/` → Move ou renomeia um arquivo.
---

### Visualização de Arquivos

- `cat arquivo.txt` → Mostra o conteúdo do arquivo.
- `less arquivo.txt` → Permite rolar pelo arquivo (q para sair).
- `head -n 10 arquivo.txt` → Mostra as 10 primeiras linhas.
- `tail -n 10 arquivo.txt` → Mostra as 10 últimas linhas.
- `tail -f arquivo.log` → Acompanha um arquivo em tempo real.
-
---

### Redirecionamento e Pipes

- `comando > arquivo.txt` → Redireciona a saída do comando para um arquivo (sobrescreve).
- `comando >> arquivo.txt` → Adiciona a saída ao final do arquivo.
- `comando < arquivo.txt` → Usa o arquivo como entrada para um comando.
- `comando1 | comando2` → Usa a saída de um comando como entrada para outro.

---

### Descompactação de Arquivos

- `unzip arquivo.zip` → Descompacta arquivos `.zip`.
- `tar -xvf arquivo.tar` → Extrai arquivos de um `.tar`.
- `tar -xvzf arquivo.tar.gz` ou `.tgz` → Extrai arquivos `.tar.gz`.
- `tar -xvjf arquivo.tar.bz2` → Extrai arquivos `.tar.bz2`.
- `gunzip arquivo.gz` → Descompacta um arquivo `.gz` (um único arquivo).
- `bunzip2 arquivo.bz2` → Descompacta um arquivo `.bz2` (um único arquivo).
- `unrar x arquivo.rar` → Extrai arquivos `.rar` (requer unrar instalado).
- `7z x arquivo.7z` → Extrai arquivos `.7z` (requer p7zip-full instalado).
- `file nome_do_arquivo` → Identifica o tipo real de um arquivo compactado.

---

### Gerenciadores de Pacotes do Sistema

- `sudo apt update` → Atualiza a lista de pacotes
- `sudo apt install nome` → Instala um pacote (Debian/Ubuntu).
- `sudo apt update && sudo apt upgrade` → Atualiza a lista e os pacotes.
- `sudo dnf install nome` → Instala um pacote (Fedora/CentOS).
- `sudo pacman -S nome` → Instala um pacote (Arch/Manjaro).

---

### Gerenciadores Universais

- `flatpak install flathub nome.do.app` → Instala via Flatpak (requer Flathub configurado).
- `sudo snap install nome` → Instala via Snap.

---

### Arquivos .deb e .rpm

- `sudo dpkg -i arquivo.deb` → Instala pacote `.deb`.
- `sudo apt install -f` → Corrige dependências após dpkg.
- `sudo rpm -i arquivo.rpm` → Instala pacote `.rpm`.
- `sudo dnf install arquivo.rpm` → Alternativa com dnf.

---

### Arquivos Portáteis

- `chmod +x nome.AppImage` → Torna AppImage executável.
- `./nome.AppImage` → Executa AppImage.
- `chmod +x instalador.sh` → Torna script instalador executável.
- `./instalador.sh` → Executa o script.

---

### Gerenciadores por Linguagem

- `pip install pacote` → Instala pacote Python.
- `npm install -g pacote` → Instala pacote Node.js globalmente.
- `cargo install pacote` → Instala pacote Rust.

---

### Compilação a partir do Código-fonte

- `./configure && make && sudo make install` → Compila e instala.
- ⚠️ Necessário ter dependências como `build-essential`, `gcc`, etc.

---

### Relacionado a

- [[instalação-de-programas]]
- [[comandos-git]]
- [[comandos-conda]]
