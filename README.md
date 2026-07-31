| ![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg) ![FastAPI](https://img.shields.io/badge/framework-FastAPI-009688?logo=fastapi) ![MLflow](https://img.shields.io/badge/MLOps-MLflow-0194E2?logo=mlflow) ![Thompson Sampling](https://img.shields.io/badge/Algorithm-Thompson%20Sampling-blue.svg) ![Scikit-learn](https://img.shields.io/badge/ML-Scikit--learn-F7931E?logo=scikit-learn) ![MIT License](https://img.shields.io/badge/license-MIT-yellow.svg) |
|:----------------------------------------------------------------------------------------------------------------------------------------:|

# 🎯 Datathon — Plataforma de Experimentação Adaptativa para Ofertas Financeiras

## 📌 Descrição

Este projeto faz parte do **Tech Challenge – Fase 5** da Pós-Tech em Machine Learning Engineering, cujo objetivo é aplicar conhecimentos avançados em **Machine Learning Engineering** e **Inteligência Artificial**, desenvolvendo uma solução completa end-to-end para personalização adaptativa de ofertas em canais digitais.

O desafio consiste em criar uma **plataforma de experimentação adaptativa** que utiliza algoritmos de **Multi-Armed Bandit** (Thompson Sampling) para recomendar ofertas, mensagens ou próximos passos para clientes em tempo real, otimizando taxas de conversão e aprendendo continuamente com as respostas observadas.

A solução integra:
- 📊 **Análise Exploratória** de dados bancários de marketing
- 🧠 **Thompson Sampling** (Bayesian bandit) para exploração otimizada
- 🔄 **Baseline Determinístico** para comparação de performance
- ⚡ **API FastAPI** para inferência em tempo real
- 📈 **MLflow** para rastreamento de experimentos
- 🎬 **Pipeline completa** de ML Engineering (EDA → Modelo → API → Cloud)

---

## 🎯 Objetivos do Projeto

✅ Entender o problema de decisão adaptativa em contexto financeiro  
✅ Coletar e preparar dados de marketing bancário (sem vazamento temporal)  
✅ Implementar modelo baseline determinístico para comparação  
✅ Implementar algoritmo Thompson Sampling com exploração bayesiana  
✅ Demonstrar que o modelo adaptativo supera o baseline  
✅ Criar Golden Set com 5 clientes representativos validados  
✅ Disponibilizar API REST para recomendações em tempo real  
✅ Rastrear experimentos com MLflow (versionamento de ML)  
✅ Documentar arquitetura em nuvem (AWS, Azure, GCP)  
✅ Gravar vídeo pitch (5 min) demonstrando a solução  

---

## 🏗️ Arquitetura Geral

O fluxo completo do projeto segue uma pipeline de Machine Learning end-to-end:

```
┌─────────────────────────────────────────────────────────────┐
│  1. Dados Kaggle (Marketing Bancário)                        │
│     └─ Base Kaggle: bank-marketing ou similar                │
└──────────────────┬──────────────────────────────────────────┘
                   │ Download
                   ↓
┌─────────────────────────────────────────────────────────────┐
│  2. Exploração de Dados (EDA)                                │
│     ├─ Análise estatística                                   │
│     ├─ Missings e outliers                                   │
│     └─ Visualizações                                         │
└──────────────────┬──────────────────────────────────────────┘
                   │ Compreensão dos dados
                   ↓
┌─────────────────────────────────────────────────────────────┐
│  3. Preparação de Dados                                      │
│     ├─ Remoção de vazamento temporal                         │
│     ├─ Tratamento de missings                                │
│     ├─ Normalização/Padronização                             │
│     └─ Split treino/teste                                    │
└──────────────────┬──────────────────────────────────────────┘
                   │ Dados limpos
                   ↓
┌────────────────────────────────────────────────────────────┐
│  4. Baseline + Thompson Sampling                             │
│     ├─ Baseline: Oferece sempre melhor braço histórico      │
│     ├─ Adaptativo: Thompson Sampling (Bayesian)             │
│     ├─ Simulação: 1000 rounds                                │
│     └─ Gráficos: Convergência, exploração, regret           │
└──────────────────┬──────────────────────────────────────────┘
                   │ Modelos treinados
                   ↓
┌─────────────────────────────────────────────────────────────┐
│  5. Avaliação + Golden Set                                   │
│     ├─ Validação com 5 clientes reais                        │
│     ├─ Análise de coerência das recomendações                │
│     └─ Documentação de resultados                            │
└──────────────────┬──────────────────────────────────────────┘
                   │ Modelo validado
                   ↓
┌─────────────────────────────────────────────────────────────┐
│  6. Serviço Demonstrável (API FastAPI)                       │
│     ├─ POST /recommend → Oferta para cliente                │
│     ├─ GET /arms-stats → Estatísticas de cada braço          │
│     └─ GET /health → Status da API                           │
└──────────────────┬──────────────────────────────────────────┘
                   │ Modelo em produção
                   ↓
┌─────────────────────────────────────────────────────────────┐
│  7. MLOps (MLflow Tracking)                                  │
│     ├─ Log de parâmetros (alpha, beta, n_arms)               │
│     ├─ Log de métricas (conversão, regret)                   │
│     ├─ Artefatos (modelo, scaler)                            │
│     └─ Dashboard de experimentos                             │
└──────────────────┬──────────────────────────────────────────┘
                   │ Experimentos versionados
                   ↓
┌─────────────────────────────────────────────────────────────┐
│  8. Arquitetura em Nuvem (AWS/Azure/GCP)                     │
│     ├─ S3/Blob: Armazenamento de dados                       │
│     ├─ Lambda/Functions: Processamento                       │
│     ├─ SageMaker/ML: Modelo em produção                       │
│     ├─ API Gateway: Endpoints HTTP                           │
│     └─ CloudWatch: Monitoramento                             │
└──────────────────┬──────────────────────────────────────────┘
                   │ Infraestrutura definida
                   ↓
┌─────────────────────────────────────────────────────────────┐
│  9. Demo Day (Vídeo Pitch 5 min)                             │
│     ├─ Problema de negócio explicado                         │
│     ├─ Solução proposta e algoritmos                         │
│     ├─ Demo ao vivo (API rodando)                            │
│     └─ Resultados e conclusões                               │
└─────────────────────────────────────────────────────────────┘
```

---

## 📊 Problema de Negócio

### Contexto
Uma instituição financeira digital precisa decidir qual **oferta, mensagem ou próximo passo** apresentar para cada cliente em diferentes canais.

### Desafios Atuais
- ❌ **Regras fixas** desperdiçam tráfego (nem sempre a melhor oferta é a mesma)
- ❌ **Testes A/B longos** demoram para reagir a mudanças de contexto
- ❌ **Mudanças de contexto** prejudicam a personalização (clientes mudam comportamento)
- ❌ **Decisões estáticas** não aprendem com o tempo (sem feedback loop)

### Solução Proposta: Plataforma Adaptativa
✅ Algoritmo que **aprende continuamente** qual oferta cada cliente prefere  
✅ **Equilibra exploração** (testar novas ofertas) e **explotação** (usar conhecimento)  
✅ Personaliza ofertas **em tempo real** sem congelar em regras estáticas  
✅ Melhora **taxa de conversão** vs. abordagens determinísticas  

---

## 🧠 Algoritmo: Thompson Sampling

### O que é?
**Thompson Sampling** é um algoritmo bayesiano de bandit adaptativo que:
1. Modela cada oferta como uma distribuição de probabilidade (Beta)
2. A cada interação, faz sample da distribuição de cada oferta
3. Escolhe a oferta com maior probabilidade amostrada (exploração automática)
4. Atualiza a distribuição com a resposta observada (aprendizado)

### Priors
- **α (alpha)**: Sucessos prévios iniciais (ex: 1)
- **β (beta)**: Fracassos prévios iniciais (ex: 1)
- Distribuição: Beta(α, β)

### Convergência
- Conforme mais dados chegam, a distribuição converge para a taxa real
- Exploração decresce naturalmente → Explotação aumenta
- **Não precisa de hiperparâmetro de exploração** (ao contrário de ε-Greedy)

### Comparação com Baseline
| Aspecto | Baseline (Greedy) | Thompson Sampling |
|---------|-------------------|-------------------|
| Exploração | Nenhuma (0%) | Contínua (bayesiana) |
| Convergência | Rápida mas míope | Ótima (ótimo para regret) |
| Adaptação | Nenhuma | Contínua com dados novos |
| Taxa Conversão | XX% (melhor histórico) | XX+% (aprendendo) |

---

## 📁 Estrutura do Projeto

```
mle_tech_chalenge_5/
│
├── 📋 README.md                        # Este arquivo
├── 📊 PLANO_EXECUCAO.md                # Roadmap das 9 fases
├── 📦 requirements.txt                 # Dependências Python
├── .gitignore                          # Exclusões Git
├── .env.example                        # Template de variáveis
│
├── 📂 data/
│   ├── raw/                            # Dados brutos (Kaggle)
│   └── processed/                      # Dados após EDA
│
├── 📂 notebooks/
│   ├── 01_EDA.ipynb                   # Análise Exploratória
│   └── 02_Baseline_e_Adaptativo.ipynb # Modelos e Comparação
│
├── 📂 src/
│   ├── __init__.py
│   ├── baseline.py                     # Modelo Baseline
│   ├── adaptive_model.py               # Thompson Sampling
│   ├── data_processing.py              # Funções de EDA
│   ├── train_and_log.py               # Treinamento + MLflow
│   ├── inference.py                    # Script de inferência
│   └── api.py                          # API FastAPI
│
├── 📂 models/
│   ├── model.pkl                       # Modelo serializado
│   └── scaler.pkl                      # StandardScaler
│
├── 📂 config/
│   └── config.yaml                     # Configurações
│
├── 📂 mlruns/                          # MLflow tracking (auto)
│   └── experiments/
│
└── 📂 doc/
    ├── datathon.md                     # Briefing completo do desafio
    ├── FASES_DETALHADAS.md             # Estruturação com componentes
    ├── golden_set_results.csv          # Resultados Golden Set
    └── POSTECH - MLET - DATATHON.pdf   # PDF do desafio
```

---

## 🚀 Como Executar

### Pré-requisitos
- Python 3.8+
- pip ou conda
- Git

### 1️⃣ Setup do Ambiente

```bash
# Clonar repositório
git clone https://github.com/seu-usuario/datathon-7mlet-grupo-XX.git
cd datathon-7mlet-grupo-XX

# Criar ambiente virtual
python -m venv venv

# Ativar ambiente
source venv/bin/activate  # macOS/Linux
# ou
venv\Scripts\activate     # Windows

# Instalar dependências
pip install -r requirements.txt

# Copiar variáveis de ambiente
cp .env.example .env
```

### 2️⃣ Preparar Dados

```bash
# Abrir notebook de EDA
jupyter notebook notebooks/01_EDA.ipynb

# Ou executar direto (se implementado script)
python src/data_processing.py
```

### 3️⃣ Treinar Modelos

```bash
# Executar notebook com baseline + Thompson
jupyter notebook notebooks/02_Baseline_e_Adaptativo.ipynb

# Ou executar treinamento com MLflow
python src/train_and_log.py

# Visualizar experimentos no MLflow
mlflow ui --host 0.0.0.0 --port 5000
# Abra: http://localhost:5000
```

### 4️⃣ Usar o Modelo (API)

#### Opção A: API FastAPI
```bash
# Iniciar servidor
uvicorn src.api:app --reload --host 0.0.0.0 --port 8000

# Em outro terminal, testar
curl -X POST "http://localhost:8000/recommend" \
  -H "Content-Type: application/json" \
  -d '{
    "age": 35,
    "income": 5000,
    "previous_conversions": 2,
    "days_since_contact": 10
  }'

# Acessar documentação interativa
# Swagger: http://localhost:8000/docs
# ReDoc: http://localhost:8000/redoc
```

#### Opção B: Script Python
```bash
python src/inference.py
```

---

## 🛠️ Tecnologias Utilizadas

| Componente | Tecnologia | Versão | Uso |
|------------|------------|---------|-----|
| **Linguagem** | Python | 3.8+ | Desenvolvimento |
| **Data Processing** | Pandas + NumPy | 2.0+, 1.24+ | Manipulação de dados |
| **ML** | Scikit-learn | 1.3+ | Baseline, Métricas |
| **Algoritmo** | NumPy + SciPy | 1.24+, 1.11+ | Thompson Sampling |
| **Visualização** | Matplotlib + Seaborn | 3.7+, 0.12+ | Gráficos |
| **Notebooks** | Jupyter | 1.0+ | Desenvolvimento |
| **MLOps** | MLflow | 2.8+ | Rastreamento de experimentos |
| **API** | FastAPI | 0.104+ | Servidor REST |
| **ASGI Server** | Uvicorn | 0.24+ | Execução da API |
| **Config** | Python-dotenv + PyYAML | 1.0+, 6.0+ | Configurações |
| **Testing** | Pytest | 7.4+ | Testes (opcional) |

---

## 📊 Base de Dados

### Kaggle Dataset
O projeto utiliza base de marketing bancário do Kaggle, como:
- **bank-marketing** (henriqueyamahata)
- **bank-marketing-data-set** (tunguz)
- **bank-term-deposit-subscription** (dharmik34)
- **telemarketing-jyb-dataset** (aguado)

**Características:**
- Dados de campanhas bancárias
- Target: conversão/clique (resposta do cliente)
- Features: idade, renda, histórico de contatos, etc.
- Período: Múltiplos anos de dados históricos

### Preparação
- ✅ Remoção de colunas com vazamento temporal
- ✅ Tratamento de valores faltantes
- ✅ Normalização/padronização de features
- ✅ Split sem embaralhamento (dados são processados sequencialmente)

---

## 📈 Resultados Esperados

Após completar o projeto, você terá:

✅ **Dataset processado** sem vazamento temporal  
✅ **Baseline determinístico** com taxa de conversão baseline (ex: 30%)  
✅ **Modelo Thompson Sampling** superando baseline (ex: 35%+)  
✅ **Gráficos** de convergência, exploração e análise de regret  
✅ **Golden Set** com 5 clientes validados manualmente  
✅ **API REST** fornecendo recomendações em tempo real  
✅ **MLflow tracking** com parâmetros e métricas versionados  
✅ **Arquitetura cloud** documentada (AWS/Azure/GCP)  
✅ **Vídeo pitch** (5 min) demonstrando a solução  

---

## 🎓 Fases do Projeto

Este projeto é estruturado em **9 fases**:

| # | Fase | Objetivo | Status |
|---|------|----------|--------|
| 0 | Organização | Setup, estrutura, dependências | ✅ |
| 1 | EDA | Exploração e preparação de dados | ⏳ |
| 2 | Baseline + ML | Implementar e comparar modelos | ⏳ |
| 3 | Avaliação | Golden Set com 5 clientes | ⏳ |
| 4 | Serviço | API FastAPI funcionando | ⏳ |
| 5 | MLOps | Rastreamento com MLflow | ⏳ |
| 6 | Cloud | Arquitetura em nuvem | ⏳ |
| 7 | Docs | Documentação completa | ⏳ |
| 8 | Demo | Vídeo pitch (5 min) | ⏳ |

Para detalhes de cada fase, veja **[PLANO_EXECUCAO.md](./PLANO_EXECUCAO.md)**.

---

## 📚 Documentação

- **[PLANO_EXECUCAO.md](./PLANO_EXECUCAO.md)** — Roadmap completo com 9 fases, timeline e checklist
- **[doc/FASES_DETALHADAS.md](./doc/FASES_DETALHADAS.md)** — Estruturação de cada fase com tarefas específicas e componentes
- **[doc/datathon.md](./doc/datathon.md)** — Briefing oficial do desafio Datathon
- **[Swagger API](http://localhost:8000/docs)** — Documentação interativa (quando API rodando)

---

## 📞 Suporte

Para dúvidas sobre o desafio, consulte:
- **Briefing**: [doc/datathon.md](./doc/datathon.md)
- **Roadmap**: [PLANO_EXECUCAO.md](./PLANO_EXECUCAO.md)
- **Fases Detalhadas**: [doc/FASES_DETALHADAS.md](./doc/FASES_DETALHADAS.md)

---

**Status**: Fase 0 - Organização ✅  
**Última atualização**: 2026-07-30  
**Próximas etapas**: Fase 1 (EDA) ⏳