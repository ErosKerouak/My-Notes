
---

**Linguagem:** #Python  
**Tags:** #cheatsheet #numpy #arrays #científico

---

##  Importação

```python
import numpy as np
````

---

###  Criação de arrays

- `np.array([1, 2, 3])` → Cria array 1D
    
- `np.array([[1, 2], [3, 4]])` → Cria array 2D
    
- `np.zeros((3, 3))` → Matriz 3×3 de zeros
    
- `np.ones((2, 4))` → Matriz 2×4 de uns
    
- `np.full((2, 2), 7)` → Matriz 2×2 preenchida com 7
    
- `np.eye(3)` → Matriz identidade 3×3
    
- `np.arange(0, 10, 2)` → `[0, 2, 4, 6, 8]`
    
- `np.linspace(0, 1, 5)` → `[0. , 0.25, 0.5, 0.75, 1.]`
    

---

### Indexação e fatiamento

- `a[0]` → Primeiro elemento
    
- `a[1:4]` → Do segundo ao quarto elemento
    
- `a[:, 0]` → Primeira coluna
    
- `a[1, :]` → Segunda linha
    
- `a[-1]` → Último elemento
    
- `a[a > 0]` → Filtro booleano
    

---

###  Forma e transposição

- `a.shape` → Dimensões do array
    
- `a.reshape(2, 3)` → Redimensiona array
    
- `a.flatten()` → Converte para 1D
    
- `a.T` → Transposta do array
    

---

###  Operações elementares

- `a + b`, `a - b`, `a * b`, `a / b` → Operações elemento a elemento
    
- `a ** 2` → Potência
    
- `np.sqrt(a)`, `np.log(a)`, `np.exp(a)` → Funções matemáticas
    

---

###  Estatísticas

- `np.mean(a)` → Média
    
- `np.std(a)` → Desvio padrão
    
- `np.var(a)` → Variância
    
- `np.min(a)` / `np.max(a)` → Mínimo / máximo
    
- `np.median(a)` → Mediana
    
- `np.percentile(a, 90)` → Percentil 90
    
- `np.sum(a, axis=0)` / `axis=1` → Soma por eixo
    

---

### Álgebra linear

- `np.dot(a, b)` → Produto escalar/matriz
    
- `np.matmul(a, b)` → Produto de matrizes
    
- `np.linalg.inv(a)` → Inversa
    
- `np.linalg.det(a)` → Determinante
    
- `np.linalg.eig(a)` → Autovalores e autovetores
    
- `np.linalg.solve(A, b)` → Resolve Ax = b
    

---

###  Aleatoriedade (`np.random`)

- `np.random.rand(3, 3)` → Uniforme entre 0 e 1
    
- `np.random.randn(100)` → Distribuição normal
    
- `np.random.randint(0, 10, 5)` → Inteiros aleatórios
    
- `np.random.seed(42)` → Define semente
    

---

###  Utilidades e transformações

- `np.unique(a)` → Valores únicos
    
- `np.sort(a)` → Ordena array
    
- `np.argsort(a)` → Índices que ordenam
    
- `np.clip(a, min, max)` → Limita os valores
    
- `np.concatenate([a, b])` → Junta arrays
    
- `np.stack([a, b], axis=0)` → Empilha arrays
    
- `np.isnan(a)` / `np.isfinite(a)` → Verifica `NaN` e infinitos
    

---

##  Dicas rápidas

- Arrays são mais rápidos e eficientes que listas
    
- Use `axis=0` para colunas, `axis=1` para linhas
    
- Combine com `matplotlib`, `xarray`, `pandas` para análise completa
    
- `NumPy` é base para quase todo ecossistema científico em Python
    

---
