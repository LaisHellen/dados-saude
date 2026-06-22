# Dados-Saúde

Repositório dedicado a estudos e projetos de análise de dados em saúde pública, reunindo iniciativas de extração, tratamento, visualização e interpretação de dados para geração de evidências, apoio à tomada de decisão e comunicação da informação.

---

# Estudo de Caso: Transição do perfil de mortalidade por doenças crônicas entre mulheres negras e brancas no Estado de São Paulo (2000–2020)

## Objetivo

Como parte de um exercício de análise de dados em saúde pública, este estudo buscou compreender como o perfil de mortalidade por Doenças Crônicas Não Transmissíveis (DCNTs) entre mulheres negras e brancas mudou entre os anos de 2000 e 2020 no Estado de São Paulo.

O objetivo foi identificar padrões que possam subsidiar discussões sobre monitoramento epidemiológico, desigualdades em saúde e planejamento de ações públicas.

---

## Fonte dos Dados

* Sistema de Informações sobre Mortalidade (SIM/DATASUS)
* Extração realizada via biblioteca PySUS
* Períodos analisados:
  * 2000
  * 2020
* Unidade geográfica:
  * Estado de São Paulo

---

## Metodologia

O pipeline foi desenvolvido em Python utilizando Google Colab.

As etapas executadas foram:

### 1. Extração dos dados

Utilização da biblioteca PySUS para leitura dos dados do SIM referentes aos anos de 2000 e 2020.

### 2. Seleção das variáveis

Foram utilizadas as seguintes variáveis:

| Variável | Descrição                      |
| -------- | ------------------------------ |
| ANO      | Ano do óbito                   |
| SEXO     | Sexo da pessoa falecida        |
| RACACOR  | Raça/Cor                       |
| CAUSABAS | Causa básica do óbito (CID-10) |

### 3. Tratamento dos dados

* Filtragem apenas para registros femininos;
* Padronização da variável raça/cor;
* Agrupamento das categorias "Preta" e "Parda" na categoria analítica "Negra";
* Remoção de registros sem informação válida para as variáveis utilizadas.

### 4. Classificação das causas de morte

Os códigos CID-10 presentes na variável CAUSABAS foram agrupados em quatro categorias de doenças crônicas:

| Código CID-10 | Categoria                      |
| ------------- | ------------------------------ |
| C             | Neoplasias (Câncer)            |
| E             | Doenças Metabólicas            |
| I             | Doenças Cardiovasculares       |
| J             | Doenças Respiratórias Crônicas |

### 5. Análise

Foram calculadas:

* Frequências absolutas;
* Frequências proporcionais;
* Diferenças percentuais entre grupos raciais;
* Variação das causas de morte entre 2000 e 2020.

---

# Dicionário de Dados

## SEXO

| Código | Descrição |
| ------ | --------- |
| 1      | Masculino |
| 2      | Feminino  |

---

## RACACOR

| Código Original | Descrição |
| --------------- | --------- |
| 1               | Branca    |
| 2               | Preta     |
| 4               | Parda     |

### Agrupamento Utilizado

| Categoria Analítica | Composição    |
| ------------------- | ------------- |
| Branca              | Branca        |
| Negra               | Preta + Parda |

---

## CAUSABAS

Representa a causa básica do óbito registrada segundo a Classificação Internacional de Doenças (CID-10).

### Agrupamento Analítico Utilizado

| Prefixo CID-10 | Grupo Analítico                |
| -------------- | ------------------------------ |
| C              | Neoplasias (Câncer)            |
| E              | Doenças Metabólicas            |
| I              | Doenças Cardiovasculares       |
| J              | Doenças Respiratórias Crônicas |

---

# Principais Resultados

## 1. Mudança na participação dos grupos raciais

Embora as mulheres brancas representem a maior parte dos registros analisados, observou-se aumento da participação proporcional de mulheres negras entre os óbitos por doenças crônicas entre 2000 e 2020.

---

## 2. Diferenças no perfil de mortalidade

As doenças cardiovasculares permaneceram como principal causa de morte nos dois grupos raciais.

Entretanto, observam-se diferenças na distribuição proporcional das causas de morte entre mulheres negras e brancas, evidenciando a importância de análises com recorte racial.

---

## 3. Transição epidemiológica

Entre 2000 e 2020 foi observada:

* Redução da participação relativa das doenças cardiovasculares;
* Aumento da participação das neoplasias;
* Aumento da participação das doenças respiratórias crônicas.

Essas mudanças sugerem transformações no perfil epidemiológico da população feminina ao longo das duas décadas analisadas.

---

# Tecnologias Utilizadas

* Python
* PySUS
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Google Colab
* GitHub

---

# Estrutura do Repositório

```text
dados-saude/

├── notebooks/
│   └── mortalidade_mulheres_sp.ipynb
└── README.md
```

---

# Conclusão

A análise demonstrou que as doenças crônicas permanecem como importante causa de mortalidade entre mulheres no Estado de São Paulo. Além disso, foram identificadas diferenças na distribuição das causas de morte entre mulheres negras e brancas e mudanças relevantes no perfil epidemiológico entre 2000 e 2020.

O estudo evidencia o potencial do uso de bases secundárias do SUS para geração de evidências e apoio ao planejamento de políticas públicas voltadas à redução das desigualdades em saúde.

---

## Como reproduzir o projeto

1. Clone este repositório.
2. Abra o notebook disponível na pasta `notebooks`.
3. Instale as dependências necessárias.
4. Execute as etapas de extração, tratamento e análise dos dados.
5. Gere novamente as visualizações e indicadores apresentados neste estudo.

```bash
pip install pysus pandas matplotlib seaborn
```
