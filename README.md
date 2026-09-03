# Análise de Dados de Energia — SERS

Projeto desenvolvido para a disciplina **Soluções em Energias Renováveis e Sustentáveis**, do curso de **Ciência da Computação**.

O projeto reúne duas etapas de análise de dados realizadas pela equipe:

1. **`CP1_SERS.ipynb`** — primeira etapa da atividade, envolvendo a análise de diferentes datasets do setor energético utilizando Python/Pandas;
2. **`Desafio_Final_Energia_ONS_API_Final.ipynb`** — etapa final, utilizando dados reais obtidos diretamente de uma API pública do Operador Nacional do Sistema Elétrico (ONS).

A atividade tem como objetivo aplicar técnicas de preparação, inspeção, manipulação, filtragem, estatística descritiva e interpretação de dados relacionados ao setor de energia. A orientação da atividade estabelece que os códigos, resultados e interpretações sejam registrados nos próprios notebooks.

---

## 1. CP1_SERS

O arquivo **`CP1_SERS.ipynb`** representa a primeira etapa do projeto e reúne análises realizadas sobre diferentes conjuntos de dados relacionados ao consumo e à geração de energia.

A atividade foi estruturada a partir das orientações fornecidas pelo professor, que propõem inicialmente a preparação e inspeção dos dados no **Orange Data Mining** e, posteriormente, a análise dos dados preparados utilizando **Python e Pandas**.

Entre os procedimentos realizados estão:

* carregamento dos datasets;
* inspeção dos registros;
* identificação e seleção de atributos;
* verificação de valores ausentes;
* criação de amostras;
* renomeação e organização de atributos;
* cálculo de valores máximos, mínimos e médias;
* criação de limiares percentuais;
* filtragem de registros;
* contagem e cálculo de percentuais;
* comparação entre diferentes recortes dos dados;
* interpretação dos resultados.

A proposta da atividade é utilizar os dados para responder a situações relacionadas ao contexto energético analisado, e não apenas executar comandos do Pandas.

### Datasets analisados

O `CP1_SERS.ipynb` contempla seis conjuntos de dados utilizados na atividade:

| # | Dataset                                             | Fonte                           | Tema                                               |
| - | --------------------------------------------------- | ------------------------------- | -------------------------------------------------- |
| 1 | **Appliances Energy Prediction**                    | UCI Machine Learning Repository | Consumo de eletrodomésticos e condições ambientais |
| 2 | **Steel Industry Energy Consumption**               | UCI Machine Learning Repository | Consumo energético industrial                      |
| 3 | **Power Consumption of Tetouan City**               | UCI Machine Learning Repository | Consumo elétrico de três zonas de Tétouan          |
| 4 | **Solar Power Generation Data**                     | Kaggle                          | Geração de energia fotovoltaica                    |
| 5 | **Wind & Solar Energy Production Dataset**          | Kaggle                          | Produção de energia eólica e solar                 |
| 6 | **Individual Household Electric Power Consumption** | UCI Machine Learning Repository | Consumo elétrico residencial                       |

Esses seis datasets representam diferentes contextos do setor energético, incluindo consumo residencial, consumo industrial, distribuição de energia e geração por fontes renováveis.

### Fontes dos dados

#### 1. Appliances Energy Prediction — UCI

Dataset utilizado para analisar o consumo de eletrodomésticos em uma residência e sua relação com variáveis ambientais, principalmente temperatura e umidade.

**Fonte:** UCI Machine Learning Repository
https://archive.ics.uci.edu/dataset/374/appliances+energy+prediction

No notebook, a análise utiliza o consumo de eletrodomésticos, temperaturas e umidades para identificar registros de maior consumo. Entre os procedimentos, foi utilizado um limiar correspondente a **70% do consumo máximo** e, posteriormente, uma condição adicional de temperatura.

#### 2. Steel Industry Energy Consumption — UCI

Dataset utilizado para analisar o consumo energético de uma indústria siderúrgica, considerando variáveis como consumo em kWh, potência reativa, fator de potência, tipo de carga e classificação do dia.

