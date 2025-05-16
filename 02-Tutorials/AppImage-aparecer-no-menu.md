
---

**Data:** 16-05-2025  
**Tags:** #tutorial #instrucoes #procedimento #vim #AppImage

---

## Objetivo

Ensinar como criar um arquivo `.desktop` para que um aplicativo distribuído como **AppImage** (por exemplo, Neovide) apareça no **menu do sistema operacional**, com nome, ícone e descrição personalizados.

---

## Pré-requisitos

- Um AppImage funcional, com permissão de execução (`chmod +x`)
    
- Um ícone `.png` (ou `.svg`) para o aplicativo
    
- Permissões de escrita no diretório `~/.local/share/applications/`
    

---

## Etapas

### 1. Organizar o AppImage e o ícone

Crie uma pasta para armazenar o AppImage e o ícone:

```bash
mkdir -p ~/.local/bin
mkdir -p ~/.local/share/icons
mv ~/Downloads/neovide.AppImage ~/.local/bin/neovide
wget https://github.com/neovide/neovide/raw/main/assets/neovide.png -O ~/.local/share/icons/neovide.png
chmod +x ~/.local/bin/neovide
```

---

### 2. Criar o arquivo `.desktop`

Crie e edite o atalho do aplicativo:

```bash
nano ~/.local/share/applications/neovide.desktop
```

Cole o conteúdo abaixo:

```ini
[Desktop Entry]
Name=Neovide
Comment=GUI for Neovim
Exec=/home/lpga/.local/bin/neovide.AppImage %U
Icon=/home/lpga/.local/share/icons/neovide.png
Terminal=false
Type=Application
Categories=Utility;TextEditor;

```

> ⚠️ Ajuste os caminhos se o nome de usuário não for `eros` no seu sistema.

Salve com `Ctrl + O`, depois `Enter`, e saia com `Ctrl + X`.

---

### 3. Verificar no menu de aplicativos

Recarregue o cache de atalhos (opcional, na maioria dos casos):

```bash
update-desktop-database ~/.local/share/applications/
```

Depois, abra o menu do sistema e digite:

```
Neovide
```

O ícone e o nome do programa devem aparecer. Clique para abrir.

---

## Observações

- Se o atalho não aparecer: reinicie a sessão ou o computador, ou verifique se há erros de digitação no `.desktop`.
    
- A entrada `Exec=` deve apontar para o AppImage com permissão de execução.
    
- Você pode usar ícones em `.svg` também.
    
- O AppImage não precisa estar no `/usr/bin`; pode estar na home sem problemas.
    

---

## Referências

- [Freedesktop Desktop Entry Specification](https://specifications.freedesktop.org/desktop-entry-spec/latest/)
    
- [[Instalar-Neovim]] 
    

---

