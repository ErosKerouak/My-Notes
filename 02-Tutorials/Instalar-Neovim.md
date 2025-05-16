
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
" Início do gerenciador de plugins
call plug#begin('~/.vim/plugged')

" Navegação e produtividade
Plug 'preservim/nerdtree'
Plug 'tpope/vim-surround'
Plug 'mhinz/vim-startify'

" Markdown
Plug 'plasticboy/vim-markdown'
Plug 'dkarter/bullets.vim'

" Python
Plug 'dense-analysis/ale'
Plug 'vim-python/python-syntax'

" Estética e barra de status
Plug 'vim-airline/vim-airline'

" Temas visuais
Plug 'dracula/vim', { 'as': 'dracula' }
Plug 'morhetz/gruvbox'
Plug 'joshdick/onedark.vim'
Plug 'navarasu/onedark.nvim'
Plug 'EdenEast/nightfox.nvim'
Plug 'folke/tokyonight.nvim', { 'branch': 'main' }
Plug 'NLKNguyen/papercolor-theme'
Plug 'shaunsingh/nord.nvim'

" LaTeX
Plug 'lervag/vimtex'

call plug#end()

" --------- CONFIGURAÇÕES GERAIS ---------

" Aparência
colorscheme gruvbox
syntax enable
set number
set relativenumber
set scrolloff=5
set wrap
set linebreak
set showmode
set mouse=a
set termguicolors

" Statusline
let g:airline_powerline_fonts = 1

" NerdTree toggle
nnoremap <C-n> :NERDTreeToggle<CR>

" Melhor indentação
set tabstop=4
set shiftwidth=4
set expandtab
set smartindent

" Histórico e experiência
set hidden
set nobackup
set nowritebackup
set noswapfile
set updatetime=300

" Vim-startify (tela inicial)
let g:startify_lists = [
      \ { 'type': 'sessions',  'header': ['   Sessões']       },
      \ { 'type': 'files',     'header': ['   Arquivos recentes'] },
      \ { 'type': 'dir',       'header': ['   Arquivos do diretório atual'] },
      \ ]

" ALE: linter em tempo real
let g:ale_linters_explicit = 1
let g:ale_python_flake8_executable = 'flake8'
let g:ale_lint_on_text_changed = 'never'
let g:ale_lint_on_save = 1
let g:ale_fix_on_save = 0

" Vimtex: apenas realce de sintaxe, sem compilador
let g:vimtex_enabled = 1
let g:vimtex_compiler_enabled = 0
let g:vimtex_view_enabled = 0

" Markdown e bullets
let g:vim_markdown_folding_disabled = 1
let g:bullets_enabled_file_types = ['markdown', 'text', 'gitcommit']

" Plugin python-syntax
let g:python_highlight_all = 1

" Atalhos úteis para escrita
inoremap jj <Esc>  " sai do modo de inserção com jj

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