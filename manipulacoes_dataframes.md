inicializar dataframe:
```
df = pd.read_csv('dados.csv')

# ou

df = pd.read_excel('dados.xlsx')
```

mostrar df:
```
df
```

mostrar primeiras 5 linhas do df:
```
df.head()
```

excluir coluna(s):
```
df = df.drop(columns=['coluna', 'coluna2', ...])
```

passar valores de certa(s) coluna(s) para outro dataframe:
```
df2 = df['coluna', 'coluna2', ...].values
```

novo df com coluna(s) especificada(s)
```
df2 = df['coluna', 'coluna2', ...]
```

mostrar número de colunas e linhas:
```
df.shape
```

mostrar número de valores nulos em cada coluna do df:
```
df.isnull().sum()

# ou

print(df.isnull().sum())
```

mostrando os diferentes valores de um coluna e o número de quanto a coluna possui de cada valor:
```
df['coluna'].value_counts()
```

preenchendo valores nulos de uma coluna com a moda:
```
df['coluna'].fillna('valor da moda', inplace=True)
```

desvio padrão de uma coluna (apenas numérico):
```
desvio = df['coluna'].std()
desvio
```

verificando outliers
```
df.loc[X['coluna'] >= 2 * desvio, 'coluna']
```

mediana de uma coluna
```
mediana = df['coluna'].median()
mediana
```

eliminando os outliers (nesse caso, preenchendo com a mediana)
```
df.loc[df['coluna'] >= 2 * desvio, 'coluna'] = mediana
df.loc[df['coluna'] >= 2 * desvio]
```

data binding (binning) - condensando excesso de valores diferentes em um valor único
```
df.loc[df['coluna'] == 'valor 1', 'coluna'] = 'outros'
df.loc[df['coluna'] == 'valor 2', 'coluna'] = 'outros'
agrupado = df.groupby(['coluna']).size()
agrupado

# agrupado conterá os valores condensados como 'outros'
```

(outra forma de binning - ex: binning de minérios diversos)
```
minerios_agrupados = {
    "Rochas de Construção": [
        "GRANITO", "MÁRMORE", "BASALTO", "GNAISSE", "ARENITO", "QUARTZITO",
        "CALCÁRIO", "DOLOMITO", "SIENITO", "DIABÁSIO", "FILITO", "ARDÓSIA",
        "PEGmatito", "GRANODIORITO"
    ],
    "Materiais de Areia e Argila": [
        "AREIA", "AREIA QUARTZOSA", "AREIA DE FUNDIÇÃO", "AREIA P/ VIDRO",
        "AREIA INDUSTRIAL", "ARGILA", "ARGILA REFRATÁRIA", "ARGILA COMUM",
        "CAULIM", "BENTONITA"
    ],
    "Minérios Metálicos": [
        "MINÉRIO DE FERRO", "FERRO", "MINÉRIO DE MANGANÊS", "MANGANÊS",
        "MINÉRIO DE COBRE", "COBRE", "MINÉRIO DE NÍQUEL", "NÍQUEL",
        "MINÉRIO DE ZINCO", "ZINCO", "MINÉRIO DE CHUMBO", "CHUMBO",
        "MINÉRIO DE ESTANHO", "ESTANHO", "MINÉRIO DE TITÂNIO", "TITÂNIO",
        "MINÉRIO DE CROMO", "CROMO", "MINÉRIO DE LÍTIO", "LÍTIO",
        "MINÉRIO DE ALUMÍNIO", "ALUMÍNIO", "BAUXITA"
    ],
    "Minérios Nobres e Preciosos": [
        "OURO", "MINÉRIO DE OURO", "PRATA", "MINÉRIO DE PRATA", "PLATINA",
        "MINÉRIO DE PLATINA", "DIAMANTE", "DIAMANTE INDUSTRIAL"
    ],
    "Gemas e Minerais Ornamentais": [
        "ESMERALDA", "AMETISTA", "TOPÁZIO", "TURMALINA", "QUARTZO RÓSEO",
        "ÁGATA", "GRANADA", "CITRINO", "OPALA"
    ],
    "Minerais Industriais": [
        "FELDSPATO", "FLUORITA", "GRAFITA", "TALCO", "MICA", "MOSCOVITA",
        "BARITA", "GIPSITA", "APATITA"
    ],
    "Combustíveis e Energéticos": [
        "CARVÃO", "CARVÃO MINERAL", "TURFA", "ANTRACITO"
    ],
    "Águas Minerais": [
        "ÁGUA MINERAL", "ÁGUA POTÁVEL DE MESA", "ÁGUAS TERMAIS"
    ]
}

mapa_substancia = {
    substancia: categoria
    for categoria, substancias in minerios_agrupados.items()
    for substancia in substancias
}

df["Categoria"] = df["Substância(s)"].map(mapa_substancia).fillna("Outros")

df['Categoria'].value_counts()
```

geração de características (ex: data -> dia, mes, ano)
```
# transformando data em valor padrão do sistema
df['DATA'] = pd.to_datetime(df['DATA'], format='%d/%m/%Y')
df['DATA']

# gerando as novas características
X['ANO'] = X['DATA'].dt.year
X['MES'] = X['DATA'].dt.month
X['DIA'] = X['DATA'].dt.day
```

valores diferentes de uma coluna
```
df['coluna'].unique()
```

removendo linhas duplicadas do dataframe
```
df_filtrado = df_filtrado.drop_duplicates()
```

mostrar o nome das colunas do dataframe
```
df.columns
```

remover linhas com valores nulos com base em uma coluna
```
df = df.dropna(subset=['coluna'])
```

preenchendo valores nulos de uma coluna passando um valor específico
```
df['formacao'].fillna('valor de preenchimento, inplace=True)
```
removendo linha especificada do dataset
```
# n é o número da linha que se deseja remover
df2 = df.drop(index=0)
```

renomeando colunas
```
renomear_colunas = {
    'coluna1': 'col1',
    'coluna2': 'col2',
    ...
}

df2 = df_tratado.rename(columns=renomear_colunas)
df2.columns

# os novos nomes serão os que aparecem depois dos 2 pontos (:)
```

separando valores de uma coluna para novas colunas (ex: localização -> x, y)
```
df2 = pd.DataFrame()
df2[['x', 'y']] = df['Localização'].str.split(', ', expand=True)

# df2 terá as novas colunas com os valores que foram separados
```

converter valores de uma coluna (ex: str p/ float)
```
# uma coluna
df2['coluna'] = df['coluna'].astype(float)

# várias colunas
df2[['coluna1', 'coluna2', ...]] = df[['coluna1', 'coluna2', ...]].astype(float)

```

Obs: adicionar LabelEncoder, OneHotEncoder