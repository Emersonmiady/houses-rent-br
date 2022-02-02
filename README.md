# Aluguéis no Brasil
---
Bom, eu estava navegando pelo *Kaggle* e me deparei com um conjunto de dados a respeito dos valores dos aluguéis em algumas cidades brasileiras. Eu achei ele bem interessante, e já que uma das minhas intenções era treinar o que havia aprendido de ML no *DataCamp*, além de praticar *EDA* e *storytelling*, aceitei investigar um pouco mais nele.

- Análise completa em "**alugueis_brasil.ipynb**".

Observação 1: para melhorar a visualização de algumas imagens, por conta da resolução que foi comprometida, recomendo clicar em "Open in Colab", no começo do *notebook*.

Observação 2: resolvi melhorar ainda mais este projeto criando uma versão 2 dele, juntos com algumas pessoas da minha faculdade para um certo trabalho. Esta segunda versão é apresentada no arquivo "**alugueis_brasil_v2.ipynb**", recomendo muito a sua visualização, pois foi feito uma análise muito mais profunda e detalhada!

# Contexto
---
Um dos maiores desafios que as imobiliárias enfrentam é a precificação de seu imóvel, isso porque o mercado é extremamente dinâmico, logo exige um acompanhamento regular das tendências e perspectivas do setor por certos profissionais. Considerando a instabilidade econômica brasileira nesses últimos anos, esse setor adquiriu ainda mais dificuldades para retomar seu crescimento, sendo este um dos fatores que tornaram a precificação em uma tarefa complexa para as empresas.

Existem muitas coisas que um empreendedor nessa área deve se atentar, como a localização do imóvel, a infraestrutura e certas variáveis de mercado, exigindo uma pesquisa bem elaborada e uma precificação coerente, para que o cliente saia satisfeito e feche seu negócio!

Sendo assim, tentei utilizar o que sabia de ***Machine Learning*** para prever esses valores, além de fazer uma ***EDA*** no *dataset*!

**Base de dados:** Casas para se alugar, em algumas cidades do Brasil, disponível nesse [link](https://www.kaggle.com/rubenssjr/brasilian-houses-to-rent).

# Ferramentas utilizadas
---
- Linguagem de programação Python;
- Pacotes: pandas, numpy, matplotlib, seaborn, sklearn;
- Notebook: Google Colaboratory.

# Descrição breve das etapas
---
## 1. Pré-processamento
- Transformação do "-" na coluna floor para 0;
- Transformação da coluna `floor` em numérica;
- Remoção de **alguns** *outliers*.

## 2. Análise Exploratória dos Dados
Algumas visualizações que obtive estão abaixo:
![](https://github.com/Emersonmiady/houses-rent-br/blob/main/img/accept_animal_city.png?raw=true)
![](https://github.com/Emersonmiady/houses-rent-br/blob/main/img/furniture_city.png?raw=true)
![](https://github.com/Emersonmiady/houses-rent-br/blob/main/img/furniture_rent_amount.png?raw=true)

## 3. Preparando para o ML
1. Retirei as colunas que eu não queria (`floor`, `fire insurance (R$)` e `total (R$)`);
2. Transformei as variáveis categóricas em *dummies*, retirando as redundantes;
3. Dividi as variáveis independentes (X) e dependente (y).

## 4.1. Machine Learning: modelos testados
Foram testados:
- K-Neighbors Regressor;
- Regressão Linear;
- Regressão Ridge;
- Regressão Lasso;
- Decision Tree Regressor;
- Random Forest Regressor.

## 4.2. Machine Learning: Aplicando a modelagem
Após selecionar os modelos, fiz um *cross-validation* com todos eles, para ver qual era o melhor.

## 4.3. Machine Learning: Resultados das métricas
<img src="https://github.com/Emersonmiady/houses-rent-br/blob/main/img/ml_results.png?raw=true">

A métrica de comparação foi o RMSE, e no caso, a Random Forest Regressor obteve o melhor resultado.

## 4.4. Machine Learning: Tuning de Hiperparâmetros
Após escolher o modelo acima, resolvi verificar se haveria alguma forma de melhorá-lo ainda mais, testando diferentes parâmetros. Entretanto, foi possível concluir que mesmo combinando valores nos argumentos do algoritmo, o RMSE não foi menor que o algoritmo padrão do *sklearn*, e portanto, a melhor escolha foi escolher a floresta aleatória de antes.

## 5. Testando o modelo
Resultado do `y_pred` e `y_test`:
![](https://github.com/Emersonmiady/houses-rent-br/blob/main/img/prediction_rf_sklearn.png?raw=true)

Testando uma casa com essas características:
- Área de 250 m²;
- 3 quartos;
- 2 banheiros;
- 1 vaga;
- Valor do condomínio (aproximado): R\$ 1.700;
- Valor do IPTU (aproximado): R\$ 1.000;
- Localizada em São Paulo;
- Permissão da entrada de animais;
- Não sendo mobiliada.

Resultado: seria recomendado um aluguel de R$ 2822.76.
