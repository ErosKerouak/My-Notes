
---

**Linguagem:** #Python  
**Tags:** #cheatsheet #pandas #dataframe #dados

---

##  Importação

```python
import pandas as pd
````

---

##  Leitura e escrita de dados

```python
pd.read_csv("arquivo.csv")            # Lê arquivo CSV
pd.read_excel("arquivo.xlsx")         # Lê planilha Excel
pd.read_json("arquivo.json")          # Lê arquivo JSON
df.to_csv("saida.csv", index=False)   # Salva CSV
```

---

##  Criação de DataFrame

```python
data = {"Pais": ["Brasil", "EUA"], "População": [211, 340]}
df = pd.DataFrame(data)
```

---

##  Exploração inicial

```python
df.head(5)          # Primeiras 5 linhas
df.tail(3)          # Últimas 3 linhas
df.shape            # (linhas, colunas)
df.columns          # Lista de colunas
df.info()           # Estrutura geral
df.describe()       # Estatísticas descritivas
```

---

##  Seleção de dados

### Colunas e linhas

```python
df["coluna"]                  # Uma coluna (Series)
df[["col1", "col2"]]          # Múltiplas colunas
df.iloc[0]                    # Linha por índice
df.loc[3]                     # Linha por rótulo
```

### Fatiamento e filtros

```python
df[0:5]                        # Linhas de 0 a 4
df.loc[df["idade"] > 30]       # Filtro por condição
df.query("idade > 30")         # Filtro com string
```

---

##  Manipulação de colunas

```python
df["nova"] = df["valor"] * 2           # Nova coluna
df.rename(columns={"idade": "Idade"})  # Renomeia
df.drop("coluna", axis=1)              # Remove coluna
df.drop([0, 1], axis=0)                # Remove linhas
```

---

##  Tratamento de dados

```python
df.dropna()                  # Remove linhas com NaN
df.fillna(0)                 # Preenche NaNs
df.isna().sum()              # Conta NaNs por coluna
df.duplicated().sum()        # Conta duplicados
df.drop_duplicates()         # Remove duplicados
```

---

##  Agrupamento e agregação

```python
df.groupby("categoria").mean()
df.groupby("tipo").agg({"valor": ["mean", "max", "count"]})
```

---

##  Ordenação

```python
df.sort_values("valor")                     # Crescente
df.sort_values("valor", ascending=False)    # Decrescente
```

---

##  Junções e mesclagens

```python
pd.concat([df1, df2])             # Junta por linhas
pd.merge(df1, df2, on="id")       # Merge por coluna-chave
```

---

##  Datas e tempos

```python
df["data"] = pd.to_datetime(df["data"])
df["ano"] = df["data"].dt.year
df["dia"] = df["data"].dt.day
df["mes"] = df["data"].dt.month
```

---

##  Dicas úteis

- `df.copy()` → Evita modificações não intencionais
    
- `df.apply(func)` → Aplica função a cada linha/coluna
    
- `df["coluna"].map(dicionario)` → Substitui valores por mapeamento
    

---







