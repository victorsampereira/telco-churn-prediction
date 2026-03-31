# Previsão de Churn de Clientes em uma Empresa de Telecomunicações

## 1. Introdução e Objetivo do Negócio

O churn de clientes, ou seja, a taxa de cancelamento de serviços, é uma das métricas mais críticas para empresas de telecomunicações. Reter um cliente existente é significativamente mais barato do que adquirir um novo.

O objetivo deste projeto é construir um modelo de Machine Learning capaz de prever quais clientes têm maior probabilidade de cancelar seus serviços. Com essa informação, a empresa pode criar campanhas de retenção direcionadas, oferecendo descontos, suporte proativo ou novos benefícios para os clientes em risco, otimizando assim os investimentos e reduzindo a perda de receita.

**Fonte dos Dados:** [Telco Customer Churn - Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)

---

## 2. Metodologia

O projeto foi estruturado seguindo as principais etapas de um ciclo de vida de ciência de dados:

1.  **Análise Exploratória de Dados (AED):** Investigação inicial dos dados para extrair insights, entender a distribuição das variáveis e a relação delas com a variável alvo (`Churn`).
2.  **Pré-processamento e Engenharia de Features:** Preparação dos dados para a modelagem, incluindo o tratamento de variáveis categóricas e o escalonamento de features numéricas.
3.  **Modelagem e Treinamento:** Treinamento de diferentes algoritmos de classificação para encontrar o que melhor se adapta ao problema.
4.  **Avaliação de Modelos:** Comparação dos modelos utilizando métricas apropriadas para o problema de negócio, com foco especial na identificação correta dos clientes que irão cancelar.

---

## 3. Análise Exploratória de Dados (Principais Insights)

A análise inicial revelou padrões importantes sobre o comportamento dos clientes:

* **Taxa de Churn:** O dataset é desbalanceado, com aproximadamente **26.5%** dos clientes tendo cancelado o serviço.
    ![Distribuição do Churn](images/churn_distribution.png)

* **Impacto do Tipo de Contrato:** Clientes com contratos mensais (`Month-to-month`) têm uma taxa de churn drasticamente maior em comparação com clientes de contratos anuais (`One year`, `Two year`). Isso sugere que contratos de longo prazo são um fator chave na retenção.
    ![Churn por Tipo de Contrato](images/churn_by_contract.png)

* **Tempo de Contrato (Tenure):** Clientes mais novos (baixo `tenure`) têm uma probabilidade muito maior de cancelar. A taxa de churn diminui consistentemente à medida que o cliente permanece mais tempo na empresa.

---

## 4. Resultados dos Modelos

Foram treinados e avaliados três modelos de classificação. A métrica principal para o sucesso do modelo é o **Recall**, pois é mais custoso para a empresa *não identificar* um cliente que vai cancelar (Falso Negativo) do que contatar um que não iria (Falso Positivo).

| Modelo | Acurácia | Precisão (Churn=Sim) | Recall (Churn=Sim) | AUC |
| :--- | :---: | :---: | :---: | :---: |
| Regressão Logística | 0.81 | 0.66 | 0.57 | 0.85 |
| Random Forest | 0.79 | 0.64 | 0.49 | 0.83 |
| **XGBoost Classifier** | **0.80** | **0.65** | **0.55** | **0.84** |

![Matriz de Confusão do Modelo Final](images/confusion_matrix.png)

---

## 5. Conclusão

Embora a Regressão Logística tenha apresentado um bom equilíbrio geral, o **XGBoost Classifier** foi selecionado como o modelo final devido à sua performance robusta e alta capacidade de generalização.

O modelo pode ser utilizado pela equipe de retenção para gerar uma lista semanal de clientes com alta probabilidade de churn. Ações proativas, como ofertas personalizadas e chamadas de suporte, podem então ser direcionadas a esse grupo, maximizando o ROI das campanhas de retenção.

---

## 6. Como Executar o Projeto

Siga as instruções abaixo para replicar o ambiente e executar os notebooks.

1.  **Clone o repositório:**
    ```bash
    git clone https://github.com/victorsampereira/telco-churn-prediction
    cd telco-churn-prediction
    ```

2.  **Crie um ambiente virtual e ative-o:**
    ```bash
    python -m venv venv
    source venv/bin/activate  # No Windows: venv\Scripts\activate
    ```

3.  **Instale as dependências:**
    ```bash
    pip install -r requirements.txt
    ```

4.  **Execute o Jupyter Lab:**
    ```bash
    jupyter lab
    ```
5.  **Navegue pela pasta `notebooks/` e execute os arquivos na ordem numérica.**
