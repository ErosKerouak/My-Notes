# Dicionário de Caracteres do Vim (Modo Normal)

Este documento visa construir um dicionário sistemático dos **caracteres utilizados no modo normal do Vim**, abordando cada um como uma "palavra" de uma **linguagem analítica**. A proposta é definir:

- O **significado isolado** de cada caractere (se houver)
    
- Um resumo funcional (legenda)
    
- Uma **classificação gramatical** baseada em sua morfologia dentro da "linguagem do Vim"
    

Cada entrada seguirá o seguinte modelo:

```
### a
- Legenda: insert after
- Função isolada: entra no modo de inserção após o cursor
- Classe gramatical: ATM (Atômico)

### A
- Legenda: insert end
- Função isolada: entra no modo de inserção no fim da linha
- Classe gramatical: ATM
```

---

### a

- Legenda: insert after
    
- Função isolada: entra em modo de inserção após o cursor
    
- Classe gramatical: ATM
    

### A

- Legenda: insert EOL
    
- Função isolada: entra em modo de inserção ao fim da linha
    
- Classe gramatical: ATM
    

### b

- Legenda: prev word
    
- Função isolada: move o cursor para o início da palavra anterior
    
- Classe gramatical: ADR
    

### B

- Legenda: prev WORD
    
- Função isolada: move para o início da "WORD" anterior
    
- Classe gramatical: ADR
    

### c

- Legenda: change + mov
    
- Função isolada: requer movimento para executar edição
    
- Classe gramatical: AFX
    

### C

- Legenda: change to EOL
    
- Função isolada: deleta até o fim da linha e entra em inserção
    
- Classe gramatical: ATM
    

### d

- Legenda: delete + mov
    
- Função isolada: requer movimento para executar deleção
    
- Classe gramatical: AFX↻
    

### D

- Legenda: delete to EOL
    
- Função isolada: deleta até o fim da linha
    
- Classe gramatical: ATM
    

### e

- Legenda: end word
    
- Função isolada: move para o fim da palavra atual
    
- Classe gramatical: ADR
    

### E

- Legenda: end WORD
    
- Função isolada: fim da WORD atual
    
- Classe gramatical: ADR
    

### f

- Legenda: find chr →
    
- Função isolada: requer caractere seguinte para localizar
    
- Classe gramatical: AFX
    

### F

- Legenda: find chr ←
    
- Função isolada: requer caractere seguinte para localizar para trás
    
- Classe gramatical: AFX
    

### g

- Legenda: go to
    
- Função isolada: é prefixo de comandos como `gg`, `g~`, etc.
    
- Classe gramatical: AFX↻
    

### G

- Legenda: go EOL
    
- Função isolada: vai para a última linha do arquivo
    
- Classe gramatical: ATM
    

### h

- Legenda: move ←
    
- Função isolada: move o cursor para a esquerda
    
- Classe gramatical: ATM
    

### H

- Legenda: top scrn
    
- Função isolada: move o cursor para o topo da tela
    
- Classe gramatical: ATM
    

### i

- Legenda: insert bef
    
- Função isolada: entra no modo de inserção antes do cursor
    
- Classe gramatical: ATM
    

### I

- Legenda: insert bol
    
- Função isolada: insere no início da linha atual
    
- Classe gramatical: ATM
    

### j

- Legenda: move ↓
    
- Função isolada: move para a linha abaixo
    
- Classe gramatical: ATM
    

### J

- Legenda: join line
    
- Função isolada: une a linha atual com a próxima
    
- Classe gramatical: ATM
    

### k

- Legenda: move ↑
    
- Função isolada: move para a linha acima
    
- Classe gramatical: ATM
    

### K

- Legenda: help word
    
- Função isolada: abre a ajuda para a palavra sob o cursor
    
- Classe gramatical: EXC
    

### l

- Legenda: move →
    
- Função isolada: move o cursor para a direita
    
- Classe gramatical: ATM
    

### L

- Legenda: bot scrn
    
- Função isolada: move o cursor para o fim da tela
    
- Classe gramatical: ATM
    

### m

- Legenda: set mark
    
- Função isolada: requer letra para definir uma marca
    
- Classe gramatical: MRK
    

### M

- Legenda: mid scrn
    
- Função isolada: move o cursor para o meio da tela
    
- Classe gramatical: ATM
    

### n

- Legenda: next srch
    
- Função isolada: repete a última busca para frente
    
- Classe gramatical: ADR
    

### N

- Legenda: prev srch
    
- Função isolada: repete a última busca para trás
    
- Classe gramatical: ADR
    

### o

- Legenda: open bel
    
- Função isolada: insere nova linha abaixo
    
- Classe gramatical: ATM
    

### O

- Legenda: open abv
    
- Função isolada: insere nova linha acima
    
- Classe gramatical: ATM
    

### p

- Legenda: paste aft
    
- Função isolada: cola após o cursor
    
- Classe gramatical: ATM
    

### P

- Legenda: paste bef
    
