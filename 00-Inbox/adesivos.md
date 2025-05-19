Quero deixar estabelecido um sistema de regras rigoroso e sistemático para compor os adesivos. Como as regras que existem para a própria tabela periódica dos elementos químicos.

Para isso, é importante ter em mente que o que estou fazendo não é exatamente uma tebela periódica de comandos, e nem uma tabela periódica de teclas, na verdade é uma tabela de caracteres. Não é uma tabela periódica de comandos, porque a maior parte dos comandos do vim é realizado pela combinação de dois ou mais caracteres, sendo que nem todos os caracteres são capazes de executar um comando ao serem digitados isoladamente. E não é uma tabela periódica de teclas, porque cada tecla contem dois caracteres, um quando clicamos `tecla`, e outro quando clicamos `shift+tecla`.   

A principio, cada adesivo deve conter no minimo:

```
┌───────────┐
|shift+tecla| ← caractere
|  legenda  | ← legenda curta
|───────────|
|   tecla   | ← caractere
|  legenda  | ← legenda curta
└───────────┘
```

Posso pensar em incluir mais coisas depois (sigla da categoria por exemplo).

Algumas regras que já estabeleci:

1. Usando símbolos, palavras e abreviações, as legendas devem descrever da melhor maneira possível os comandos associados aos caracteres, sem desobedecer a cetas condições.
	
2. As legendas não podem ter mais de 2 palavras.
    
3. As palavras não podem ter mais de 3 letras.
    
4. Se uma palavra com mais de 3 letras for necessária, abreviações ou símbolos devem ser usados no lugar.
    
5. As abreviações usadas devem ser consistentes.
    
6. Preferencialmente, abreviações devem se parecer o suficiente com a palavra para serem fáceis de entender de forma intuitiva.

Essas regras ainda podem mudar. Mas lebre-se disso, quero deixar as regras explicadas no README quando tudo estiver pronto.

Uma coisa que ainda preciso decidir, é como lidar com caracteres que  não executam comandos ao serem digitados isoladamente. O ideal, é ter uma regra, ou um conjunto de regras, para isso. Pensei em uma regra, que já soluciona boa parte dessas ocorrências:

- Se um caractere não executar nenhum comando ao ser digitado isoladamente no modo normal, o comando executado ao digitar tal caractere duas vezes atribuirá a legenda. 

Isso já resolve para `dd`,  `gg`, `yy` e `zz`. 

Acho que o ideal é construir um conjunto separado de regras, que definam a atribuição de legendas aos caracteres. Poderia começar assim:

1. Se um caractere executar um comando ao ser digitado isoladamente no modo normal, o comando executado ao digita-lo atribuirá a legenda. 
2.  Se um caractere não executar nenhum comando ao ser digitado isoladamente no modo normal, o comando executado ao digita-lo duas vezes atribuirá a legenda. 
3.  Se um caractere não executar nenhum comando ao ser digitado isoladamente no modo normal, e nem ao ser digitado duas vezes, ...

Do 3 em diante eu terei que pensar, e investigar caso a caso.

Uma coisa que seria util, é um sistema de classificação separado para os caracteres. A do sistema de classificação das funções. Esse sistema não serviria para dizer o que o caractere faz, mais sim para indicar como ele se comporta na gramatica do vim.  

Por exemplo, caracteres que não executam nada isoladamente poderiam ser afixos estritos, ou algo assim. Se ele não executam nada isoladamente, mas executa ao ser repetido, poderia ser um afixo estrito recursivel. 

Vale a pena fazer uma revisão bibliográfica sobre isso, é bem provável que algo desse tipo já exista.   

Eu ainda vou definir as cores dos adesivos com base na classificação dos comandos. Mas eu poderia deixar essa classificação gramatical dos caracteres indicada de alguma outra forma, talvez uma sigla com uma fonte menor. Seria mais util do que uma sigla da categoria da função, que já sera indicada pela cor. 

Tendo esse enfoque gramatical, eu acho que precisávamos começar fazendo um dicionario de caracteres no modo normal do vim. Incluindo não apenas as letras maiúsculas e minusculas, como também os outros símbolos que compõem comandos no modo normal do vim. Se encararmos os comandos do vim como uma língua analítica, cada caractere é uma palavra. Vamos tentar definir o que cada uma dessas palavras significa individualmente, e como elas poderiam ser classificadas. 

