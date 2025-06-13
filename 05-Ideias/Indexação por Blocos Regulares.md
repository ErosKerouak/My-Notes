
Achei essa logica fascinate:
```python
# Verifica bloco 3x3
start_row = (row // 3) * 3
start_col = (col // 3) * 3
end_row = start_row + 3
end_col = start_col + 3

for i in range(start_row, end_row):
	for j in range(start_col, end_col):
		if board[i][j] == num:
			return False
```

Dificilmente pensaria em algo assim sozinho, pelo menos não sem o conhecimento prévio de uma aplicação  exemplo, o que atá agora eu não tinha. 

`row` e `col` são as coordenadas de `num`, podendo ser números de 0 a 8. `num` pode estar em qualquer lugar em uma grade que vai de $row = 0$ até $row = 8$; e $col = 0$ até $col = 8$. A matriz $9 \times 9$ é dividida em 9 blocos $3 \times 3$. Precisamos fazer uma busca no bloco de `num`, mas não sabemos em qual bloco `num` vai cair. Uma forma de resolver isso, é passar todas as possibilidades explicitamente:

```python
if row <= 2:
  if col <= 2:
    for i in range(3):
      if board[i][i] == num:
        return False
  if 2 < col <= 5:
    for i in range(3):
      for j in range(3, 6):
        if board[i][j] == num:
            return False
  if 5 < col <= 8:
    for i in range(3):
      for j in range(6, 8):
        if board[i][j] == num:
          return False
if 2 < row <= 5:
  if col <= 2:
    for i in range(3, 6):
      for j in range(3):
      if board[i][j] == num:
        return False
  if 2 < col <= 5:
    for i in range(3, 6):
        if board[i][i] == num:
            return False
  if 5 < col <= 8:
    for i in range(3, 6):
      for j in range(6, 8):
        if board[i][j] == num:
          return False
if 5 < row <= 8:
  if col <= 2:
    for i in range(6, 8):
      for j in range(3):
      if board[i][j] == num:
        return False
  if 2 < col <= 5:
    for i in range(6, 8):
      for j in range(3, 6)
        if board[i][j] == num:
            return False
  if 5 < col <= 8:
    for i in range(6, 8):
        if board[i][i] == num:
          return False
```

Mas e se pudêssemos determinar quais `row` e `col` delimitam o bloco de `num` apenas pelo `row` e `col` de `num`? Podemos fazer isso simplesmente fazendo:

```python
start_row = (row // 3) * 3
start_col = (col // 3) * 3
end_row = start_row + 3
end_col = start_col + 3
```

O que achei mais interessante, é que só funciona porque a indexação no python começa sempre por zero. Se a indexação começasse por um, o que sei que é o caso para algumas linguagens de programação, a logica ainda poderia ser usada, mas o código ficaria um pouco mais verboso.

---

## **Indexação por Blocos Regulares**

A **indexação por blocos regulares** é uma técnica fundamental em programação e ciência de dados para localizar rapidamente uma região de interesse dentro de uma estrutura dividida uniformemente, como vetores, matrizes, grades ou séries temporais.

### **Objetivo**

Determinar, a partir de um índice ou coordenada arbitrária, qual **bloco**, **janela**, **chunk**, **bin**, ou **voxel** contém esse elemento, sem precisar fazer comparações manuais ou varreduras completas.

### **Lógica típica**

Usa divisão inteira e multiplicação para encontrar os limites do bloco:

```python
start = (index // block_size) * block_size
end = start + block_size
```

Esse padrão permite:

- Identificar rapidamente um bloco 3×3 no Sudoku.
    
- Criar janelas fixas em séries temporais.
    
- Dividir arrays em chunks para processamento paralelo.
    
- Localizar células de uma malha espacial em geociências.
    
- Indexar dados em bancos de dados por partições.
    

### **Conceitos relacionados**

- Chunking / Partitioning
    
- Windowing (janelas deslizantes)
    
- Binning (em histogramas e geodados)
    
- Grid indexing (em geoprocessamento)
    
- Spatial hashing / voxel grids (em 3D e computação gráfica)
    

### **Vantagens**

- Simplicidade algorítmica
    
- Eficiência computacional
    
- Redução de comparações lógicas
    
- Elegância quando combinada com indexação iniciando em zero
    

---