**Fonte:** UCI Machine Learning Repository
https://archive.ics.uci.edu/dataset/851/steel+industry+energy+consumption

A análise busca identificar situações de consumo elevado e verificar sua relação com categorias de carga e valores de fator de potência. A atividade orienta a utilização de um limiar de **75% do consumo máximo** para identificar registros de maior demanda.

#### 3. Power Consumption of Tetouan City — UCI

Dataset utilizado para analisar o consumo elétrico de três zonas de distribuição da cidade de Tétouan, relacionando os valores de consumo a variáveis meteorológicas.

**Fonte:** UCI Machine Learning Repository
https://archive.ics.uci.edu/dataset/849/power+consumption+of+tetouan+city

A análise permite comparar os picos de consumo das três zonas e observar as condições ambientais associadas aos períodos de maior demanda.

#### 4. Solar Power Generation Data — Kaggle

Dataset utilizado para analisar a geração de energia de uma planta fotovoltaica, incluindo informações de potência CC, potência CA, geração diária, geração acumulada e identificação dos inversores.

**Fonte:** Kaggle
https://www.kaggle.com/datasets/anikannal/solar-power-generation-data

A análise considera períodos de alta geração e utiliza a frequência dos identificadores dos inversores para observar quais aparecem com maior frequência nesses períodos. O próprio exercício ressalta que esse recorte não deve ser utilizado, isoladamente, para afirmar desempenho ou falha de um inversor.

#### 5. Wind & Solar Energy Production Dataset — Kaggle

Dataset utilizado para comparar a ocorrência de períodos de alta geração **solar** e **eólica**.

**Fonte:** Kaggle
https://www.kaggle.com/datasets/ahmeduzaki/wind-and-solar-energy-production-dataset

Como as duas fontes apresentam escalas diferentes, cada uma é comparada com seu próprio valor máximo. Dessa forma, o critério utilizado evita favorecer uma das fontes simplesmente por possuir valores absolutos maiores.

#### 6. Individual Household Electric Power Consumption — UCI

Dataset utilizado para analisar o consumo elétrico detalhado de uma residência, incluindo potência ativa, potência reativa, tensão, corrente e submedições.

**Fonte:** UCI Machine Learning Repository
https://archive.ics.uci.edu/dataset/235/individual+household+electric+power+consumption

A análise identifica períodos de demanda elevada utilizando **75% da potência ativa máxima** e posteriormente adiciona a corrente média como segundo critério.

---

# 2. Desafio Final — Análise de Dados de Energia com API

Após a primeira etapa, foi desenvolvido o arquivo:

**`Desafio_Final_Energia_ONS_API_Final.ipynb`**

Esse notebook representa a etapa final da atividade e amplia a análise para dados obtidos diretamente de uma **API pública do Operador Nacional do Sistema Elétrico (ONS)**.

Diferentemente da primeira etapa, em que foram utilizados datasets disponibilizados em repositórios como UCI e Kaggle, nesta fase os dados são consultados diretamente por meio de uma API.

## Fonte dos dados

Os dados utilizados são provenientes do conjunto **Carga Verificada**, disponibilizado pelo ONS.

**Portal de dados do ONS:**
https://dados.ons.org.br/

**Dataset:**
https://dados.ons.org.br/dataset/carga-energia-verificada

**API utilizada no notebook:**
`https://apicarga.ons.org.br/prd/cargaverificada`

A análise foi realizada inicialmente para a área de carga:

**São Paulo — SP**

e para o período:

**01/08/2025 a 07/08/2025**

A API fornece registros relacionados à carga elétrica, incluindo informações de data/hora, área de carga e diferentes medidas de carga.

---

## Objetivos do Desafio Final

O notebook foi desenvolvido para realizar uma análise exploratória da carga elétrica da área de São Paulo.

As principais etapas foram:

