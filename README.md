## **Desafio Data Science - COGNITIVO.AI**
___

## Luciano Fernandes de Ávila Oliveira
**Dataset:**<br> 
Nosso dataset é uma extração de dados do Airbnb Rio de
Janeiro, conforme fonte:
http://insideairbnb.com/get-the-data.html.
    
**Objetivo:**<br> 
Previsão do preço da estadia **(feature ‘price’)**
___
## Respostas
**a. Como foi a definição da sua estratégia de modelagem?**<br>

- Após o tratamento dos dados, fiz uma pré-seleção de variáveis removendo as que estavam muito correlacionadas, **evitando problemas com multicolinearidade**.
- Para a modelagem, foi escolhido o método ensemble **XGBoost** que combina vantagens de RandomForest e Gradient Boosting, pois é uma implementação de árvores de decisão incrementadas por gradiente.
- Após gerar o modelo inicial, extraí uma tabela de **importância de variáveis** para manter no modelo somente variáveis com maior importância.
- Para tunar o modelo, usei uma grid de hyper-parâmetros do XGBoost para fazer uma busca através de **GridSearch**, testando uma quantidade pré-determinada de combinações de parâmetros usando **validação cruzada**.
<br><br>

**b. Como foi definida a função de custo utilizada?**<br>

Uma função de custo de uma análise supervisionada de regressão mede o quão próximo os valores preditos estão dos valores reais.<br>
Como nosso desafio é de regressão, a função de custo utilizada foi a **RMSE (Root Mean Square Error)**.<br> 
Com essa função de custo, o algoritmo trabalha para reduzir a raiz quadrada da média dos erros ao quadrado.
<br><br>

**c. Qual foi o critério utilizado na seleção do modelo final?**<br>

O modelo escolhido foi o que ofereceu **menor MSE no GridSearch**
<br><br>

**d. Qual foi o critério utilizado para validação do modelo?Por que escolheu utilizar este método?**<br>

Foi usada validação cruzada **(k-fold Cross-Validation)**.<br>
Esse método foi escolhido pois ele nos permite usar todos os dados para treinar e para avaliar(exceto os que foram inicialmente separados para testar o modelo no final).<br>
Ou seja, cada linha do banco de dados é usada k-1 vezes para treinar e 1 vez para avaliar, Desse modo podemos aproveitar melhor todo o dataset.<br>
Esse é o principal motivo de usar validação cruzada em vez de simplesmente treinar o modelo com uma parte dos dados e avaliar com outra parte.
<br><br>

**e. Quais evidências você possui de que seu modelo é suficientemente bom?**<br>

A avaliação final do modelo foi feita em uma parcela não utilizada em nenhum momento da modelagem, nem para treinamento nem para tunagem de parâmetros.<br>
Dessa forma podemos garantir melhor confiabilidade na métrica da avaliação utilizada.
___
