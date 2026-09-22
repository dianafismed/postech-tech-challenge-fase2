# Tech Challenge — Fase 2 | POSTECH Data Analytics

---

## 1. Identificação

| Campo | Valor |
|---|---|
| Turma | 2DTATBB |
| Grupo | Grupo 15 |
| Data de entrega | <!-- PREENCHER: DD/MM/AAAA --> |

### Integrantes

| Nome completo | RM | E-mail |
|---|---|---|
|Carolina Barboza Segala |RM377840 |carolbarboza85@gmail.com |
|Danilo Augusto Vieira de Andrade |RM377762 |danilo.andrade.393@bb.com.br |
|Diana Avila |RM377835 |dianafismed@yahoo.com.br |
|Lilian Dantas Campos |RM377797 |lilian_ccontabeis@yahoo.com.br |


---

## 2. Links da entrega

Estes três links são **obrigatórios** e devem ser idênticos aos do PDF de submissão.

| Item | Link |
|---|---|
| Repositório | https://github.com/dianafismed/postech-tech-challenge-fase2 |
| Vídeo executivo (≤ 5 min) | <!-- PREENCHER: YouTube não listado / Drive com acesso liberado --> |
| Apresentação | <!-- PREENCHER: link do arquivo em `docs/` ou Drive --> |

> ⚠️ Repositório privado ou inacessível **zera** toda a Dimensão 1 da rúbrica.
> Confira o acesso em uma janela anônima antes de enviar.

---

## 3. O problema

A concessão de crédito é essencial para a operação das instituições financeiras, porém traz consigo o risco constante da inadimplência.

Diante disso, a aplicação do Machine Learning surge como uma solução estratégica para otimizar e automatizar a análise de crédito, permitindo identificar padrões em dados históricos para classificar os solicitantes entre bons e maus pagadores.

Com isso, o objetivo do projeto é desenvolver um modelo preditivo capaz de diminuir o risco da carteira, aumentar a eficiência operacional e acelerar as tomadas de decisão nos processos de avaliação de cartões de crédito.


### Variável alvo

A vaiável alvo é a STATUS.

Foi adotado um critério padrão de risco que identifica como mau pagador um cliente com 60 dias ou mais de atraso, para tratamento inicial e binarização.

0 - Bom Pagador: clientes que apresentam os indicadores 0, 1, C ou X.

1 - Mau Pagador: clientes que apresentam os indicadores 2, 3, 4 ou 5 em seu STATUS, demonstrando inadimplência grave, com atrasos maiores de 60 dias.


### Dataset

| Campo | Valor |
|---|---|
| Fonte | https://drive.google.com/file/d/1z4yEyiCE_CGCWbvAAZQZSz-5-E5T5eYd/view |
| Linhas × colunas | <!-- PREENCHER --> |
| Período / versão | <!-- PREENCHER --> |
| Licença de uso | <!-- PREENCHER --> |

Descrição das variáveis:

| Variável | Tipo | Descrição |
|---|---|---|
| | | |

---

## 4. Como reproduzir

```bash
git clone <URL_DO_REPOSITORIO>
cd <NOME_DO_REPOSITORIO>

python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate

pip install -r requirements.txt
jupyter notebook
```

Baixe o dataset e coloque o arquivo bruto em `data/raw/` (os dados **não** são versionados —
veja `data/README.md`).

Depois execute os notebooks nesta ordem:

| # | Notebook | O que faz |
|---|---|---|
| 1 | `notebooks/01_eda.ipynb` | Análise exploratória |
| 2 | `notebooks/02_preprocessamento.ipynb` | Limpeza, escala e feature engineering |
| 3 | `notebooks/03_modelagem.ipynb` | Treino e comparação dos modelos |
| 4 | `notebooks/04_avaliacao.ipynb` | Métricas, importância de variáveis e conclusões |

**Semente fixa:** `RANDOM_STATE = 42`, declarada na primeira célula de cada notebook.
Rodar os notebooks na ordem acima, a partir de um ambiente limpo, deve reproduzir
exatamente os números da seção 5.

---

## 5. Resultados

| Modelo | Acurácia | Precisão | Recall | F1 | AUC-ROC |
|---|---|---|---|---|---|
| <!-- PREENCHER --> | | | | | |
| | | | | | |

**Modelo escolhido:** <!-- PREENCHER --> — <!-- PREENCHER: por quê. -->

**Métricas priorizadas:** <!-- PREENCHER: justifique a escolha considerando o
     desbalanceamento de classes e o custo de cada tipo de erro no contexto do negócio. -->

---

## 6. Principais conclusões

<!-- PREENCHER: 3 a 5 conclusões em linguagem de negócio.
     Inclua quais variáveis mais influenciam o resultado e o que isso significa
     na prática para quem vai usar o modelo. -->

1.
2.
3.

### Limitações e próximos passos

<!-- PREENCHER -->

---

## 7. Estrutura do repositório

```
.
├── data/          dados brutos (raw) e tratados (processed) — não versionados
├── notebooks/     análise em ordem numerada
└── docs/          apresentação executiva
```

Detalhes e convenções em [`ESTRUTURA.md`](ESTRUTURA.md).
Antes de enviar, percorra o [`CHECKLIST.md`](CHECKLIST.md).

---

## 8. Tecnologias

<!-- PREENCHER: Python 3.11, pandas, scikit-learn, ... -->
