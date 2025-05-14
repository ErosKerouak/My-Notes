**Linguagem:** #Bash  

### Gerenciadores de Pacotes do Sistema

- `sudo apt update` → Atualiza a lista de pacotes
- `sudo apt install nome` → Instala um pacote (Debian/Ubuntu).
- `sudo apt update && sudo apt upgrade` → Atualiza a lista e os pacotes.
- `sudo dnf install nome` → Instala um pacote (Fedora/CentOS).
- `sudo pacman -S nome` → Instala um pacote (Arch/Manjaro).

### Gerenciadores Universais

- `flatpak install flathub nome.do.app` → Instala via Flatpak (requer Flathub configurado).
- `sudo snap install nome` → Instala via Snap.

### Arquivos .deb e .rpm

- `sudo dpkg -i arquivo.deb` → Instala pacote `.deb`.
- `sudo apt install -f` → Corrige dependências após dpkg.
- `sudo rpm -i arquivo.rpm` → Instala pacote `.rpm`.
- `sudo dnf install arquivo.rpm` → Alternativa com dnf.

### Arquivos Portáteis

- `chmod +x nome.AppImage` → Torna AppImage executável.
- `./nome.AppImage` → Executa AppImage.
- `chmod +x instalador.sh` → Torna script instalador executável.
- `./instalador.sh` → Executa o script.

### Gerenciadores por Linguagem

- `pip install pacote` → Instala pacote Python.
- `npm install -g pacote` → Instala pacote Node.js globalmente.
- `cargo install pacote` → Instala pacote Rust.

### Compilação a partir do Código-fonte

- `./configure && make && sudo make install` → Compila e instala.
- ⚠️ Necessário ter dependências como `build-essential`, `gcc`, etc.

###  Relacionado a

- [[comandos-conda]]
- [[comandos-bash-essenciais]]
