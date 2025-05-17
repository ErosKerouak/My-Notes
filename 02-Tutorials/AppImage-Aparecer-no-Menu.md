
---

**Data:** 16-05-2025  
**Tags:** #tutorial #instrucoes #procedimento #vim #neovim #obsidian #AppImage

---

## Objetivo

Ensinar como criar um arquivo `.desktop` para que um aplicativo distribuído como **AppImage** (por exemplo, Neovide, Obsidian, etc.) apareça no **menu do sistema operacional**, com nome, ícone e descrição personalizados.

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
mkdir -p ~/.local/bin/obsidian
mkdir -p ~/.local/share/icons
```


Mova o ícone e o AppImage para as pastas correspondentes:

```bash
mv ~/Downloads/obsidian.AppImage ~/.local/bin/obsidian/obsidian.AppImage
mv ~/Downloads/obsidian.png ~/.local/share/icons/obsidian.png
```

Torne o AppImage executável, caso ainda não tenha feito isso:

```bash
chmod +x ~/.local/bin/obsidian/obsidian.AppImage
```

---

### 2. Criar o arquivo `.desktop`

Crie e edite o atalho do aplicativo:

```bash
touch ~/.local/share/applications/obsidian.desktop
vim ~/.local/share/applications/obsidian.desktop
```

Cole o conteúdo abaixo e edite conforme necessário:

```ini
[Desktop Entry]
Name=Nome visível do app
Comment=Descrição curta (tooltip)
Exec=caminho_para_o_AppImage
Icon=caminho_para_o_ícone_ou_nome_do_ícone
Terminal=true|false
Type=Application
Categories=Categoria1;Categoria2;
MimeType=tipo/mime1;tipo/mime2;
```

Explicação de cada campo:

| Campo        | O que faz                                                                     |
| ------------ | ----------------------------------------------------------------------------- |
| `Name`       | Nome que aparece no menu                                                      |
| `Comment`    | Texto curto de descrição (aparece como dica/tooltips)                         |
| `Exec`       | Caminho ou comando para iniciar o app (pode incluir `%U`, `%F`, etc.)         |
| `Icon`       | Caminho para o ícone (ou nome de um ícone instalado no sistema)               |
| `Terminal`   | `true` se o app precisa de terminal, `false` se é gráfico                     |
| `Type`       | Quase sempre `Application`                                                    |
| `Categories` | Define em que categoria do menu o app aparece (ajuda o sistema a classificar) |
| `MimeType`   | (Opcional) Define os tipos de arquivos que o app pode abrir                   |

	Os campos: `Name`, `Exec` e `Type` são obriagatorios para o .desktop funcionar, os demais campos são opcionais.   

Exemplo: AppImage do Obsidian

```ini
[Desktop Entry]
Name=Obsidian
Comment=Markdown-based note-taking app
Exec=/home/eros/.local/bin/obsidian.AppImage
Icon=/home/eros/Imagens/icones/obsidian.png
Terminal=false
Type=Application
Categories=Utility;TextEditor;
```

Salve com `Ctrl + O`, depois `Enter`, e saia com `Ctrl + X`.

---

### 3. Verificar no menu de aplicativos

Recarregue o cache de atalhos (opcional, na maioria dos casos):

```bash
update-desktop-database ~/.local/share/applications/
```

Depois, abra o menu do sistema e digite:

```
Obsidian
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

