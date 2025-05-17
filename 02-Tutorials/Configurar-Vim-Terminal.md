
---

**Data:** 17-05-2025  
**Tags:** #tutorial #instrucoes #procedimento #vim

---

## Objetivo


Instalar, configurar e customizar o Vim, além de torná-lo o editor de texto padrão do terminal.

---

## Pré-requisitos

- Acesso a um terminal com permissões de superusuário (`sudo`)
    
- Conexão com a internet

---

## Etapas

### 1. Instale o Vim

Instale o Vim, caso ainda não esteja disponível no sistema.

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

Depois, recarregue com:

```bash
source ~/.bashrc
``` 

---

### 3. {{Etapa 3 — finalização ou verificação}}

Indique como confirmar que tudo funcionou corretamente.

---

## Observações

- {{Notas importantes, armadilhas comuns ou alternativas viáveis}}
    
- {{Links úteis ou complementares}}
    

---

## Referências

- [Documentação oficial](https://.../)
    
- [[Nota interna relacionada]]
    