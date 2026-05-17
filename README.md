# 🏠 House Price Prediction - End-to-End Machine Learning Project

## 📌 Visão Geral

Este projeto tem como objetivo desenvolver um modelo de Machine Learning capaz de prever o preço de imóveis com base em suas características estruturais, físicas e de localização.

O projeto segue um pipeline completo de ML, incluindo:
- Data Cleaning
- Análise Exploratória de Dados (EDA)
- Detecção e remoção de outliers
- Feature Engineering
- Treinamento de modelos preditivos

Para este projeto foi utilizado os modelos de regressão linear:
'KNN', 'Decision Tree' , 'Ridge','Neural Network', 'Elastic Net', 'Random Forest', 'SVR' e 'XGBoost'.

---

## 📊 Dataset

O dataset utilizado foi obtido do Kaggle:

https://www.kaggle.com/code/ammar111/house-price-prediction-an-end-to-end-ml-project/input

Ele contém diversas variáveis relacionadas a imóveis:

Order, PID, MS SubClass, MS Zoning, Lot Frontage, Lot Area, Street, Alley, Lot Shape, Land Contour, Pool Area, Pool QC, Fence, Misc Feature, Misc Val, Mo Sold, Yr Sold, Sale Type, Sale Condition, SalePrice

---

## 🧠 Pipeline do Projeto

## 1 - Data Cleaning

Foi realizada análise de valores faltantes por coluna.

Pool QC:
- 99,56% de valores ausentes
- Hipótese: ausência indica inexistência de piscina
- Tratamento: preenchido como "No Pool"

Misc Feature:
- 96,38% de valores ausentes
- Tratamento: preenchido como "No Feature"

Garagem e Basement:
- Tratamento específico por registro:
  - No Garage
  - No Basement

Outras variáveis:
- Mas Vnr Area = 0
- Mas Vnr Type = "None"
- Electrical = moda

---

## 2 - OUTLIERS

Outliers prejudicam o modelo.

Foi analisado:

![Gr Liv Area vs SalePrice](/diagrams/scatter_GrLivArea_SalePrice.png)

Casas com GrLivArea > 4000 foram removidas por serem outliers.

---

## 3 - EDA

Análise da variável alvo:

![](/diagrams/boxplot_SalePrice.png)
![](/diagrams/histogram_SalePrice.png)

Correlação entre variáveis:

![](/diagrams/corr_features.png)

Principais variáveis correlacionadas com SalePrice:
- Overall Qual
- Gr Liv Area
- Year Built
- Year Remod/Add
- Mas Vnr Area
- Total Bsmt SF
- 1st Flr SF
- Full Bath
- Garage Cars
- Garage Area

Outras análises:
Queremos analisar as variáveis ​​preditoras que estão correlacionadas com a variável alvo (SalePrice). Vemos que a variável alvo apresenta uma alta correlação positiva com "Overall Qual" e "Gr Liv Area". Observamos também que a variável alvo está positivamente correlacionada com o Year Built, Year Remod/Add, Mas Vnr Area, Total Bsmt SF, 1st Flr SF, Full Bath, Garage Cars, e Garage Area.

![](/diagrams/displot_OverallQual.png)
![](/diagrams/scatter_OverallQual_SalePrice.png)
![](/diagrams/histplot_variables.png)
![](/diagrams/scatter_variables_SalePrice.png)
![](/diagrams/histplot_variables2.png)
![](/diagrams/scatter_variables2_SalePrice.png)

Garagem:
Existem ainda correlações muito fortes entre as variaveis de Garagem, o que de certa forma faz sentido, mas vamos confirmar essa hipotese com graficos.

![](/diagrams/colobar_Garage.png)

Basement:
![](/diagrams/histplot_variables3.png)
![](/diagrams/scatter_variables_BsmtFullBath.png)

---

## 4 - FEATURE ENGINEERING

Foi identificada forte relação entre:
- Overall Qual
- Gr Liv Area
- SalePrice

Foram criadas novas features:

- Quadrado das variáveis:
  - Overall Qual²
  - Gr Liv Area²

- Cubo das variáveis:
  - Overall Qual³
  - Gr Liv Area³

- Interação:
  - Overall Qual × Gr Liv Area

  As features foram normalizadas pelo método StandardScaler().

---

Por fim, assim ficou o Score MAE dos modelos:

![](/diagrams/model_scores.png)

Portanto, o modelo de regressão linear XGBoost desempenhou melhor nos testes.

---

## 🎯 Objetivo

Melhorar a performance do modelo capturando relações não lineares e interações entre variáveis.

---

## 👨‍💻 Conclusão

Projeto completo de Machine Learning para regressão de preços de imóveis, incluindo:
- Limpeza de dados
- Tratamento de outliers
- EDA profunda
- Feature engineering avançado
