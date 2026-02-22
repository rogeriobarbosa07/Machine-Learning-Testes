## Anotações sobre Machine Learning

### KDD
1. **Seleção**
    - Analisar subconjunto
    - Escolher subconjunto (Atributos independentes + Alvo)
2. **Pré-Processamento** - Limpeza dos dados (Transformar dados "sujos" em dados "confiáveis")
    - Tratamento de dados ausentes (ex: mean, median, most_frequent, KNNImputer)
    - Dados inconsistentes
    - Detectar outliers
    - Etc.
3. **Transformação** - Formatação dos dados
    - Codificação de variáveis categóricas (ex: OneHotEncoder, OrdinalEncoder, LabelEncoder)
        - Adaptar os dados p/valores que o modelo consiga ler (adapta p/ valores numéricos)
        - OneHotEncoder: Cria nova coluna p/cada **categoria** única da sua variável. Atua nas **vars. de Entrada**
        - LabelEncoder: Transformação de **classes** em números (ex: 0, 1, 2 ...). Atua na **var. Alvo**
        - OrdinalEncoder: Parecido com o LabelEncoder, mas projetado para as vars. de Entrada
    - Normalização ou padronização (ex: StandardScaler, MinMaxScaler ou RobustScaler)
    - Seleção e remoção de colunas
    - Criação de novos atributos (Extração de características. Engenharia de atributos)
    - Agregação de valores (Binning)
    - Etc.
4. **Mineração de dados**
    - Escolher modelo
    - Inserir o conjunto "train" (X e y) no algoritmo p/treiná-lo
5. **Avaliação**
    - Inserir o conjunto de teste no modelo treinado p/avaliar o modelo
    - Matriz de confusão
    - Métricas (ex: Accuracy, Precision, Recall, F1-score, MC)

Obs: Definir melhor a diferença entre Pré-processamento e Transformação (ou juntar a explicação dos dois)

Obs2: pode haver mudançãs na ordem

Obs3: não usar outros meio p/prever a classe alvo (deve-se prevê-la apenas na mineração)

### Sobre Vetorização
- De Categorias
    - One-Hot Encoder para atributos com valores não sequenciais
    - Label Encoder para atributos com valores sequenciais (ou manipular valores manualmente por garantia)
- De Classes (alvo)
    - Apenas Label Encoder

### Engenharia de Atributos
- Pré-processamento:
    - Tratamento de valores faltantes
    - Tratamento de Outliers
- Codificação de categorias (One-Hot Encoder, Label Encoder)
- Dimensionamento de características (colocar atributos numéricos na mesma escala)
- Geração e extração de características
    - Binning
    - PCA
    - Decomposição de datas
- Seleção de características importantes (ignorar características irrelevantes)
    - Combater maldição da dimensionalidade: características em excesso deterioram a performance do modelo (causa overfitting)

### Pré-processamento
- Valores Faltantes
    - Excluir ou
    - Preencher: categóricos c/ moda, numéricos c/ mediana
- Outliers
    - Não há regra geral
    - Remover ou normalizar

### Geração e extração de características
- Binning
    - Reduz alta quantidade de atributos
    - Categoria "outros" p/ baixa cardinalidade
- Geração de características: extrair outros atributos a partir de um existente
    - Ex: Data -> Dia, Mês, Ano

### Funções de modelo de ML:
- Instanciando: **modelo = algoritmo(parâmetros)**
- Treinando: **modelo.fit(X_treino, y_treino)**
- Prevendo: **^y = modelo.predict(X_teste)**
- Comparando dados reais c/ previsões: **função_de_comparação(^y, y_teste)**
