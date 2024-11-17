# Previsão de Consumo de Energia Elétrica com Rede Neural LSTM

Este projeto utiliza uma Rede Neural Recorrente LSTM para prever o consumo mensal de energia elétrica residencial no Brasil a partir de dados históricos. A previsão do consumo de energia é essencial para ajudar no planejamento e uso eficiente de recursos. Este projeto visa prever o consumo dos próximos 12 meses com base nos dados históricos fornecidos.

## Objetivo

Usar uma rede LSTM para prever o consumo mensal de energia elétrica residencial no Brasil.

## Fonte de Dados

O conjunto de dados utilizado está disponível na plataforma [Base dos Dados](https://basedosdados.org/dataset/3e31e540-81ba-4665-9e72-3f81c176adad?table=b955feef-1649-428b-ba46-bc891d2facc2). O arquivo `consumo_eletrico_brasil.csv` contém dados mensais de consumo residencial de energia ao longo de vários anos.

## Estrutura do Projeto

- **notebooks/**: Contém o notebook Jupyter com o código completo de análise exploratória, pré-processamento, modelagem e previsão.
- **imagens/**: Imagens e gráficos gerados durante o projeto.
- **README.md**: Documento com a explicação completa do projeto.

## Etapas do Projeto

### 1. Entendimento do Problema

A previsão do consumo de energia elétrica é fundamental para o planejamento adequado e para a eficiência do uso de recursos. Utilizamos dados históricos de consumo de energia no Brasil para treinar um modelo LSTM, visando prever o consumo nos próximos 12 meses.

### 2. Análise Exploratória dos Dados

Na análise exploratória, verificamos as características dos dados, incluindo:
- Evolução do consumo ao longo do tempo.
- Análise de tendências e sazonalidades.
- Identificação de valores ausentes e tratamento.

Os gráficos de evolução do consumo mostraram uma tendência de crescimento ao longo dos anos, com variações sazonais. 

### 3. Tratamento dos Dados

O tratamento dos dados incluiu as seguintes etapas:
- **Filtragem**: Consideramos apenas o consumo residencial.
- **Agregação**: Agrupamos os dados por data, somando o consumo e o número de consumidores.
- **Normalização**: Utilizamos `MinMaxScaler` para normalizar as colunas `consumo` e `numero_consumidores` para o intervalo [0, 1].
- **Divisão em Treino e Teste**: Dividimos os dados em 80% para treino e 20% para teste.
- **Criação de Sequências Temporais**: Utilizamos os últimos 12 meses como entrada para prever o próximo mês.

### 4. Desenvolvimento do Modelo LSTM

#### Descrição do Modelo
Utilizamos uma rede neural LSTM, ideal para séries temporais devido à sua capacidade de capturar dependências de longo prazo nos dados.

#### Arquitetura do Modelo
A arquitetura do modelo LSTM consiste em:
- **Uma camada LSTM** com 50 neurônios.
- **Uma camada de Dropout** com taxa de 0,2 para evitar overfitting.
- **Uma camada densa** de saída com ativação linear.
  
O modelo foi compilado com o otimizador Adam e a função de perda MSE (Erro Quadrático Médio).

### 5. Previsão para os Próximos 12 Meses

Após o treinamento do modelo, geramos previsões para os dados de teste e para os próximos 12 meses. Os gráficos abaixo mostram:
- A comparação entre os valores reais e os valores previstos no conjunto de teste.
- As previsões para o consumo dos próximos 12 meses.

![Gráfico de Previsão no Conjunto de Teste](imagens/consumo_real_vs_previsto.png)
![Previsão para os Próximos 12 Meses](imagens/previsao_futura.png)

### 6. Resultados e Conclusões

#### Precisão do Modelo
O modelo apresentou um erro MSE de aproximadamente 753 bilhões e um RMSE de cerca de 867 mil, o que indica que as previsões do modelo estão distantes dos valores reais em termos de precisão. O modelo capturou uma tendência média, mas teve dificuldades em reproduzir os picos e vales do consumo.

#### Importância do Número de Consumidores
O número de consumidores foi incluído como uma variável adicional, pois ele influencia diretamente o consumo total de energia. A inclusão dessa variável ajuda o modelo a capturar melhor o comportamento dos dados.

#### Sugestões de Melhorias
1. **Ajuste de Hiperparâmetros**: Aumentar o número de neurônios, adicionar mais camadas LSTM e ajustar a taxa de dropout podem melhorar o desempenho.
2. **Variáveis Adicionais**: Incluir variáveis como indicadores climáticos ou econômicos pode ajudar o modelo a entender melhor as variações no consumo.
3. **Modelos Alternativos**: Experimentar outras arquiteturas, como modelos híbridos com LSTM e camadas de atenção, pode melhorar a previsão de séries temporais complexas.

---

## Como Executar o Projeto

1. Clone o repositório:
   ```bash
   git clone https://github.com/pazil/Previsao_Consumo_Energia_LSTM.git

2. Instale as dependências:

    pip install -r requirements.txt

3. Abra o notebook "notebooks/analise_exploratoria.ipynb" para seguir todas as etapas do projeto.