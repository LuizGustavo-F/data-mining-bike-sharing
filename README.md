# Previsão de Demanda - Bike Sharing Dataset

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Data Science](https://img.shields.io/badge/Status-Concluído-success)
![License](https://img.shields.io/badge/License-MIT-green)

Este projeto de Data Mining tem como objetivo prever a quantidade diária de aluguéis de bicicletas com base em condições ambientais e sazonais. O modelo final obteve uma precisão (R²) de **88%**, superando a baseline linear.

---

## Índice
- [Visão Geral](#-visão-geral)
- [Estrutura do Projeto](#-estrutura-do-projeto)
- [Tecnologias Utilizadas](#-tecnologias-utilizadas)
- [Análise Exploratória (Insights)](#-análise-exploratória-insights)
- [Modelagem e Resultados](#-modelagem-e-resultados)
- [Como Executar](#-como-executar)
- [Autor](#-autor)

---

## Visão Geral

O problema consiste em uma tarefa de **Regressão**. Utilizando o *Bike Sharing Dataset* (UCI Machine Learning Repository), buscamos prever a variável `cnt` (contagem total de bicicletas alugadas) utilizando variáveis como temperatura, humidade, velocidade do vento e dias da semana.

**Principais Desafios:**
* Identificar e remover vazamento de dados (*data leakage*) nas colunas `casual` e `registered`.
* Tratar a multicolinearidade entre temperatura real (`temp`) e sensação térmica (`atemp`).
* Capturar a não-linearidade da demanda em dias de clima extremo.

---

## Estrutura do Projeto

A organização de pastas segue o padrão de Ciência de Dados para reprodutibilidade:

```text
├── data/
│   ├── raw/               # Dados originais (imutáveis)
│   └── processed/         # Dados limpos e tratados
├── images/                # Gráficos gerados para análise
├── notebooks/
│   ├── 01_eda.ipynb       # Análise Exploratória e Seleção de Features
│   └── 02_modeling.ipynb  # Treinamento, Tuning e Avaliação dos Modelos
├── README.md              # Documentação do projeto
└── requirements.txt       # Dependências do projeto
````
# Tecnologias Utilizadas

**Linguagem:** Python\
**Manipulação de Dados:** Pandas, NumPy\
**Visualização:** Matplotlib, Seaborn\
**Machine Learning:** Scikit-Learn (Linear Regression, Random Forest,
GridSearchCV)\
**IDE:** VS Code

------------------------------------------------------------------------

# Análise Exploratória (Insights)

Durante a EDA, identificamos fortes correlações que guiaram a seleção de
variáveis.

## 1. Correlação e Vazamento de Dados

Foi identificada uma correlação de **0.95** entre `registered` e o alvo
`cnt`.\
Essas colunas foram removidas para evitar que o modelo "colasse" a
resposta.

## 2. Influência da Temperatura

A relação entre temperatura e aluguéis é positiva, mas não perfeitamente
linear, sugerindo que modelos baseados em árvores poderiam performar
melhor.

------------------------------------------------------------------------

# Modelagem e Resultados

Foram treinados dois modelos para fins de comparação.\
O dataset foi dividido em 70% treino e 30% teste.

### Comparativo de Métricas

  ---------------------------------------------------------------------------
  Modelo                    R² (Score)   MAE (Erro Médio Absoluto)   RMSE
  ------------------------- ------------ --------------------------- --------
  Random Forest (Tuned)     0.8807       462.59                      688.87

  Regressão Linear          0.8508       578.35                      770.39
  ---------------------------------------------------------------------------

**Conclusão:**\
O modelo Random Forest reduziu o erro médio absoluto em cerca de **116
locações por dia** em comparação à Regressão Linear, mostrando melhor
desempenho em capturar padrões sazonais complexos.

------------------------------------------------------------------------

# Visualização das Previsões

O gráfico (não incluído aqui) mostra como o **Random Forest (verde)**
segue mais fielmente os **dados reais (preto)** do que a **Regressão
Linear (azul)** em uma amostra de 50 dias.

------------------------------------------------------------------------

# Como Executar

Para rodar este projeto localmente:

### Clone o repositório:

``` bash
git clone https://github.com/SEU_USUARIO/NOME_DO_REPO.git
```

### Instale as dependências:

``` bash
pip install -r requirements.txt
```

### Execute os notebooks:

Navegue até a pasta `notebooks/` e abra no Jupyter ou VS Code.

------------------------------------------------------------------------

# Autor

Desenvolvido por **Luiz G. F Carvalho**
