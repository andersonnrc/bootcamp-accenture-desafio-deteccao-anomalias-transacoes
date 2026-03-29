# 🛡️ Detecção de Fraudes em Cartões de Crédito com Machine Learning

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Google Colab](https://img.shields.io/badge/Colab-F9AB00?style=for-the-badge&logo=googlecolab&color=525252)
![Pandas](https://img.shields.io/badge/Pandas-2C2D72?style=for-the-badge&logo=pandas&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/scikit_learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-1793E1?style=for-the-badge&logo=xgboost&logoColor=white)

## 📌 Visão Geral do Projeto
Este projeto tem como objetivo desenvolver um modelo de Machine Learning capaz de identificar transações fraudulentas em cartões de crédito. O principal desafio técnico abordado é o **desbalanceamento extremo dos dados**, onde as fraudes representam menos de 0,2% das transações totais.

O projeto explora técnicas de pré-processamento, estratégias de amostragem (Undersampling vs. SMOTE) e a otimização de algoritmos baseados em árvores (Random Forest e XGBoost) para maximizar a detecção de fraudes (*Recall*) minimizando o bloqueio de clientes legítimos (*Precision*).

---

## 🏗️ Arquitetura e Etapas de Desenvolvimento

O pipeline de dados foi construído seguindo as seguintes etapas:

1. **Análise Exploratória (EDA):** Carregamento do dataset público (Kaggle) e identificação do desbalanceamento (0.17% de fraudes).
2. **Pré-processamento:** Aplicação do `RobustScaler` nas variáveis `Time` e `Amount` para mitigar o impacto de outliers, mantendo as variáveis numéricas anonimizadas (V1 a V28) geradas por PCA.
3. **Estratégias de Balanceamento:**
   * **Random Undersampling:** Redução da classe majoritária.
   * **SMOTE (Oversampling):** Geração de dados sintéticos para a classe minoritária.
4. **Treinamento e Avaliação de Base (Random Forest):** Comparação entre os modelos treinados com Undersampling (alto recall, baixa precisão) e SMOTE (equilíbrio ideal).
5. **Modelagem Avançada (XGBoost):** Implementação do Extreme Gradient Boosting utilizando a base balanceada pelo SMOTE.
6. **Otimização de Hiperparâmetros:** Utilização do `RandomizedSearchCV` para encontrar a configuração matemática ideal do XGBoost, focando na métrica *F1-Score*.
7. **Explicabilidade do Modelo (Feature Importance):** Extração das variáveis mais relevantes para a tomada de decisão do algoritmo.

---

## 📊 Resultados e Conclusões

A evolução dos modelos demonstrou o clássico *trade-off* entre *Precision* e *Recall* no contexto de fraudes:

* **Random Forest (Undersampling):** Paranoico. Detectou quase todas as fraudes (Recall: 90%), mas gerou mais de 2.000 falsos positivos (Precision: 4%).
* **Random Forest (SMOTE):** Equilibrado. Reduziu os falsos positivos para apenas 14, mantendo um Recall sólido de 81%.
* **XGBoost Otimizado (Modelo Final):** O modelo campeão conseguiu detectar **86.7% das fraudes reais**, gerando apenas 34 falsos positivos em um universo de quase 57.000 transações legítimas avaliadas no conjunto de teste.

A análise de **Feature Importance** revelou que o valor absoluto da compra (`Amount`) e o tempo (`Time`) têm peso irrelevante na detecção. O modelo pauta suas decisões primariamente em padrões ocultos de comportamento, sendo a variável anonimizada `V14` responsável por quase 63% do peso preditivo.

---

## 🚀 Como Executar o Projeto

A execução do script `Jupyter Notebook` foi realizada no `Google Colab`.

---

## 🧑‍💼 Contato

[Linkedin](https://www.linkedin.com/in/anderson-ribeiro-carvalho)