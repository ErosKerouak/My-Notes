
---

**Linguagem:** #Python  
**Tags:** #cheatsheet #funcoes #python-puro #builtin

---

###  Funções de tipos e conversão

| Função     | O que faz                                                 |
| ---------- | --------------------------------------------------------- |
| `int(x)`   | Converte `x` para inteiro                                 |
| `float(x)` | Converte `x` para ponto flutuante                         |
| `str(x)`   | Converte `x` para string                                  |
| `bool(x)`  | Converte para `True` ou `False`                           |
| `list(x)`  | Converte para lista                                       |
| `tuple(x)` | Converte para tupla                                       |
| `set(x)`   | Converte para conjunto (sem repetições)                   |
| `dict()`   | Cria um dicionário vazio ou a partir de pares chave-valor |

---

###  Funções de containers

| Função                      | O que faz                               |
| --------------------------- | --------------------------------------- |
| `len(obj)`                  | Retorna o número de elementos           |
| `sorted(iterável)`          | Retorna uma lista ordenada              |
| `reversed(seq)`             | Retorna um iterador reverso             |
| `enumerate(iterável)`       | Retorna pares `(índice, valor)`         |
| `zip(a, b, ...)`            | Agrupa elementos de múltiplos iteráveis |
| `range(início, fim, passo)` | Gera sequência de números               |

---

###  Funções matemáticas simples

| Função | O que faz |
|--------|-----------|
| `abs(x)` | Valor absoluto |
| `round(x[, n])` | Arredonda `x` (opcionalmente com `n` casas) |
| `pow(x, y)` | Calcula `x` elevado a `y` (equivalente a `x**y`) |
| `max(iterável, ...)` | Maior valor |
| `min(iterável, ...)` | Menor valor |
| `sum(iterável)` | Soma os valores |

---

###  Testes e verificação

| Função | O que faz |
|--------|-----------|
| `isinstance(obj, tipo)` | Verifica se `obj` é de certo tipo |
| `type(obj)` | Retorna o tipo do objeto |
| `id(obj)` | Retorna o identificador único (endereço na memória) |
| `all(iterável)` | Retorna `True` se todos os elementos forem verdadeiros |
| `any(iterável)` | Retorna `True` se algum elemento for verdadeiro |

---

###  Entrada e saída

| Função | O que faz |
|--------|-----------|
| `print(...)` | Exibe algo na tela |
| `input(mensagem)` | Lê uma entrada do usuário como string |

---

###  Funções funcionais

| Função | O que faz |
|--------|-----------|
| `map(func, iterável)` | Aplica `func` a cada item |
| `filter(func, iterável)` | Filtra itens para os quais `func` retorna `True` |
| `eval(expr)` | Avalia uma string como expressão Python |
| `exec(código)` | Executa código Python (mais geral que `eval`) |

---

###  Criação de objetos especiais

| Função | O que faz |
|--------|-----------|
| `open(arquivo, modo)` | Abre um arquivo |
| `range()` | Cria iterador de números inteiros |
| `slice(início, fim, passo)` | Define fatia (usado em fatiamento avançado) |
| `object()` | Cria um objeto base vazio |
| `classmethod()` / `staticmethod()` | Define métodos especiais em classes |
| `property()` | Cria propriedades em classes |

---

###  Tratamento de erros

| Função | O que faz |
|--------|-----------|
| `help(obj)` | Abre ajuda interativa |
| `dir(obj)` | Lista atributos e métodos de um objeto |
| `globals()` / `locals()` | Retorna variáveis globais/locais do ambiente atual |
| `__import__('modulo')` | Importa módulo dinamicamente |

---