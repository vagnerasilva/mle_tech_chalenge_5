# 🎯 Datathon - Plataforma de Experimentação Adaptativa

> **MLe Tech Challenge 5**: Construindo uma solução end-to-end de Machine Learning Engineering para recomendação adaptativa de ofertas em canais digitais.

---

## 📌 Problema de Negócio

Uma instituição financeira digital precisa decidir, em diferentes canais, qual **oferta, mensagem ou próximo passo** apresentar para cada cliente elegível.

### Desafios Atuais
- ❌ Regras fixas desperdiçam tráfego de clientes
- ❌ Testes A/B longos demoram para reagir
- ❌ Mudanças de contexto prejudicam a personalização
- ❌ Decisões estáticas não aprendem com o tempo

### Solução Proposta
✅ **Plataforma adaptativa** que:
- Identifica comportamentos distintos de clientes
- Equilibra exploração (descobrir) e explotação (usar conhecimento)
- Aprende com respostas observadas em tempo real
- Personaliza ofertas de forma responsável

---

## 🛠️ Tecnologias & Algoritmos

### Stack Técnico
- **Linguagem**: Python 3.8+
- **Data Processing**: Pandas, NumPy, Scikit-learn
- **ML Tracking**: MLflow
- **API**: FastAPI + Uvicorn

### Algoritmo Principal
- **[Thompson Sampling](https://en.wikipedia.org/wiki/Thompson_sampling)** (ou Epsilon-Greedy/UCB)
  - Exploração bayesiana sob incerteza
  - Modela conversão/recompensa esperada por oferta
  - Documentação de priors e estratégia de exploração

---

## 📊 Base de Dados

### Kaggle Dataset
- **Nome**: [Adicione o nome da base escolhida]
- **Link**: [Adicione o link Kaggle]
- **Descrição**: [Descrição breve do dataset]

### Tratamento de Dados
- ✅ Remoção de colunas com vazamento temporal
- ✅ Tratamento de valores faltantes
- ✅ Normalização/padronização de features

---

## 🚀 Como Executar

### 1. Setup do Ambiente

```bash
# Clonar repositório
git clone https://github.com/seu-usuario/datathon-7mlet-grupo-XX.git
cd datathon-7mlet-grupo-XX

# Criar ambiente virtual
python -m venv venv
source venv/bin/activate  # Linux/Mac

# Instalar dependências
pip install -r requirements.txt

# Copiar variáveis de ambiente
cp .env.example .env
```

### 2. Preparar Dados

```bash
# Executar notebook de EDA
jupyter notebook notebooks/01_EDA.ipynb
```

### 3. Treinar Modelo

```bash
# Executar treinamento com MLflow
python src/train_and_log.py

# Visualizar experimentos
mlflow ui --host 0.0.0.0 --port 5000
```

### 4. Usar o Modelo

#### API FastAPI
```bash
# Iniciar servidor
uvicorn src.api:app --reload --host 0.0.0.0 --port 8000

# Acessar documentação interativa
# http://localhost:8000/docs
```

---

## 📈 Resultados

| Métrica | Baseline | Adaptativo | Melhoria |
|---------|----------|-----------|----------|
| Taxa de Conversão | XX% | XX% | ↑ XX% |
| Regret (Cumulativo) | XXX | XXX | ↓ XX% |

---

## 🧪 Golden Set (Testes)

Validação com 5 clientes representativos:

| Cliente | Recomendação | Sentido? |
|---------|--------------|----------|
| 1 | Premium | ✅ Sim |
| 2 | Standard | ✅ Sim |
| 3 | Premium | ✅ Sim |
| 4 | Basic | ✅ Sim |
| 5 | Premium | ✅ Sim |

---

## ☁️ Arquitetura em Nuvem

[Adicione descrição de arquitetura AWS/Azure/GCP aqui]

---

## 📁 Estrutura do Projeto

```
datathon-7mlet-grupo-XX/
├── PLANO_EXECUCAO.md           # Roadmap detalhado
├── README.md                    # Este arquivo
├── requirements.txt
├── .env.example
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│   ├── 01_EDA.ipynb
│   └── 02_Baseline_e_Adaptativo.ipynb
│
├── src/
│   ├── api.py
│   ├── inference.py
│   └── adaptive_model.py
│
├── models/
└── config/
```

---

## 📚 Documentação Completa

Veja [**PLANO_EXECUCAO.md**](./PLANO_EXECUCAO.md) para as 9 fases de desenvolvimento.

Veja [**doc/datathon.md**](./doc/datathon.md) para o briefing completo do desafio.

---

**Status**: Fase 1 - Organização ⏳  
**Última atualização**: 2026-07-30
