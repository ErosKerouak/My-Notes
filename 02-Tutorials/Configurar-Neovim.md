
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

### 1. Instalar o Neovim 

Instale o Vim, caso ainda não esteja disponível no sistema:

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
" ============================================
" ==========   Plugins (Vim-Plug)   ==========
" ============================================
" Instale o gerenciador primeiro:
" https://github.com/junegunn/vim-plug
call plug#begin('~/.vim/plugged')

  " Navegação e produtividade
  Plug 'preservim/nerdtree'            " File explorer em árvore
  Plug 'tpope/vim-surround'            " Manipula pares ("" '' () {} <>)
  Plug 'mhinz/vim-startify'            " Tela inicial com sessões e arquivos recentes
  Plug 'ThePrimeagen/vim-be-good'      " Jogo para praticar movimentos no modo Normal
  Plug 'junegunn/fzf', { 'do': { -> fzf#install() } }  " Fuzzy finder para arquivos e comandos

  " Markdown
  Plug 'plasticboy/vim-markdown'       " Realce de sintaxe e suporte a Markdown
  Plug 'dkarter/bullets.vim'           " Criar/continuar listas com marcadores automaticamente

  " Python
  Plug 'dense-analysis/ale'            " Linter assíncrono (suporta múltiplas linguagens)
  Plug 'vim-python/python-syntax'      " Destaque avançado de sintaxe Python

  " Estética e statusline
  Plug 'vim-airline/vim-airline'       " Barra de status leve e customizável

  " Temas visuais
  Plug 'dracula/vim', { 'as': 'dracula'        }  " Tema escuro vibrante
  Plug 'morhetz/gruvbox'                         " Tema retrô claro/escuro
  Plug 'joshdick/onedark.vim'                    " One Dark (Atom) para Vim
  Plug 'navarasu/onedark.nvim'                   " One Dark otimizado em Lua para Neovim
  Plug 'EdenEast/nightfox.nvim'                  " Variedade de temas modernos para Neovim
  Plug 'folke/tokyonight.nvim', { 'branch': 'main' }  " Tema inspirado em Tóquio
  Plug 'NLKNguyen/papercolor-theme'              " Tema minimalista claro/escuro
  Plug 'shaunsingh/nord.nvim'                    " Tema "frio" inspirado no ártico

  " LaTeX
  Plug 'lervag/vimtex'                 " Edição, sintaxe e compilação de LaTeX

call plug#end()

" ============================================
" ==========   Configuração dos Plugins  =====
" ============================================
" Vim-Airline
let g:airline_powerline_fonts = 1       " Usa fontes Powerline

" NERDTree
nnoremap <C-n> :NERDTreeToggle<CR>     " Ctrl-n abre/fecha o explorador

" Startify
let g:startify_lists = [
      \ { 'type': 'sessions', 'header': ['   Sessões'] },
      \ { 'type': 'files',    'header': ['   Recentes'] },
      \ { 'type': 'dir',      'header': ['   Diretório atual'] },
      \ ]

" ALE (Asynchronous Lint Engine)
let g:ale_linters_explicit        = 1
let g:ale_python_flake8_executable = 'flake8'
let g:ale_lint_on_text_changed    = 'never'
let g:ale_lint_on_save            = 1
let g:ale_fix_on_save             = 0

" VimTeX
let g:vimtex_enabled        = 1   " Habilita VimTeX
let g:vimtex_compiler_enabled = 0 " Desativa compilação automática
let g:vimtex_view_enabled     = 0 " Desativa visualizador automático

" Markdown & bullets.vim
let g:vim_markdown_folding_disabled = 1
let g:bullets_enabled_file_types    = ['markdown', 'text', 'gitcommit']

" python-syntax
let g:python_highlight_all = 1

" ============================================
" ==========   Aparência e Interface   =======
" ============================================
colorscheme gruvbox      " Tema ativo
syntax on                " Habilita realce de sintaxe
set background=dark      " Fundo escuro ideal para temas
set number               " Mostra número absoluto de linhas
set relativenumber       " Mostra número relativo de linhas
set cursorline           " Destaque da linha atual
set cursorcolumn         " Destaque da coluna atual
set showcmd              " Exibe comandos incompletos
set laststatus=2         " Sempre mostra statusline
set clipboard=unnamedplus " Usa clipboard do sistema
set mouse=a              " Habilita uso do mouse em todos os modos

" ============================================
" ==========   Comportamento Geral   ========
" ============================================
filetype on
filetype plugin on          " Carrega plugins por tipo de arquivo
set wrap                   " Quebra linha longa na próxima linha da janela
set linebreak              " Quebra em espaços para não cortar palavras
set incsearch              " Busca incremental ao digitar
set ignorecase smartcase   " Busca case-insensitive, exceto se usar letras maiúsculas
set scrolloff=8            " Mantém 8 linhas acima/abaixo do cursor
set hlsearch               " Destaca resultados de busca
set showmode               " Exibe modo atual (insert/normal/visual)
set showmatch              " Destaca parênteses correspondentes
set hidden                 " Permite trocar de buffer sem salvar
set nobackup               " Sem arquivo de backup (~)
set nowritebackup          " Sem backup temporário durante escrita
set noswapfile             " Sem arquivo .swp
set updatetime=300         " Delay curto para eventos (ALE, CursorHold etc.)

" ============================================
" ==========   Indentação e Tabulação   ======
" ============================================
set tabstop=4              " Tab = 4 espaços visuais
set shiftwidth=4           " Auto-indent = 4 espaços
set expandtab             " Converte tab em espaços
set smartindent           " Indentação automática inteligente
set autoindent            " Copia indentação da linha anterior

" ============================================
" ==========   Atalhos e Automação   ========
" ============================================
command! Settings vsplit $MYVIMRC   " Abre init.vim em split vertical
command! Reload   source $MYVIMRC    " Recarrega configurações sem sair

autocmd BufWritePre * silent! %s/\s\+$//e
" Remove espaços em branco no fim de linha ao salvar
```

Salve com `:wq`. Em seguida, abra o Neovim novamente e instale os plugins:

```vim
:PlugInstall
```

---

### **3. Instalar o Neovide, interfaces gráficas para Neovim**

 Instale as dependências (caso não tenha):

```bash
sudo apt update
sudo apt install curl git libgtk-3-dev
```


 Baixe o Neovide pré-compilado, você pode baixar a versão mais recente diretamente do GitHub:

```bash
wget https://github.com/neovide/neovide/releases/download/0.15.0/neovide.AppImage
```

Torne o AppImage executavel:

```bash
chmod +x neovide.AppImage
./neovide.AppImage
```

```bash
cd ~/Downloads
wget https://github.com/neovide/neovide/releases/latest/download/neovide-x86_64.AppImage
chmod +x neovide-x86_64.AppImage
```

Execute o Neovide:

```bash
./neovide.AppImage
```

---

## **4. Extras opcionais no `init.vim`**

Você pode adicionar:

```vim
" ============================================
" ==========   Configurações Neovide   =======
" ============================================
if exists("g:neovide")

  " ===== Fonte =====
  " set guifont=JetBrainsMono\ Nerd\ Font:h14  " Fonte da GUI com suporte a ícones

  " ===== Cursor =====
  let g:neovide_cursor_animation_length = 0.08   " Duração da animação do cursor (0.0 = sem animação)
  let g:neovide_cursor_trail_size = 0.4          " Tamanho do rastro deixado pelo cursor
  let g:neovide_cursor_vfx_mode = "railgun"      " Efeito visual do cursor (ex: railgun, torpedo, pixiedust, ripple, sonicboom, wireframe)
  " let g:neovide_cursor_vfx_mode =              " Desativa o efeito do cursor (alternativa)

  " ===== Rolagem =====
  let g:neovide_scroll_animation_length = 0.1    " Duração da animação de rolagem (scroll)

  " ===== Transparência =====
  let g:neovide_opacity = 0.9               " Transparência da janela (1.0 = opaco, 0.0 = invisível)
  let g:transparency = 0.9                      " (Opcional) compatível com alguns plugins que usam 'g:transparency'

  " ===== Comportamento da janela =====
  " let g:neovide_remember_window_size = v:true    " Salva e restaura o tamanho da janela entre sessões

  " ===== Mouse =====
  let g:neovide_hide_mouse_when_typing = v:true  " Esconde o mouse enquanto digita

  " ===== Teclas modificadoras =====
  let g:neovide_input_use_logo = v:true          " Permite usar a tecla Alt como modificador (útil para acentos e atalhos)

  " ===== Tema exclusivo para Neovide (opcional) =====
  " colorscheme tokyonight                       " Define um tema visual diferente só no Neovide

endif
```

> (A fonte `JetBrainsMono Nerd Font` precisa ser instalada.)
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