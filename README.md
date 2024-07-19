Projeto LMSYS
================
## Descrição
Esse projeto trata-se na verdade de uma competição no Kaggle, cujo objetivo é dada uma base de dados que contém diversos prompts de conversas com modelos de IA, decidir qual obteve a melhor resposta, em questão de qual o usuário iria preferir, podendo também ocasionar em um possível empate.

## Dados
Segundo a própria descrição do desafio, os dados são compostos pelas seguintes colunas:
*   id - A unique identifier for the row.
*   model_[a/b] - The identity of model_[a/b]. Included in train.csv but not test.csv.
*   prompt - The prompt that was given as an input (to both models).
*   response_[a/b] - The response from model_[a/b] to the given prompt.
*   winner_model_[a/b/tie] - Binary columns marking the judge's selection. The ground truth target column.

## Objetivo
O objetivo é criar um modelo que consiga prever qual modelo de IA teve a melhor resposta, ou se houve um empate, baseando-se nas respostas dadas por ambos os modelos.

### Métodos Planejados e Utilizados
#### Análise Exploratória
Primeiramente, o ideal é fazer uma análise exploratória dos dados, para o melhor entendimento, como a quantidade de vitórias, empates, e derrotas de cada modelo, e a quantidade de prompts que cada modelo respondeu.
#### Contexto
Com isso um tratamento de dados se faz necessário, é válido a utilização da estratégia de Unificar o contexto da Pergunta-Resposta para extrairmos os tokens mais relevantes.
Esses tokens serão utilizados para treinar um modelo de classificação, que irá prever qual modelo teve a melhor resposta, ou se houve um empate.
#### Tokenização 
Para a tokenização, utilizaremos o BertTokenizer, que é um tokenizador do modelo BERT, que é um modelo de linguagem desenvolvido pelo Google, que é um dos modelos estado-da-arte em NLP. 
#### Modelo de Classificação
O modelo de classificação que será utilizado é o BertForSequenceClassification, que é um modelo de classificação de sequências, que utiliza o modelo BERT como base, ele será treinado com os tokens extraídos do contexto da pergunta-resposta.