1. consulta dos dados diretamente na API;
2. construção de um DataFrame utilizando Pandas;
3. inspeção da estrutura dos dados;
4. identificação dos principais atributos;
5. renomeação das colunas;
6. tratamento e verificação dos dados;
7. análise de valores ausentes;
8. cálculo de indicadores estatísticos;
9. identificação de períodos de alta demanda;
10. criação de diferentes recortes dos dados;
11. cálculo de percentuais;
12. identificação do momento de pico;
13. criação de gráficos;
14. interpretação dos resultados;
15. geração de um relatório técnico;
16. validação crítica das conclusões.

A estrutura proposta pelo professor exige que o notebook contenha a consulta à API, DataFrame, organização dos dados, indicadores, recortes, gráficos, interpretações, síntese dos resultados e relatório final.

---

## Principais atributos utilizados

Após a consulta à API, os atributos relacionados à análise foram organizados no DataFrame.

Entre eles estão:

* `Area_Carga` — código da área de carga;
* `Data_Referencia` — data de referência da medição;
* `Data_Hora_UTC` — data e hora da medição em UTC;
* `Carga_Global` — valor da carga global;
* `Carga_Global_Consistente` — carga global com consistência aplicada;
* `Carga_Global_SMMGD` — carga global considerando SMMGD;
* `Carga_Supervisionada` — carga supervisionada;
* `Carga_Nao_Supervisionada` — carga não supervisionada;
* `Carga_MMGD` — carga referente à medição de micro e minigeração distribuída.

Também foram verificadas as características dos dados e os tipos das variáveis antes da realização das análises.

---

## Indicadores analisados

Foram calculados os principais indicadores estatísticos da carga elétrica:

* carga mínima;
* carga máxima;
* carga média;
* mediana;
* amplitude entre o maior e o menor valor;
* quantidade total de medições.

Esses indicadores foram utilizados para compreender a distribuição da carga durante o período analisado.

---

## Identificação de alta demanda

Para identificar períodos próximos ao pico de consumo, foi definido como critério de **alta demanda**:

> registros com carga superior a **90% da carga máxima**.

A partir desse critério foram calculados:

* limiar de alta demanda;
* quantidade de registros acima do limiar;
* percentual em relação ao total;
* maior valor registrado;
* data e horário do pico, quando disponíveis.

---

## Segundo critério de análise

Além do critério de alta demanda, foi utilizado um segundo recorte considerando:

> **carga acima da média observada no período.**

Esse segundo conjunto foi comparado ao conjunto de alta demanda para verificar como a alteração do critério modifica a quantidade de registros selecionados.

---

## Visualizações

O notebook também apresenta visualizações para facilitar a interpretação dos dados.

Entre elas estão:

* gráfico do comportamento da **Carga Global ao longo do tempo**;
* histograma da distribuição da **Carga Global**, acompanhado de indicadores como média, mediana, máximo e limiar de alta demanda.

As visualizações permitem observar as oscilações da carga ao longo do período e a frequência dos diferentes níveis de demanda.

---

## Resultados principais

Para o período de **01/08/2025 a 07/08/2025**, foram analisadas:

* **336 medições**;
* **Carga mínima:** 12.139,253 MW;
* **Carga máxima:** 23.185,312 MW;
* **Carga média:** 17.870,829 MW;
* **Mediana:** 18.199,128 MW;
* **Amplitude:** 11.046,059 MW.

Considerando o critério de alta demanda, definido como valores superiores a 90% da carga máxima:

* **Limiar:** 20.866,781 MW;
* **50 registros** classificados como alta demanda;
* **14,88%** das medições.

Considerando o segundo critério, carga acima da média:

* **184 registros**;
* **54,76%** do total analisado.

Esses valores são utilizados no notebook como base para as interpretações e para o relatório técnico final.

---

# 3. Tecnologias utilizadas

O projeto utiliza principalmente:

* **Python**
* **Pandas**
* **Matplotlib**
* **Jupyter Notebook / Google Colab**
* **Orange Data Mining**
* **API pública do ONS**

