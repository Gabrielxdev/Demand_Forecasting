# Previsao de Demanda no Varejo

## 1. Visao Geral do Projeto
Este projeto consiste no desenvolvimento de um modelo preditivo de ponta a ponta para estimar a demanda de pecas no setor de varejo. O objetivo principal e ajudar na tomada de decisao estrategica, prevendo a quantidade de unidades que serao vendidas com base em fatores como preco, nivel de estoque, campanhas promocionais e precos dos concorrentes.

O pipeline acompanha desde a Analise Exploratoria de Dados (EDA) ate a construcao de um aplicativo web interativo para simulacoes de cenarios em tempo real.

## 2. Estrutura da Solucao

O projeto foi estruturado em tres grandes etapas (Inicio, Meio e Fim):

### Inicio: Exploracao e Analise de Dados
No arquivo `notebook/EDA.ipynb`, a base de dados corporativa e analisada criticamente. As etapas incluem:
* Limpeza e tratamento de valores ausentes.
* Descoberta de padroes estatisticos e correlacao entre o desconto praticado e o pico da demanda.
* Visualizacao do impacto do preco dos concorrentes nas vendas.

### Meio: Engenharia de Recursos e Modelagem
A Inteligencia Artificial foi lapidada dentro do arquivo `notebook/ML.ipynb`:
* Preparacao dos dados: Variaveis textuais (como Categoria) foram transformadas usando `LabelEncoder` (cujos dicionarios foram salvos em `label_encoders.pkl`).
* O algoritmo escolhido para a previsao numerica foi o **XGBoost Regressor**, que demonstrou excelente performance para prever a variancia da demanda.
* O modelo treinado foi serializado e salvo usando Pickle (`xgboost_demand_model.pkl`).

### Fim: Aplicacao e Deploy
A entrega para o usuario final e feita de forma amigavel atraves do script `notebook/app.py`, construido com o framework web Streamlit.
* Interface na qual o gestor e capaz de inserir atributos do produto (preco atual, percentual de desconto planejado, categorias) e receber instantaneamente a previsao da demanda para aquele cenario especifico.
* Este aplicativo consome diretamente os arquivos `.pkl` gerados na fase anterior, fechando o ciclo de desenvolvimento (MLOps).

## 3. Estrutura de Arquivos

* `data/`: Diretorio alocado para dados originais (bloqueado pelo .gitignore).
* `notebook/EDA.ipynb`: Analise Exploratoria.
* `notebook/ML.ipynb`: Treinamento do Modelo XGBoost.
* `notebook/app.py`: Interface Web Streamlit.
* `notebook/*.pkl`: Objetos pre-treinados do modelo e codificadores de categorias.
* `requirements.txt`: Conjunto de dependencias necessarias para execucao da aplicacao.
* `.gitignore`: Mapeamento de arquivos pesados ou ambientes virtuais para exclusao de versionamento.

## 4. Como Executar na Sua Maquina

### Pre-requisitos
Certifique-se de que o Python esteja instalado. Recomenda-se a utilizacao de um ambiente virtual (venv).

### Passos de Instalacao e Uso
1. Clone este repositorio:
   git clone https://github.com/Gabrielxdev/Demand_Forecasting.git

2. Acesse a pasta do projeto:
   cd Demand_Forecasting

3. Instale as dependencias do projeto:
   pip install -r requirements.txt

4. Inicie o painel preditivo (via Streamlit):
   streamlit run notebook/app.py

A aplicacao ficara disponivel para interacao local no endereco indicado pelo seu terminal `http://localhost:8501`.

## 5. Tecnologias Empregadas
* Python (Linguagem central)
* Scikit-Learn e Pandas (Pre-processamento e Estruturacao do pipelime)
* XGBoost (Modelo preditivo Gradient Boosting)
* Streamlit (Construcao dinamica da Interface de Usuario web)
* Pickle (Exportacao de modelos binarios)
