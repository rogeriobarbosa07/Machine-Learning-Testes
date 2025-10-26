## Anotações sobre Machine Learning

### KDD
1. **Seleção**
    - Analisar subconjunto
    - Escolher subconjunto (Atributos independentes + Alvo)
2. **Pré-Processamento** (Limpeza dos dados)
    - Analisar dados ausentes por atributo
    - Dados inconsistentes
    - Detectar outliers
    - Etc.
3. **Transformação**: Dados precisam ser formatados p/que o algoritmo possa interpretá-los ns etapa seguinte
    - Geração de novos atributos (extração de carcterísticas)
    - Agregação de valores (Binning)
    - Vetorização de categorias
    - Vetorização de classes
    - Adaptar os dados p/valores que o modelo consiga ler (valores numéricos)
    - Etc.
4. Mineração de dados
    - Escolher modelo
    - Inserir o conjunto "train" (X e y) no algoritmo p/treiná-lo
5. Avaliação
    - Inserir o conjunto de teste no modelo treinado p/avaliar o modelo
    - Matriz de confusão
Obs: pode haver mudançãs na ordem
Obs2: não usar outros meio p/prever a classe alvo (deve-se prevê-la apenas na mineração)

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