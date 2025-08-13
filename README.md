# Challenge Telecom Parte 2

## Análise de Evasão de Clientes - Projeto Telecom X

### Descrição do Projeto

Este projeto tem como objetivo analisar os fatores que influenciam a evasão de clientes (churn) em uma empresa de telecomunicações, utilizando técnicas de Ciência de Dados e Machine Learning. A partir dos dados fornecidos, realizamos etapas de pré-processamento, análise exploratória, modelagem preditiva e interpretação dos resultados para apoiar estratégias de retenção de clientes.

---

## Conteúdo do Repositório

- **dados_tratados.csv** — Base de dados tratada e pronta para análise e modelagem.  
- **relatorio_churn.pdf** — Relatório detalhado com a análise dos dados, resultados dos modelos e conclusões.  
- Código fonte para pré-processamento, análise, modelagem e avaliação.

---

## Etapas do Projeto

### 1. Preparação e Tratamento dos Dados
- Remoção da coluna `customerID`, que é um identificador único sem valor preditivo.  
- Expansão das colunas que contêm informações em formato JSON.  
- Conversão da variável alvo `Churn` para numérico (0 para não evadiu e 1 para evadiu).  
- Tratamento de valores nulos e aplicação de codificação one-hot para variáveis categóricas.  
- Aplicação da técnica SMOTE para balanceamento das classes devido ao desbalanceamento identificado (73% clientes ativos, 27% evadidos).

### 2. Análise Exploratória
- Verificação da proporção das classes de churn para entender o desequilíbrio.  
- Análise de correlação entre variáveis numéricas e a evasão, destacando fortes correlações negativas com `tenure` (tempo de contrato) e positivas com `InternetService_Fiber optic` e `Charges.Total`.  
- Investigação detalhada do impacto do tempo de contrato e total gasto no churn, onde clientes que evadiram apresentaram menor tempo de contrato médio e menor gasto total.

### 3. Modelagem Preditiva
- Divisão dos dados em conjuntos de treino (70%) e teste (30%).  
- Criação de dois modelos:  
  - **Regressão Logística** (com normalização dos dados): modelo linear que captura relações diretas entre variáveis e churn.  
  - **Random Forest** (sem normalização): modelo baseado em árvores que captura relações não lineares e interações entre variáveis.

#### Justificativa:
- A normalização foi aplicada na Regressão Logística, pois modelos lineares e baseados em distância (como KNN) são sensíveis à escala dos dados.  
- Random Forest não requer normalização, pois trabalha com regras de decisão e é menos afetado pela escala das variáveis.

#### Resultados:
- Regressão Logística apresentou melhor desempenho geral com acurácia de ~80%, precisão para churn de 66% e recall de 54%.  
- Random Forest teve acurácia de ~78%, precisão de 62% e recall de 47%.

### 4. Interpretação e Importância das Variáveis
- Variáveis mais relevantes segundo Regressão Logística:  
  - `tenure` (tempo de contrato) com forte influência negativa (mais tempo, menor churn).  
  - `Charges.Total` e `InternetService_Fiber optic` com impacto positivo na evasão.  
- Variáveis mais importantes segundo Random Forest:  
  - `Charges.Total`, `tenure` e `Charges.Monthly`.

### Estratégias sugeridas:
- Investir na retenção de clientes com menor tempo de contrato e maior risco de churn.  
- Revisar planos e custos para clientes com altos gastos e serviço de fibra óptica.  
- Oferecer benefícios em contratos de longo prazo para reduzir a evasão.

---

## Como Executar

Clone o repositório:  
```bash
git clone https://github.com/jvca21/Challenge_Telecom_Parte2.git
cd Challenge_Telecom_Parte2
```
## Como Executar

Use o Google colab ou Instale as dependências (recomenda-se usar um ambiente virtual):

```bash
pip install -r requirements.txt
```


## Arquivo de Dados

`dados_tratados.csv`: Este arquivo contém os dados finais, tratados e codificados, usados para treinar e testar os modelos. Inclui as variáveis preditoras e a variável alvo `Churn`.

---

## Contribuições

Contribuições são bem-vindas! Sinta-se à vontade para abrir *issues* e *pull requests* para melhorias.

---

## Autor

João Vitor Cavalcanti Aquino

---

## Licença

Este projeto está sob a licença .
