# TelecomX_parte2

## 1. Propósito da Análise

O objetivo principal deste projeto foi desenvolver um modelo de Machine Learning para prever a evasão (*churn*) de clientes da empresa de telecomunicações fictícia "Telecom X". A análise visa não apenas identificar clientes com alta probabilidade de cancelar seus serviços, mas também compreender os principais fatores que influenciam essa decisão, permitindo à empresa criar estratégias de retenção mais eficazes e personalizadas.

## 2. Estrutura do Projeto

O projeto é composto pelos seguintes arquivos essenciais, mantidos no mesmo diretório para simplicidade:

```
telecomx_churn_prediction/
├── dados_tratados.csv
├── TelecomX_parte2_BR.ipynb
└── README.md
```

- **`dados_tratados.csv`**: O dataset limpo e pré-processado, pronto para ser carregado pelo notebook.
- **`TelecomX_parte2_BR.ipynb`**: O notebook Jupyter com todo o código, desde a preparação dos dados até a modelagem e interpretação dos resultados.
- **`README.md`**: Este arquivo, com a documentação completa do projeto.

## 3. Preparação dos Dados

Para que os algoritmos de Machine Learning pudessem ser aplicados, os dados passaram por um rigoroso processo de preparação:

- **Classificação das Variáveis:** As variáveis foram identificadas como numéricas (ex: `Meses_Contrato`, `Cobranca_Mensal`) e categóricas (ex: `Servico_Internet`, `Contrato`, `Metodo_Pagamento`).
- **Codificação (Encoding):** Variáveis categóricas binárias (ex: `Possui_Parceiro`) foram codificadas como `0` e `1`. Para as variáveis com múltiplas categorias, foi aplicada a técnica de **One-Hot Encoding** (`pd.get_dummies`), transformando-as em colunas numéricas que o modelo pode processar.
- **Padronização (Standardization):** As *features* numéricas foram padronizadas usando o `StandardScaler` do Scikit-learn. Esta etapa foi crucial para o desempenho da Regressão Logística, garantindo que todas as variáveis contribuíssem de forma equilibrada para o modelo.
- **Separação Treino-Teste:** O conjunto de dados foi dividido em **80% para treino** e **20% para teste** (`train_test_split`), utilizando o parâmetro `stratify` para manter a proporção original de churn em ambos os conjuntos.

## 4. Justificativa da Modelagem

Foram selecionados dois modelos distintos para uma análise comparativa:

1.  **Regressão Logística:** Escolhido como um modelo de *baseline* por sua robustez, rapidez e alta interpretabilidade. Seus coeficientes nos permitem entender facilmente o impacto (positivo ou negativo) de cada variável no churn.
2.  **Random Forest:** Selecionado como um modelo mais complexo e poderoso, capaz de capturar relações não-lineares nos dados. É um algoritmo de *ensemble* conhecido por sua alta precisão e pela capacidade de medir a importância das variáveis.

Após a avaliação, o modelo de **Regressão Logística foi o escolhido**, pois apresentou melhor performance nas métricas de negócio mais relevantes (Recall e F1-Score para a classe Churn) e se mostrou mais estável, sem o *overfitting* observado no Random Forest.

## 5. Exemplos de Gráficos e Insights (EDA)

A análise exploratória revelou padrões importantes. O gráfico abaixo, por exemplo, mostra que o churn está fortemente concentrado em clientes com pouco tempo de contrato.

![Boxplot de Meses de Contrato vs. Churn](https://github.com/user-attachments/assets/64198d0b-18fb-4818-ba0d-a0b2dfc14b63)

Outros insights relevantes incluem:
- **Correlação Negativa Forte:** `Meses_Contrato` e `Contrato_Two year` são os fatores que mais contribuem para a retenção de clientes.
- **Correlação Positiva:** Ter serviço de `Fibra Ótica` e usar `Cheque Eletrônico` como método de pagamento estão fortemente associados a uma maior chance de churn.

## 6. Instruções para Execução do Notebook

Para executar este projeto em seu ambiente local ou no Google Colab, siga os passos abaixo:

1.  **Garanta que os arquivos** `TelecomX_parte2_BR.ipynb` e `dados_tratados.csv` estejam no mesmo diretório.
2.  **Instale as bibliotecas necessárias:**
    ```bash
    pip install pandas matplotlib seaborn scikit-learn jupyter
    ```
3.  **Execute as células do notebook `TelecomX_parte2_BR.ipynb`** de forma sequencial. O notebook está documentado para guiar o usuário através de cada etapa do processo e irá carregar o arquivo `dados_tratados.csv` diretamente.