A primeira etapa utiliza o Orange Data Mining como ferramenta de preparação e exploração inicial, seguida da manipulação dos dados com Python/Pandas. A atividade orienta justamente essa divisão entre preparação dos dados e análise programática.

---

# 4. Estrutura do projeto

```text
.
├── CP1_SERS.ipynb
├── Desafio_Final_Energia_ONS_API_Final.ipynb
└── README.md
```

### `CP1_SERS.ipynb`

Notebook correspondente à primeira etapa da atividade, contendo análises de datasets provenientes principalmente do **UCI Machine Learning Repository** e **Kaggle**.

### `Desafio_Final_Energia_ONS_API_Final.ipynb`

Notebook correspondente ao desafio final, utilizando dados de carga elétrica obtidos diretamente da **API pública do ONS**.

### `README.md`

Este documento, contendo a descrição do projeto, metodologia e fontes dos dados utilizados.

---

# 5. Metodologia

De forma geral, o projeto segue o seguinte fluxo:

```text
Fontes de Dados
      │
      ▼
Preparação e Inspeção
      │
      ▼
Python / Pandas
      │
      ▼
Limpeza e Organização
      │
      ▼
Indicadores Estatísticos
      │
      ▼
Filtros e Recortes
      │
      ▼
Visualizações
      │
      ▼
Interpretação
      │
      ▼
Relatório Técnico
```

A metodologia busca transformar os dados brutos em informações que permitam compreender diferentes comportamentos relacionados ao consumo e à geração de energia.

---

# 6. Considerações finais

O projeto permitiu aplicar, de forma prática, conceitos de análise e manipulação de dados em diferentes contextos do setor energético.

Na primeira etapa, foram trabalhados datasets de consumo residencial, consumo industrial, distribuição de energia e geração de fontes renováveis. Já no desafio final, a análise foi realizada utilizando dados de carga elétrica obtidos diretamente de uma API pública do ONS.

A evolução entre as duas etapas permitiu passar de datasets previamente disponibilizados para uma fonte de dados acessada por API, mantendo como base os mesmos princípios de análise: **inspecionar, organizar, calcular, filtrar, visualizar e interpretar os dados**.

As conclusões apresentadas no projeto devem ser entendidas dentro dos períodos, amostras e critérios utilizados em cada análise, evitando generalizações que não possam ser sustentadas pelos dados.

---

# 7. Referências e fontes dos dados

### UCI Machine Learning Repository

* Appliances Energy Prediction
  https://archive.ics.uci.edu/dataset/374/appliances+energy+prediction

* Steel Industry Energy Consumption
  https://archive.ics.uci.edu/dataset/851/steel+industry+energy+consumption

* Power Consumption of Tetouan City
  https://archive.ics.uci.edu/dataset/849/power+consumption+of+tetouan+city

* Individual Household Electric Power Consumption
  https://archive.ics.uci.edu/dataset/235/individual+household+electric+power+consumption

### Kaggle

* Solar Power Generation Data
  https://www.kaggle.com/datasets/anikannal/solar-power-generation-data

* Wind & Solar Energy Production Dataset
  https://www.kaggle.com/datasets/ahmeduzaki/wind-and-solar-energy-production-dataset

### Operador Nacional do Sistema Elétrico — ONS

* Portal de Dados do ONS
  https://dados.ons.org.br/

* Carga de Energia Verificada
  https://dados.ons.org.br/dataset/carga-energia-verificada

* API de Carga Verificada
  https://apicarga.ons.org.br/prd/cargaverificada

---

## 8. Arquivos da entrega

| Arquivo                                     | Descrição                                   |
| ------------------------------------------- | ------------------------------------------- |
| `CP1_SERS.ipynb`                            | Análise dos datasets da primeira etapa      |
| `Desafio_Final_Energia_ONS_API_Final.ipynb` | Análise final utilizando API pública do ONS |
| `README.md`                                 | Documentação do projeto e fontes dos dados  |

---

**Disciplina:** Soluções em Energias Renováveis e Sustentáveis
**Curso:** Ciência da Computação
