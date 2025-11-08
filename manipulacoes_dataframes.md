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

pegar o índice de um valor específico em um dataframe
```
indice = df.index[df['coluna'] == 'valor'].tolist()
```

modificando valores (de uma coluna específica)
```
df.loc[df['coluna'] == 'valor 1', 'coluna'] = 'valor 2'
# todos os valores de 'coluna', que antes eram 'valor 1' passarão a ser 'valor 2'
```

One-Hot Encoder
```
# Inicializa o codificador OneHotEncoder para transformar variáveis categóricas em numéricas
ohe_encoder = OneHotEncoder(sparse_output=False)

# Define a lista de colunas categóricas a serem codificadas
categorical_columns = [
    'coluna 1', 'coluna 2', ...
]

# Remove a coluna alvo antes de trabalhar nos atributos
df_features = df.drop(columns=['cargo'])

# Aplica a codificação One-Hot nas colunas categóricas do conjunto de treinamento
encoded_data = ohe_encoder.fit_transform(df_features[categorical_columns])

# Obtém os nomes das novas colunas geradas pela codificação
new_columns = ohe_encoder.get_feature_names_out(categorical_columns)

# Cria um DataFrame com os dados codificados e os novos nomes de colunas
df_ohe = pd.DataFrame(encoded_data, columns=new_columns)

# Remove as colunas categóricas originais do conjunto de treinamento
df_not_phe = df_features.drop(columns=categorical_columns).reset_index(drop=True)

# Concatena o DataFrame com as colunas codificadas ao DataFrame original
X = pd.concat([df_not_phe, df_ohe], axis=1)
```

Label Encoder
```
y = df['coluna alvo']
label_encoder = LabelEncoder()
encoded_label = label_encoder.fit_transform(y)
y = encoded_label
y[:100]
```
