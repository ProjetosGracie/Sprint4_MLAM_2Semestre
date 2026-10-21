# Sprint 4 — Classificação Linear com Energia Renovável

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white" alt="Pandas">
  <img src="https://img.shields.io/badge/Scikit--learn-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white" alt="Scikit-learn">
  <img src="https://img.shields.io/badge/Machine_Learning-6C63FF?style=for-the-badge" alt="Machine Learning">
</p>

<p align="center">
  Projeto acadêmico de Machine Learning desenvolvido na disciplina de Machine Learning (MLAM), no curso de Ciência da Computação da FIAP.
</p>

---

## Sobre o projeto

O **Sprint 4 — Classificação Linear com Energia Renovável** tem como objetivo desenvolver um modelo de Machine Learning capaz de classificar níveis de produção de energia renovável com base em variáveis climáticas e operacionais.

Para isso, foi utilizada a **Regressão Logística (*Logistic Regression*)**, um algoritmo de classificação que permite prever uma entre três categorias de produção energética:

- **Low:** baixa produção de energia.
- **Medium:** média produção de energia.
- **High:** alta produção de energia.

O projeto também investiga como diferentes proporções de treinamento e teste influenciam o desempenho do modelo, mantendo as demais condições experimentais constantes.

## Equipe

**Turma:** 1CCPJ  
**Disciplina:** Machine Learning (MLAM)  
**Curso:** Ciência da Computação — FIAP

| Integrante | RM |
|:---|:---|
| André Fujinaga | RM569158 |
| Arthur Machado | RM569919 |
| Conrado Gracie | RM569157 |
| Guilherme Belo | RM570079 |
| Renato Sandreschi | RM569156 |

## Dataset

O projeto utiliza o **Renewable Energy Production Dataset (2010–2020)**, conjunto de dados com informações relacionadas à produção de energia renovável.

| Característica | Descrição |
|:---|:---|
| Período de referência | 2010–2020 |
| Quantidade de registros | 1.000 |
| Quantidade de colunas | 11 |
| Valores nulos | Nenhum |
| Variável-alvo | `Energy_Class` |
| Tipo de problema | Classificação multiclasse |
| Classes | Low, Medium e High |

A variável `Energy_Class` foi codificada numericamente para permitir o treinamento do modelo:

| Classe original | Valor codificado |
|:---|:---:|
| Low | 0 |
| Medium | 1 |
| High | 2 |

## Tecnologias utilizadas

- **Python:** linguagem utilizada para implementação e análise.
- **Pandas:** carregamento, manipulação e exploração dos dados.
- **Scikit-learn:** pré-processamento, validação cruzada, treinamento e avaliação do modelo.
- **StandardScaler:** padronização das variáveis numéricas.
- **LogisticRegression:** algoritmo de classificação utilizado.
- **Matplotlib / Seaborn:** visualização de dados e matrizes de confusão, caso utilizadas no notebook.

## Metodologia

O desenvolvimento foi dividido em etapas para garantir uma avaliação consistente do modelo.

### 1. Análise exploratória dos dados

- Carregamento do dataset com Pandas.
- Verificação da estrutura e da qualidade dos dados.
- Identificação da variável-alvo.
- Análise da correlação de Pearson entre as variáveis numéricas e o alvo.
- Investigação da relação entre as features e a classificação da produção energética.

### 2. Seleção de features

Foram mantidas todas as **7 features numéricas** utilizadas no experimento.

A decisão foi fundamentada em dois pontos:

- A maior correlação observada entre as features foi de aproximadamente `0.26`, indicando associações lineares relativamente baixas entre os pares analisados.
- A validação cruzada apresentou desempenho próximo de `0.80` utilizando todas as features, superior aos resultados de aproximadamente `0.74` a `0.77` obtidos com subconjuntos avaliados.

A variável `Efficiency_Ratio` apresentou a maior correlação individual observada com o alvo, aproximadamente `0.21`.

Esses resultados sustentaram a decisão de manter todas as sete variáveis no modelo final.

### 3. Modelo de classificação

O algoritmo escolhido foi a **Regressão Logística**, implementada por meio da classe `LogisticRegression`, da biblioteca Scikit-learn.

Apesar do nome, a Regressão Logística é utilizada principalmente para problemas de classificação. No caso multiclasse, o modelo estima as probabilidades associadas às categorias e realiza a classificação a partir delas.

O modelo é considerado linear porque utiliza combinações lineares das features para construir suas funções de decisão. No espaço original das variáveis, suas fronteiras de decisão são lineares,
