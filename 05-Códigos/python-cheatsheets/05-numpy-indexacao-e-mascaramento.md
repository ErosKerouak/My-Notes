
---

**Linguagem:** #Python  
**Tags:** #cheatsheet #numpy #indexação #mascaramento

---

##  Tipos de indexação em NumPy

### 1. Indexação por posição (básica)

```python
a[0]            # Primeiro elemento (1D)
a[1, 2]         # Elemento na linha 1, coluna 2 (2D)
a[0:5]          # Fatiamento
a[:, 0]         # Todas as linhas da primeira coluna
````

---

### 2. Indexação por lista de índices

```python
a[[0, 2, 4]]         # Elementos nas posições 0, 2 e 4
a[:, [1, 3]]         # Colunas 1 e 3 para todas as linhas
a[[1, 3], [2, 0]]    # Elementos (1,2) e (3,0)
```

---

### 3. Máscaras booleanas

```python
a[a > 0]             # Retorna elementos positivos
a[a % 2 == 0]        # Retorna elementos pares
```

 A máscara é um array de booleanos com o mesmo shape de `a`.

---

##  Aplicando máscaras para edição

```python
a[a < 0] = 0         # Substitui valores negativos por 0
a[(a > 0) & (a < 10)] = 1  # Substitui intervalo específico
```

Operadores válidos:

- `&` (and), `|` (or), `~` (not)  
     Use parênteses ao combinar condições.
    

---

##  `np.where()`

```python
np.where(a > 0, 1, -1)    # Se >0, retorna 1, senão -1
```

Pode ser usado para:

- Substituição condicional
    
- Localização de elementos
    

```python
indices = np.where(a == 5)   # Índices onde `a` é 5
```

---

##  `np.nonzero()` e `np.argwhere()`

```python
np.nonzero(a)       # Índices onde os valores são diferentes de zero
np.argwhere(a > 100)  # Retorna coordenadas onde a condição é satisfeita
```

---

## `np.take()` e `np.put()`

```python
np.take(a, [1, 3, 5])     # Extrai posições específicas
np.put(a, [0, 2], [-1, -2])  # Atribui valores em posições específicas
```

---

## Substituições com `np.select()`

```python
condicoes = [a < 0, a == 0, a > 0]
valores = [-1, 0, 1]
np.select(condicoes, valores)
```

Permite aplicar múltiplas condições com valores distintos.

---

##  Indexação com `np.ix_()`

Para extrair submatrizes com listas de linhas e colunas:

```python
rows = [1, 3]
cols = [0, 2]
submat = a[np.ix_(rows, cols)]
```

---

## Atenção com cópia vs. visualização

```python
b = a[a > 0]         # Cria uma cópia
b[0] = 999           # Não afeta `a`

c = a[0:5]           # Cria uma *view* (ligada ao array original)
c[0] = 888           # Altera também `a[0]`
```

Use `a.copy()` se quiser garantir uma cópia independente.

---

##  Dicas finais

- Combine `np.where()` com `np.isnan()` ou `np.isinf()` para tratamento de dados sujos.
    
- Use máscaras para aplicar cálculos seletivos (ex: normalização de valores positivos).
    
- Indexação avançada é mais rápida e legível que loops manuais.
    

---
