<div align="center">

# ☕ Café, Estresse e Sono: Da Análise de Dados à Recomendação de Negócio

**Análise exploratória, geração de insights e modelagem preditiva sobre a relação entre consumo de café, estresse e qualidade do sono**

</div>


## 📌 Sobre o projeto

Este projeto simula uma demanda real de negócio: a empresa precisa entender como o consumo de café se relaciona com a qualidade do sono de seus clientes, a fim de orientar produtos, campanhas e conteúdos de saúde e bem-estar.

O trabalho percorre o ciclo completo de um projeto de Ciência de Dados — da limpeza e exploração dos dados até a modelagem preditiva — com foco constante em **transformar resultados estatísticos em decisões de negócio acionáveis**.

## ❓ Pergunta de negócio

> Como o consumo de café, o estresse e outros hábitos de vida se relacionam com a qualidade do sono dos clientes — e como a empresa pode usar isso para orientar melhor seus usuários?


## 🗃️ Sobre os dados

Dataset: [**Global Coffee Health Dataset**](https://www.kaggle.com/datasets/uom190346a/global-coffee-health-dataset) (Kaggle) — 10.000 registros sintéticos de participantes em 20 países.

| Categoria | Variáveis |
|---|---|
| Demográficas | Idade, Gênero, País |
| Consumo | Xícaras de café/dia, Cafeína (mg/dia), Tabagismo, Álcool |
| Sono | Horas de sono, Qualidade do sono |
| Saúde | IMC, Frequência cardíaca, Nível de estresse, Atividade física, Condições de saúde |
| Ocupacional | Ocupação principal |

## 🧭 Metodologia

O notebook está estruturado em três partes, seguindo o fluxo padrão de um projeto de dados aplicado:

| Etapa | O que foi feito |
|---|---|
| **1. Análise Exploratória (EDA)** | Verificação de dimensões, tipos, dados ausentes e duplicados · estatísticas descritivas · distribuições e outliers (skewness, boxplots) · matriz de correlação |
| **2. Visualização & Insights** | Gráficos comparativos (heatmaps, boxplots, linhas) · segmentações por gênero e faixa etária · formulação de insights de negócio |
| **3. Modelagem Preditiva** | Engenharia de features · pipeline de pré-processamento (evitando vazamento de dados) · treino e comparação de 3 modelos de classificação · avaliação e discussão crítica dos resultados |


## 🔎 Principais insights

| Achado | Evidência |
|---|---|
| Estresse é o maior "vilão" do sono — mais que o café | Correlação estresse × qualidade do sono: **r ≈ -0,91** vs. café × sono: **r ≈ -0,19** |
| Alto consumo de cafeína reduz o sono | Clientes com ≥ 400 mg/dia dormem **0,63h a menos** que clientes com < 200 mg/dia |
| Estresse alto = menos horas de sono | Baixo: **7,25h** · Médio: **5,58h** · Alto: **4,45h** por noite |
| Estresse impulsiona o consumo de café | Consumo médio de café cresce com o nível de estresse, principalmente entre 18–69 anos |
| Gênero não é um fator relevante | Padrões de sono e estresse muito semelhantes entre Male, Female e Other |
| Café não afeta IMC nem atividade física | Tendências lineares praticamente nulas entre essas variáveis |



## 🤖 Modelagem preditiva

**Alvo:** `Sleep_Quality` (Poor · Fair · Good · Excellent) — classificação multiclasse.

| Modelo | F1-macro (Validação Cruzada) | F1-macro (Teste) | Observação |
|---|:---:|:---:|---|
| **Regressão Logística** ⭐ | 0,9923 | ~0,99 | Melhor equilíbrio viés-variância, sem sinais de overfitting |
| LightGBM | 1,0000 | ~0,99 (0,96 na classe Excellent) | Indícios de overfitting |
| XGBoost | 1,0000 | ~0,99 (0,96 na classe Excellent) | Indícios de overfitting |

✅ **Modelo escolhido:** Regressão Logística, por generalizar melhor para dados não vistos.

O pré-processamento (`OneHotEncoder` + `StandardScaler`) foi encapsulado em um `Pipeline`/`ColumnTransformer`, ajustado somente sobre os dados de treino em cada fold da validação cruzada estratificada (`StratifiedKFold`) — prática que evita vazamento de informação entre treino e teste.


## 💼 Recomendações para o negócio

| Ação | Baseada em |
|---|---|
| **Alertas de consumo de cafeína** para clientes acima de 400 mg/dia, sugerindo redução gradual | Relação cafeína × horas de sono |
| **Priorizar programas de gestão de estresse** (mindfulness, atividade física, terapia digital) na proposta de valor | Estresse é o fator mais associado ao sono |
| **Conteúdo educativo sobre o ciclo estresse → café → sono ruim**, ajudando o cliente a quebrar o padrão | Associação entre estresse e maior consumo de café |
| **Segmentação de campanhas por faixa etária** (foco em 18–69 anos) | Efeito mais evidente nessa faixa etária |
| **Score preditivo de risco de sono ruim** integrado a painel/app, para ação preventiva | Modelo de Regressão Logística |
| **Comunicação transparente** sobre correlação vs. causalidade, reforçando busca por acompanhamento profissional | Limitações estatísticas e de dataset |


## 🧠 Skills demonstradas

`Análise Exploratória de Dados (EDA)` `Estatística Descritiva` `Visualização de Dados` `Engenharia de Features` `Machine Learning (Classificação)` `Validação Cruzada` `Pipelines com Scikit-learn` `Diagnóstico de Data Leakage` `Storytelling com Dados` `Tradução de Resultados Técnicos em Recomendações de Negócio`

## 🛠️ Tecnologias utilizadas

- **Python 3**
- **Pandas** / **NumPy** — manipulação e análise de dados
- **Matplotlib** / **Seaborn** — visualização de dados
- **Scikit-learn** — pré-processamento, pipelines, validação cruzada, Regressão Logística
- **LightGBM** / **XGBoost** — modelos de gradient boosting
- **Pickle** — serialização do modelo final

