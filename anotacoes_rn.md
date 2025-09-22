## Anotações sobre Redes Neurais

### Diagrama do funcionamento do perceptron
Entrada (x1, x2, ..., xn)    
           ▼  
Pesos (w1, w2, ..., wn) + Bias (b)  
           ▼  
Combinação Linear (função de previsão)  
z = w1*x1 + w2*x2 + ... + wn*xn + b  
           ▼  
Função de Ativação f(z)  
           ▼  
Saída do Neurônio (ŷ)  

Interpretação:
- Entrada: os atributos do dataset (sem a variável dependente).
- Pesos + Bias: cada entrada é multiplicada pelo seu peso e somada ao bias.
- Combinação Linear (z): igualzinho à previsão da regressão.
- Função de Ativação: transforma z em algo mais útil (probabilidade, não-linearidade, etc).
- Saída ŷ: é o que o neurônio “decidiu” retornar, que pode ir para outro neurônio ou ser a previsão final.

### Observações
1. Pesos são diferentes para cada perceptron na rede, mas o bias é único (mesmo valor p/ todos os perceptrons)
2. Pesos servem para treinar a rede: são ajustados no processo de treinamento

### Epoch vs Iteration vs Batch size
- Epoch: uma passagem por todos os dados de treino
- Iteração: cada passagem de todos os dados do registro
- Batch size: equivale ao número de registros que serão passados por cada iteração

Outra forma:
- Batch size: é como se fosse o pacote de dados que alimenta a rede em uma iteração.
- Iteração: é o processo de treinar a rede com um lote (um batch) e atualizar os pesos.
- Epoch/Época: é quando o modelo fez iterações o suficiente para que **todo** o dataset tenha passado pela rede uma vez.

### Aprendizado Online vs Batch
- Online: os pesos podem ser atualizados a cada instância (final da iteração)
- Batch: os pesos só são atualizados após todas as instâncias (final da epoch)

### Sobre o erro (loss)
- "Existe uma taxa de aprendizado que ajusta os pesos"
- "Com esses ajustes, a rede busca aprender padrões nos dados"
- "O erro diminui ao longo do treinamento da rede"
- "O processo busca um mínimo (não necessariamente o global) na curva de erro"

### Backpropagation
- O que é: é o algoritmo utilizado para treinar as redes neurais (como a rede neural aprende), ajustando os pesos de cada conexão
- Etapas:
    1. Forward pass: Os dados de entrada passam pela rede, que gera uma saída ^y
    2. Cálculo do erro: compara y com ^y, usando uma função de custo (ex: MSE, MAE)
    3. Backward pass: Calcula o gradiente da função de custo em relação aos pesos utilizando Regra da Cadeia. O erro volta da camada de saída até a de entrada, ajustando cada peso de cada conexão
    4. Atualização dos pesos: os pesos são ajustados com o **Gradiente Descendente**: w[i+1] = w[i] - η.(∂E/∂w)
    - Obs: com o gradiente e o ajuste dos pesos, o erro diminuirá e a função de erro se aproximará de um mínimo (local ou global)
    - Obs2: o peso antigo é usado como base para o peso atualizado (não se dá chute em peso, e utiliza valores antigos para aprendizado)
    - Obs3: o quanto eu atualizo depende do tamanho do passo e da inclinação da reta