

---

**Linguagem:** #Python  
**Tags:** #cheatsheet #pandas #linhas #dataframe

---

##  Seleção de linhas

```python
df.iloc[0]               # Primeira linha (por posição)
df.iloc[2:5]             # Linhas 2 a 4
df.loc[3]                # Linha com índice 3 (por rótulo)
df.loc[[1, 4, 7]]        # Várias linhas por índice
df.head(10)              # Primeiras 10 linhas
df.tail(3)               # Últimas 3 linhas
````

---

##  Filtragem de linhas

```python
df[df["coluna"] > 10]                      # Condição simples
df[df["tipo"].isin(["A", "B"])]            # Valor em lista
df[df["coluna"].str.contains("texto")]     # Condição com texto
df[~df["coluna"].isna()]                   # Remove linhas com NaN
```

---

##  Adicionar linhas

### 1. Usando `loc` (com índice novo)

```python
df.loc[len(df)] = ["valor1", "valor2", ...]
```

### 2. Usando `append()` (descontinuado no pandas >= 2.0)

```python
df = pd.concat([df, pd.DataFrame([nova_linha])], ignore_index=True)
```

---

##  Remover linhas

```python
df.drop(index=5)                          # Remove linha com índice 5
df.drop([0, 2, 4], axis=0)                # Remove múltiplas linhas
df = df[df["coluna"] != "ruido"]          # Remove por condição
```

---

##  Reordenar linhas

```python
df = df.sort_values("coluna")                 # Crescente
df = df.sort_values("coluna", ascending=False)  # Decrescente
df = df.sort_index()                          # Por índice
```

---

##  Modificar valores de linhas

```python
df.loc[0, "coluna"] = 42                    # Altera um valor específico
df.loc[df["cond"] == True, "coluna"] = 0    # Altera várias linhas por condição
```

---

##  Resetar ou redefinir índice

```python
df.reset_index(drop=True, inplace=True)    # Reseta o índice
df.set_index("coluna", inplace=True)       # Define coluna como novo índice
```

---

##  Verificar duplicatas

```python
df.duplicated()                  # Linhas duplicadas
df.drop_duplicates(inplace=True)  # Remove duplicadas
```

---

##  Inserir linha no topo

```python
nova = pd.DataFrame([[...]], columns=df.columns)
df = pd.concat([nova, df], ignore_index=True)
```

---

##  Dicas úteis

- `iloc` e `loc` são fundamentais: use `iloc` para posição, `loc` para rótulo
    
- Use `query()` para filtros legíveis: `df.query("idade > 25 and sexo == 'M'")`
    
- Reindexar pode ajudar após remoção ou ordenação: `df.reset_index(drop=True)`
    

---