- Função isolada: cola antes do cursor
    
- Classe gramatical: ATM
    

### q

- Legenda: rec mac
    
- Função isolada: inicia/encerra gravação de macro
    
- Classe gramatical: MRK
    

### Q

- Legenda: ex mode
    
- Função isolada: entra no modo Ex (pouco usado)
    
- Classe gramatical: CTL
    

### r

- Legenda: repl chr
    
- Função isolada: requer caractere para substituir
    
- Classe gramatical: AFX
    

### R

- Legenda: repl mode
    
- Função isolada: entra em modo de substituição
    
- Classe gramatical: CTL
    

### s

- Legenda: sub chr
    
- Função isolada: substitui caractere por inserção
    
- Classe gramatical: ATM
    

### S

- Legenda: sub line
    
- Função isolada: substitui linha inteira por inserção
    
- Classe gramatical: ATM
    

### t

- Legenda: till →
    
- Função isolada: requer caractere para mover até antes
    
- Classe gramatical: AFX
    

### T

- Legenda: till ←
    
- Função isolada: requer caractere para mover até antes (reverso)
    
- Classe gramatical: AFX
    

### u

- Legenda: undo
    
- Função isolada: desfaz última ação
    
- Classe gramatical: ATM
    

### U

- Legenda: undo line
    
- Função isolada: desfaz todas as mudanças na linha
    
- Classe gramatical: ATM
    

### v

- Legenda: vis char
    
- Função isolada: entra em modo visual
    
- Classe gramatical: MOD
    

### V

- Legenda: vis line
    
- Função isolada: modo visual linha
    
- Classe gramatical: MOD
    

### x

- Legenda: del chr
    
- Função isolada: deleta caractere sob cursor
    
- Classe gramatical: ATM
    

### X

- Legenda: del prev
    
- Função isolada: deleta caractere anterior ao cursor
    
- Classe gramatical: ATM
    

### y

- Legenda: yank + mov
    
- Função isolada: requer movimento para copiar
    
- Classe gramatical: AFX↻
    

### Y

- Legenda: yank line
    
- Função isolada: copia a linha atual (equivale a `yy`)
    
- Classe gramatical: ATM
    

### z

- Legenda: scroll opt
    
- Função isolada: prefixo para rolagem (`zz`, `zt`, `zb`)
    
- Classe gramatical: AFX↻
    

### Z

- Legenda: save quit
    
- Função isolada: prefixo de `ZZ` (salva e sai)
    
- Classe gramatical: AFX↻


### Referencias

[https://irian.to/blogs/mastering-vim-grammar](https://irian.to/blogs/mastering-vim-grammar)

[https://yanpritzker.com/learn-to-speak-vim-verbs-nouns-and-modifiers-d7bfed1f6b2d](https://yanpritzker.com/learn-to-speak-vim-verbs-nouns-and-modifiers-d7bfed1f6b2d)

[https://takac.github.io/2013/01/30/vim-grammar/](https://takac.github.io/2013/01/30/vim-grammar/)

[https://gist.github.com/countvajhula/0721a5fc40f2124097652071bb9f97fb](https://gist.github.com/countvajhula/0721a5fc40f2124097652071bb9f97fb)

[https://learnvim.irian.to/basics/vim_grammar](https://learnvim.irian.to/basics/vim_grammar)

[https://glts.github.io/2013/04/28/vim-normal-mode-grammar.html](https://glts.github.io/2013/04/28/vim-normal-mode-grammar.html)

[https://www.freecodecamp.org/news/vim-language-and-motions-explained/](https://www.freecodecamp.org/news/vim-language-and-motions-explained/)

--- 

[https://youtu.be/wlR5gYd6um0?si=W-gabN4ffOR-MfQp](https://youtu.be/wlR5gYd6um0?si=W-gabN4ffOR-MfQp)


**Síntese do texto "Mastering Vim grammar"**

O artigo apresenta uma abordagem didática para aprender a usar o editor de texto Vim de forma mais intuitiva, comparando seu funcionamento ao aprendizado de um novo idioma — chamado pelo autor de _Vimish_. A estrutura fundamental da "gramática do Vim" é simples: **verbo + substantivo**, onde os _verbos_ são operadores (como `d` para deletar, `y` para copiar, `c` para alterar) e os _substantivos_ são movimentos (`w`, `e`, `}` etc.), objetos de texto (`iw`, `i{`, `a"` etc.), buscas (`f`, `t`, `/` etc.) e marcas (`'a`, `` `a ``).

O autor destaca que, com o domínio de poucos verbos e substantivos, é possível construir comandos poderosos e eficientes. Exemplos incluem comandos como `d2w` (deletar duas palavras) ou `di(` (deletar conteúdo dentro de parênteses). A ideia central é que, assim como em qualquer idioma, a fluência em Vim exige vocabulário, regras gramaticais e prática constante, até que o uso se torne automático. O artigo conclui incentivando o leitor a experimentar e praticar, enfatizando que a produtividade é o objetivo principal.