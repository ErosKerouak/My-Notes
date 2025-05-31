
---

# Como instalar e ativar o `nbstripout` para limpar notebooks automaticamente

**Data:** 31-05-2025  
**Tags:** #tutorial #instrucoes #procedimento 

---

## Objetivo

Este tutorial ensina como instalar o `nbstripout` e ativá-lo corretamente em um repositório Git para que notebooks Jupyter (`.ipynb`) tenham seus **outputs e metadados removidos automaticamente** ao serem adicionados com `git add`. Isso ajuda a manter o repositório limpo e com diffs mais legíveis.

---

## Pré-requisitos

- Python com `pip` ou ambiente Conda configurado
    
- Git instalado no sistema
    
- Repositório Git já inicializado (`git init`)
    

---

## Etapas

### 1. Instalar o `nbstripout`

Você pode instalar o `nbstripout` com pip ou conda:

```bash
# Usando pip
pip install nbstripout

# Ou usando conda
conda install -c conda-forge nbstripout
```

---

### 2. Ativar o `nbstripout` no repositório

Se quiser ativar **apenas localmente**, execute:

```bash
nbstripout --install
```

Isso ativa o filtro somente no seu clone, usando `.git/info/attributes`, que **não é versionado**.

Para ativar de forma **versionada**, de modo que outros usuários também recebam a configuração ao clonar o repositório, use:

```bash
nbstripout --install --attributes .gitattributes
```

Esse comando cria (ou modifica) o arquivo `.gitattributes` na raiz do repositório com a regra:

```
*.ipynb filter=nbstripout
```

---

### 3. Confirmar se está funcionando

Você pode verificar onde o filtro está ativo com os seguintes comandos:

```bash
# Se usou ativação local (não versionada)
cat .git/info/attributes

# Se usou ativação versionada
cat .gitattributes

# Ver configuração do filtro no Git
git config --get-regexp filter.nbstripout
```

Agora, ao executar:

```bash
git add notebook.ipynb
```

os outputs e metadados serão automaticamente removidos antes do commit.

---

## Observações

- O `nbstripout` **remove os outputs e os metadados**, mantendo apenas os blocos de código e markdown.
    
- Se você quiser preservar os outputs nos commits, o `nbstripout` **não é a melhor escolha**. Nesse caso, use um script personalizado ou `pre-commit`.
    
- A ativação versionada (`--attributes .gitattributes`) é recomendada para projetos colaborativos.
    

---

## Referências

- [Documentação oficial do nbstripout](https://github.com/kynan/nbstripout)

---

