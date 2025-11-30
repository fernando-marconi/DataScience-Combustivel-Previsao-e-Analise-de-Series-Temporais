# DataScience-Combustivel | Previsão e Análise de Séries Temporais

## Visão Geral e Objetivo de Negócio

Este projeto de **Ciência de Dados** aplica técnicas de **Análise Preditiva e Séries Temporais** sobre a Camada Ouro de dados de preços de combustíveis.

O principal objetivo é gerar **previsões de preço de curto prazo** para a Gasolina, fornecendo *insights* estratégicos para a tomada de decisões no setor de energia.

## Conexão com o Pipeline de Engenharia de Dados (Camada Ouro)

Este projeto é a segunda etapa do meu portfólio. Ele utiliza como base o arquivo analítico gerado do repositório de [**Engenharia de Dados**](https://github.com/fernando-marconi/Projeto-Pipeline-Combustivel). O ponto de partida é o arquivo `.parquet` com os preços médios mensais já tratados.

## Stack Tecnológico

| Categoria | Tecnologia | Uso no Projeto |
| :--- | :--- | :--- |
| **Linguagem** | `Python` | Ambiente de modelagem e análise. |
| **Ingestão/Preparação**| Arquivo `.parquet` (Cama Ouro) | Ponto de partida do projeto, contendo o preço médio mensal limpo. |
| **Modelagem TS** | `Statsmodels` (SARIMAX) | Implementação do modelo de Séries Temporais. |
| **Visualização** | `Pandas`, `Matplotlib`, `Seaborn` | Análise Exploratória (EDA) e visualização das previsões. |

---

## Metodologia e Resultados Preditivos

O projeto segue um fluxo estruturado, desde a preparação dos dados até a avaliação do modelo:

### 1. Preparação da Série
* **Série Temporal (Target):** Preço Médio Nacional da Gasolina, isolado e ajustado para frequência mensal (`ts`).
* **Estacionariedade:** O **Teste ADF** confirmou que a série **NÃO é estacionária** (p-value: 0.2280), justificando a diferenciação (`d=1`) no modelo.

### 2. Modelagem SARIMAX
O modelo **SARIMAX** foi escolhido para capturar as componentes de Autoregressão (AR), Média Móvel (MA) e Sazonalidade (S) inerentes aos preços.

* **Parâmetros (Exemplo):** `order = (1, 1, 1)` e `seasonal_order = (1, 1, 1, 12)`.
* **Divisão:** A série foi dividida para treino e os últimos 6 meses foram reservados para teste de acurácia.

---

## Resultados

O modelo demonstrou um alto poder preditivo, validado pelas métricas abaixo e confirmado pela **sobreposição visual** entre a previsão (marcadores) e a realidade (linha verde).

### Métricas de Performance (Conjunto de Teste)

| Métrica | Valor | Interpretação |
| :--- | :--- | :--- |
| **MAPE** | **1.64%** | O erro médio de previsão é de apenas 1.64%, um resultado de **alta acurácia**. |
| **RMSE** | 0.1356 | Excelente valor para a faixa de preço analisada. |

### Visualização Final e Previsão 

[Image of Time Series Forecast vs Actuals]


A previsão futura (linha preta) sugere uma **tendência de alta constante e gradual** no preço médio nacional.

**Conclusão para o Negócio:** *Stakeholders* devem planejar estratégias de compra e estoque com base em um custo crescente (previsão de **R\$6.19 a R\$6.49** nos próximos 6 meses).
