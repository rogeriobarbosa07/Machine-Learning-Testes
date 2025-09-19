## Anotações do Caderno

### Engenharia de Atributos
- Pré-processamento:
    - Tratamento de valores faltantes
    - Tratamento de Outliers
- Codificação de categorias (One-Hot Encoder, Label Encoder)
- Dimensionamento de características
- Geração e extração de características
    - Binning
    - PCA
    - Decomposição de datas
- Seleção de características importantes (ignorar características irrelevantes)

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