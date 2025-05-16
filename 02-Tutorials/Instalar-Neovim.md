
---

**Data:** 16-05-2025  
**Tags:** #tutorial #instrucoes #procedimento #vim

---

## Objetivo

Instalar o editor **Neovim** no Linux (Pop!_OS, Ubuntu ou similares) usando Snap, configurar o gerenciador de plugins `vim-plug` e ativar plugins úteis com suporte a Markdown, LaTeX e Python.

---

## Pré-requisitos

- Acesso a um terminal com permissões de superusuário (`sudo`)
    
- Conexão com a internet
    
- Ter o Snap habilitado no sistema
    

---

## Etapas

### 1. Instalar o Neovim via Snap

Abra o terminal e instale o Neovim com a versão mais recente (≥ 0.10):

```bash
sudo snap install --edge nvim --classic
```

Verifique a versão instalada:

```bash
nvim --version
```

---

### 2. Criar o arquivo de configuração (`init.vim`) e instalar o vim-plug

Crie a pasta de configuração do Neovim:

```bash
mkdir -p ~/.config/nvim
```

Instale o gerenciador de plugins `vim-plug`:

```bash
curl -fLo ~/.local/share/nvim/site/autoload/plug.vim --create-dirs \
     https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

Crie o arquivo `~/.config/nvim/init.vim` com a configuração inicial dos plugins:

```bash
nvim ~/.config/nvim/init.vim
```

Cole o conteúdo abaixo:

```vim
call plug#begin('~/.vim/plugged')

Plug 'preservim/nerdtree'
Plug 'tpope/vim-surround'
Plug 'mhinz/vim-startify'
Plug 'plasticboy/vim-markdown'
Plug 'dkarter/bullets.vim'
Plug 'dense-analysis/ale'
Plug 'vim-python/python-syntax'
Plug 'morhetz/gruvbox'
Plug 'vim-airline/vim-airline'
Plug 'lervag/vimtex'

call plug#end()

" Configurações gerais
syntax enable
colorscheme gruvbox
set number relativenumber scrolloff=5 wrap linebreak mouse=a
set tabstop=4 shiftwidth=4 expandtab smartindent
let g:airline_powerline_fonts = 1
nnoremap <C-n> :NERDTreeToggle<CR>
let g:vimtex_compiler_enabled = 0
let g:vimtex_view_enabled = 0
```

Salve com `:wq`.

---

### 3. Instalar os plugins e tornar o Neovim o editor padrão

Abra o Neovim e instale os plugins:

```vim
:PlugInstall
```

Depois, defina o Neovim como editor padrão do sistema:

```bash
sudo update-alternatives --install /usr/bin/editor editor /snap/bin/nvim 110
sudo update-alternatives --config editor
```

Selecione o `/snap/bin/nvim` como padrão.

Para uso em scripts e Git, adicione ao final do `~/.bashrc`:

```bash
export EDITOR=nvim
export VISUAL=nvim
```

Depois recarregue:

```bash
source ~/.bashrc
```

---

## Observações

- Ao abrir `git commit` ou `crontab -e`, o Neovim será usado como editor.
    
- O plugin `vimtex` funciona apenas com Neovim ≥ 0.10 ou Vim ≥ 9.1.
    
- Para compilar LaTeX com `tectonic`, basta usar `:!tectonic arquivo.tex`.
    
- Você pode explorar comandos como `:vsp`, `:sp`, `:NERDTreeToggle`, e `:Startify`.
    

---

## Referências

- [Neovim - Site oficial](https://neovim.io/)
    
- [vim-plug - GitHub](https://github.com/junegunn/vim-plug)
    
- [vimtex - GitHub](https://github.com/lervag/vimtex)
    

---