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