# DataScience-Combustivel | Previsão e Análise de Séries Temporais

## Visão Geral e Objetivo de Negócio

Este projeto de **Ciência de Dados** aplica técnicas avançadas de **Análise Preditiva e Séries Temporais** sobre a Camada Ouro de dados de preços de combustíveis.

O principal objetivo é **prever a variação do preço médio nacional de venda** para o produto mais volátil (Gasolina ou Diesel) nos próximos 6 a 12 meses. O projeto visa fornecer *insights* estratégicos para empresas do setor de energia ou consumidores, ajudando na tomada de decisões e na mitigação de riscos financeiros.

## Dependência (Camada Ouro)

Este projeto utiliza como base o arquivo analítico de alta qualidade gerado pelo meu repositório de [**Engenharia de Dados**](https://github.com/fernando-marconi/Projeto-Pipeline-Combustivel). O ponto de partida é o arquivo `.parquet` com os preços médios mensais já tratados.

## Stack Tecnológico

| Categoria | Tecnologia | Uso no Projeto |
| :--- | :--- | :--- |
| **Linguagem** | `Python` | Ambiente de modelagem e análise. |
| **Ingestão/Preparação**| `Pandas` | Leitura da Camada Ouro (`.parquet`) e criação de *Lag Features* (variáveis de tempo). |
| **Modelagem TS** | `Statsmodels` (ARIMA/SARIMAX) ou `Prophet` | Implementação do modelo de Séries Temporais para previsão de preços. |
| **Modelagem ML** | `Scikit-learn` ou `XGBoost` | Opcional: Uso de modelos de Regressão para comparação de performance. |
| **Visualização** | `Matplotlib`, `Seaborn` | Análise Exploratória (EDA) e visualização de previsões vs. realidade. |

---

## Metodologia de Ciência de Dados

O projeto segue um fluxo estruturado, desde a preparação dos dados até a avaliação do modelo:

### 1. Ingestão e Análise Exploratória (EDA)

* **Carregamento:** Leitura do arquivo `analitico_dados_combustivel.parquet` (Camada Ouro).
* **Limpeza da Série:** Verificação de *outliers* ou valores anômalos na série temporal.
* **Decomposição:** Análise da série em seus componentes de **Tendência, Sazonalidade e Ruído** para entender o comportamento do preço. 

[Image of Time Series Decomposition]


### 2. Feature Engineering e Teste de Estacionariedade

* **Criação de Variáveis:** Geração de **Lag Features** (preços de meses anteriores) e variáveis de tempo (mês, ano, trimestre) para enriquecer o modelo preditivo.
* **Teste de Estacionariedade:** Aplicação do teste **Augmented Dickey-Fuller (ADF)** para verificar se a série é estacionária, um pré-requisito para modelos ARIMA/SARIMAX.

### 3. Modelagem Preditiva

* **Modelo Principal:** Implementação de um modelo **SARIMAX** (ou Prophet) para capturar tendências e sazonalidade nos dados.
* **Divisão dos Dados:** Utilização de uma janela de tempo para Treinamento e Teste (ex: previsão dos últimos 6 meses com dados de treino anteriores).
* **Ajuste de Hiperparâmetros:** Otimização dos parâmetros do modelo para minimizar o erro de previsão.

### 4. Avaliação e Geração de Insights

* **Métricas de Performance:** Avaliação do modelo usando métricas como **RMSE (Root Mean Square Error)** e **MAPE (Mean Absolute Percentage Error)** para quantificar a precisão da previsão.
* **Previsão de Cenário:** Geração da previsão de preço para os próximos 6 meses.
* **Visualização Final:** Plotagem do gráfico de **Preço Real vs. Preço Previsto**  para demonstrar a acurácia e comunicar o *insight* de negócio.

---

## ✅ Resultados (Exemplo de Previsão)

*(Esta seção será preenchida com dados reais após a execução do seu código. Por enquanto, deixe como placeholder.)*

O modelo de Séries Temporais alcançou um **MAPE de X%** no período de teste, indicando uma alta precisão na previsão de preços. A previsão para o próximo trimestre sugere uma tendência de **[AUMENTO/ESTABILIDADE/QUEDA]** com base nos padrões históricos.
