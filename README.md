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
| Vídeo executivo (≤ 5 min) | https://youtu.be/_SMwM_3C4Nc |
| Apresentação | https://drive.google.com/file/d/15ZaXckwTZQANMAzVcml9WInw-xZAozuE/view?usp=drive_link |

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
| 3 | `notebooks/03_modelagem.ipynb` | Treino, comparação dos modelos, métricas e conclusões |

**Semente fixa:** `RANDOM_STATE = 42`, declarada na primeira célula de cada notebook.
Rodar os notebooks na ordem acima, a partir de um ambiente limpo, deve reproduzir
exatamente os números da seção 5.

---

## 5. Resultados

| Modelo | Acurácia | Precisão | Recall | F1 |
|---|---|---|---|---|
| Regressão Logística | 0.10     | 0.62     | 0.47   | 0.06      |
| SVM                 | 0.09     | 0.70     | 0.32   | 0.05      |
| XGBoost             | 0.12     | 0.90     | 0.15   | 0.10      |
| KNN                 | 0.06     | 0.84     | 0.11   | 0.04      |
| Floresta Aleatória  | 0.06     | 0.93     | 0.06   | 0.08      |
| Árvore de Decisão   | 0.06     | 0.90     | 0.08   | 0.05      |

<br>


**Modelo escolhido:**

Regressão Logística, pois apresentou maior *RECALL*.
<br>
<br>

**Métricas priorizadas:** 

Como o objetivo da anállise é evitar perdas, a métrica priorizada foi o ***Recall***, pois ele mede a capacidade do modelo de encontrar todos os exemplos reais da classe positiva, ou seja, os maus pagadores. Neste momento, o custo de tomar um calote ($FN$) é superior ao custo de recusar um bom cliente ($FP$).

---

## 6. Principais conclusões

<!-- PREENCHER: 3 a 5 conclusões em linguagem de negócio.
     Inclua quais variáveis mais influenciam o resultado e o que isso significa
     na prática para quem vai usar o modelo. -->

**1. A Solução Simplificada Mantém Alta Assertividade com Menor Custo Operacional**

          A escolha do modelo de regressão entregou um equilíbrio ideal entre capacidade preditiva (identificação eficaz de maus pagadores) e simplicidade matemática.
     
          Na prática, a instituição financeira ganha em velocidade de resposta no momento do cadastro do cliente e reduz custos de infraestrutura em nuvem, mantendo a assertividade necessária para preservar a saúde da carteira de crédito. 
<br>
<br>

**2. Total Transparência e Facilidade de Explicabilidade para os Analistas e Reguladores**

          Por se tratar de uma estrutura linear/logística, cada decisão do modelo pode ser decomposta no impacto exato de cada variável do cliente.
     
          Isto facilita o trabalho da equipe de atendimento e mesa de crédito ao justificar recusas de forma clara e transparente para os clientes, garantindo 100% de conformidade com as exigências de auditoria e regulação do setor bancário (como LGPD e diretrizes do Banco Central).

<br>
<br>

**3. Flexibilidade para Ajustar a Política de Aprovação conforme a Meta Comercial**

          A saída do modelo em formato de probabilidade contínua ($0\%$ a $100\%$) permite calibrar os pontos de corte (thresholds) de aprovação.
          
          Isto permite que a gestão de risco altere a política de crédito conforme o momento do mercado — adotando uma postura mais conservadora (restringindo aprovações em momentos de crise) ou mais expansionista (flexibilizando aprovações para crescimento da carteira) sem a necessidade de re-treinar o modelo.

<br>
<br>

### Limitações e próximos passos

**Problemas encontrados**

- Há forte desbalanceamento de classes, o que prejudica uma análise com maior poder de predição.

**Possíveis melhoras**

- Ajustar o Limiar de Decisão (Threshold Tuning) em vez de usar $0.50$

Para bases com ~4,5% de positivos, o limiar ideal de decisão da Regressão Logística costuma ficar entre $0.05$ e $0.20$.

- Encontrar uma base melhor

- Verificar se há outras métricas que podem complementar as já experimentadas.



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

requirements.txt
