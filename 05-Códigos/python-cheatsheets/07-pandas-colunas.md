
---

**Linguagem:** #Python  
**Tags:** #cheatsheet #pandas #colunas #dataframe

---

##  Criar e atribuir colunas

```python
df["nova_coluna"] = 0                     # Valor constante
df["dobro"] = df["valor"] * 2             # Baseada em outra coluna
df["texto"] = df["nome"].str.upper()      # Manipulação de strings
````

---

##  Selecionar colunas

```python
df["coluna"]                 # Uma coluna (Series)
df[["col1", "col2"]]         # Múltiplas colunas (DataFrame)
df.columns                   # Lista com os nomes das colunas
```

---

##  Renomear colunas

```python
df.rename(columns={"velho": "novo"})
```

**Para vários ao mesmo tempo:**

```python
df.rename(columns={"a": "A", "b": "B"}, inplace=True)
```

---

##  Remover colunas

```python
df.drop("coluna", axis=1)                # Remove uma
df.drop(["a", "b"], axis=1, inplace=True)  # Remove várias
```

---

##  Reordenar colunas

```python
df = df[["nome", "idade", "email"]]     # Ordem desejada
```

---

##  Aplicar função em colunas

```python
df["log"] = df["valor"].apply(np.log)          # Usando NumPy
df["tamanho"] = df["nome"].apply(len)          # Função nativa
```

---

##  Substituir valores em colunas

```python
df["coluna"] = df["coluna"].replace("ruido", "desconhecido")
df["coluna"] = df["coluna"].map({"A": "Alfa", "B": "Beta"})
```

---

##  Filtrar DataFrame com base em colunas

```python
df[df["coluna"] > 10]                        # Condição simples
df[df["tipo"].isin(["A", "B"])]              # Filtro por grupo
df[~df["coluna"].isna()]                     # Remover NaN
```

---

##  Alterar tipo de dados da coluna

```python
df["data"] = pd.to_datetime(df["data"])
df["codigo"] = df["codigo"].astype(str)
```

---

## Renomear todas as colunas com função

```python
df.columns = [col.lower() for col in df.columns]     # Tudo minúsculo
df.columns = df.columns.str.strip()                  # Remove espaços
```

---

## Dica para reorganizar (coluna no início)

```python
col = "nova"
df = df[[col] + [c for c in df.columns if c != col]]
```

---


