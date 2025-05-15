
**Linguagem:** #Python  
**Tags:** #cheatsheet #comandos #linguagem

---

###  Tipos de dados e variáveis

- `x = 10` → Inteiro.
- `pi = 3.14` → Float.
- `nome = "Eros"` → String.
- `valores = [1, 2, 3]` → Lista.
- `tupla = (1, 2)` → Tupla (imutável).
- `conjunto = {1, 2, 3}` → Set (sem repetições).
- `d = {"a": 1}` → Dicionário.

---

###  Controle de fluxo

- `if x > 0:` → Condicional simples.
- `elif x == 0:` → Outra condição.
- `else:` → Caso contrário.
- `for i in lista:` → Itera sobre elementos.
- `while condicao:` → Laço com condição.
- `break` / `continue` → Interrompe ou pula iteração.
- `pass` → Ocupa o lugar de um bloco vazio.

---

###  Funções e escopos

- `def soma(a, b): return a + b` → Define função.
- `lambda x: x * 2` → Função anônima.
- `global x` → Declara variável global.
- `return` → Retorna valor.

---

###  Manipulação de listas

- `lista.append(x)` → Adiciona ao final.
- `lista.pop()` → Remove o último.
- `lista[0]` / `lista[-1]` → Acesso por índice.
- `lista[1:4]` → Fatiamento.
- `[x**2 for x in lista]` → List comprehension.

---

###  Manipulação de arquivos

- `open("arquivo.txt")` → Abre arquivo para leitura.
- `with open("arquivo.txt", "r") as f:` → Abertura segura.
- `f.read()` / `f.readline()` / `f.readlines()` → Leitura.
- `f.write("texto")` → Escrita.

---

### Tratamento de exceções

- `try:` / `except:` / `finally:` → Bloco de erro.
- `except ZeroDivisionError:` → Captura erro específico.
- `raise ValueError("mensagem")` → Gera exceção manual.

---

###  Relacionado a

- [[04-numpy-fundamentos]]
- [[06-pandas]]
- [[02-python-operadores]]
- [[03-python-funcoes-nativas]]
