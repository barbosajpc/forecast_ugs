# Forecast UGs Notebook

Este repositório contém um notebook Jupyter (`forecast_ugs.ipynb`) utilizado para
análise e previsão de séries temporais de Unidades Geradoras (UGs) no estado do Piauí.

## Objetivo

Realizar comparação entre modelos estatísticos e de aprendizado de máquina para
previsão de séries temporais univariadas. O melhor modelo, de acordo com as
métricas de avaliação, é selecionado para a análise final.

## Dados

- Arquivo: `UGs.csv` (dados mensais de unidades geradoras de energia elétrica
  fornecidos pela ANEEL).
- Importante frisar que o arquivo UGs.csv foi tratado previamente à implementação do estudo de forecasting
- Período utilizado: a partir de junho de 2017.
- Série univariada com 91 observações após preprocessamento.

## Metodologia

1. Carregamento e preparação da série temporal.
2. Análise exploratória (gráfico da série, decomposição clássica).
3. Teste de estacionariedade (ADF) na série original e em sua primeira
   diferença.
4. Criação de variáveis defasadas (lags) e features trigonométricas para
   sazonalidade.
5. Divisão temporal entre conjunto de treino (todas as observações menos os
   últimos 12 meses) e teste (últimos 12 meses).
6. Treinamento dos modelos:
   - ARIMA (busca por ordem mínima de AIC)
   - SARIMA (com sazonalidade de 6 meses)
   - Decision Tree
   - Random Forest
   - XGBoost
   - MLP (rede neural multilayer perceptron)
   - LSTM (rede neural recorrente)
7. Avaliação dos modelos na janela de teste usando MAE, RMSE, MAPE e R².
8. Verificação de overfitting nos modelos de aprendizado de máquina.

## Resultados

Os resultados são gravados em arquivos de saída:

- `output_model_comparison.csv`: comparativo das métricas para cada modelo.
- `output_overfit_check.csv`: métricas de treino/teste para verificar overfitting.
- Várias figuras em formato PNG mostrando a série, decomposição, ACF/PACF e a
  comparação entre valores reais e previsão do melhor modelo.

O melhor modelo segundo RMSE foi o SARIMA com configuração (2,1,2)x(1,1,1,6).

## Dependências

O notebook utiliza as seguintes bibliotecas Python:

- pandas
- numpy
- matplotlib
- scikit-learn
- xgboost
- statsmodels
- tensorflow / keras

## Como executar

1. Clone o repositório.
2. Instale as dependências (por exemplo, via `pip install -r requirements.txt`).
3. Abra e execute `forecast_ugs.ipynb` em um ambiente Jupyter.

## Autores

- João Pedro Coelho Barbosa
- Luis Eduardo Alencar Melo

## Licença

Livre para uso acadêmico.
