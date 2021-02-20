# Aluguéis no Brasil
---
Bom, eu estava navegando pelo *Kaggle* e me deparei com um conjunto de dados a respeito dos valores dos aluguéis em algumas cidades brasileiras. Eu achei ele bem interessante, e já que uma das minhas intenções era treinar o que havia aprendido de ML no *DataCamp*, além de praticar *EDA* e *storytelling*, aceitei investigar um pouco mais nele.

- Análise completa em "**alugueis_brasil.ipynb**".

Observação: para melhorar a visualização de algumas imagens, por conta da resolução que foi comprometida, recomendo clicar em "Open in Colab", no começo do *notebook*.
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
- Transformação do "-" na coluna floor para 0.

## 2. Análise Exploratória dos Dados
Algumas visualizações que obtive estão abaixo:
![](https://github.com/Emersonmiady/houses-rent-br/blob/main/img/accept_animal_city.png?raw=true)
![](https://github.com/Emersonmiady/houses-rent-br/blob/main/img/furniture_city.png?raw=true)
![](https://github.com/Emersonmiady/houses-rent-br/blob/main/img/furniture_rent_amount.png?raw=true)
![](https://github.com/Emersonmiady/houses-rent-br/blob/main/img/prediction_rf.png?raw=true)

## 3. Preparando para o ML
1. Retirei as colunas que eu não queria (`floor` e `hoa (R$)`);
2. Transformei as variáveis categóricas em *dummies* e retirei as redundantes;
3. Dividi em 0.2 de teste e apliquei o `StandardScaler()` para a padronização dos dados, já que ultilizaríamos modelos regressivos.

## 4. Machine Learning: modelos testados
Foram testados:
- K-Neighbors Regressor;
- Regressão Linear;
- Regressão Ridge;
- Regressão Lasso;
- Decision Tree Regressor;
- Random Forest Regressor.

## 4. Resultados das métricas
<img src="https://github.com/Emersonmiady/houses-rent-br/blob/main/img/ml_results.png?raw=true">

A métrica de comparação "score" era a "R-squared", e no caso, a Random Forest obteve o melhor resultado.

## 5. Testando o modelo
Testando uma casa com essas características:
- Área de 250 m²;
- 3 quartos;
- 2 banheiros;
- 1 vaga;
- Valor do condomínio (aproximado): R\$ 1700;
- Valor do seguro incêndio (aproximado): R\$ 60;
- Valor total exigido pelo cliente (aproximado): R\$ 8000;
- Localizada em São Paulo;
- Permissão da entrada de animais;
- Não sendo mobiliada.

Seria recomendado um aluguel de R$ 5054.35!
