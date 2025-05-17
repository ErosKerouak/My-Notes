
---

**Data:** 17-05-2025  
**Tags:** #tutorial #instrucoes #procedimento #vim

---

## Objetivo


Instalar e configurar o Vim, além de torná-lo o editor de texto padrão do terminal.

---

## Pré-requisitos

- Acesso a um terminal com permissões de superusuário (`sudo`)
    
- Conexão com a internet

---

## Etapas

### 1. Instale o Vim

Instale o Vim, caso ainda não esteja disponível no sistema:

```bash
sudo apt install vim
```

---

### 2. Torne o Vim o editor de texto padrão do terminal

Configure a variável de ambiente `EDITOR` e `VISUAL` no arquivo `~/.bashrc`:

1. Abra o arquivo `~/.bashrc`:

```bash
vim ~/.bashrc
```

2. Adicione as linhas abaixo no final do arquivo:

```bash
export EDITOR=vim
export VISUAL=vim
```

3. Depois, recarregue com:

```bash
source ~/.bashrc
``` 

---

### 3. Configurações iniciais do vim

Instale o gerenciador de plugins [vim-plug](https://github.com/junegunn/vim-plug):

```bash
curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
     https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

Em seguida, crie e edite o arquivo *Vim Run Commands* (`~/.vimrc`):

```bash
vim ~/.vimrc
```

Para instalar plugins com o _vim-plug_, adicione a estrutura básica abaixo ao `~/.vimrc`:

```vim
call plug#begin('~/.vim/plugged')

" Liste os plugins desejados aqui. Por exemplo:
" Plug 'preservim/nerdtree'

call plug#end()
```

Então, os plugins listados podem ser instalados ao abrir o Vim e rodar:

```vim
:PlugInstall
```

---

### 4 Customizando o Vim


O arquivo `~/.vimrc` é o **arquivo de configuração do Vim para o usuário**. Ele é carregado automaticamente toda vez que você inicia o Vim. Por meio dele, você pode:

* Configurar o comportamento padrão do editor
* Personalizar a interface (cores, número de linhas, etc.)
* Criar **atalhos de teclado**
* Definir **comandos personalizados**
* Ativar e configurar **plugins**
* Escrever **funções automatizadas** em Vimscript

Para como montar um `~/.vimrc` veja: [[Customizando-Vim-Neovim]]

---

## Observações

- {{Notas importantes, armadilhas comuns ou alternativas viáveis}}
    
- {{Links úteis ou complementares}}
    

---

## Referências

- [Documentação oficial](https://www.vim.org/docs.php) 