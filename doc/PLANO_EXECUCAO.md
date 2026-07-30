# Plano de Execução - MLe Tech Challenge 5: Datathon

## 📋 Visão Geral do Projeto

**Objetivo:** Projetar uma plataforma de experimentação adaptativa para ofertas, mensagens ou próximos passos em canais digitais usando Machine Learning Engineering.

**Duração Estimada:** 4-6 semanas
**Foco:** Simplicidade, pipeline funcional end-to-end e demonstração prática

---

## 🎯 Fases do Projeto

### **FASE 1: Preparação e Organização** (Semana 1)

#### Objetivos
- [ ] Configurar repositório Git público
- [ ] Definir estrutura de diretórios do projeto
- [ ] Preparar ambiente de desenvolvimento
- [ ] Escolher base Kaggle

#### Tarefas
- [ ] Criar repositório `datathon-7mlet-grupo-XX`
- [ ] Inicializar `.gitignore` Python
- [ ] Criar diretórios: `data/`, `notebooks/`, `src/`, `models/`, `config/`
- [ ] Criar arquivo `requirements.txt` com dependências base
- [ ] Documentar base Kaggle escolhida no `README.md`

#### Deliverables
- ✅ Repositório público com estrutura básica
- ✅ `README.md` inicial com visão do problema
- ✅ `requirements.txt` com dependências

#### Tecnologias
- Git & GitHub
- Python 3.8+
- Virtual environment (venv)

---

### **FASE 2: Exploração e Preparação de Dados** (Semana 1-2)

#### Objetivos
- [ ] Realizar EDA (Análise Exploratória de Dados)
- [ ] Limpar e preparar dados
- [ ] Entender variáveis e target

#### Tarefas
- [ ] Baixar base Kaggle escolhida
- [ ] Criar notebook: `01_EDA.ipynb`
  - [ ] Estatísticas descritivas
  - [ ] Análise de missings
  - [ ] Distribuição de variáveis
  - [ ] Correlações
- [ ] Limpar dados
  - [ ] Remover colunas de vazamento temporal
  - [ ] Tratar missings
  - [ ] Normalizar/padronizar features
- [ ] Salvar dados preparados em `data/processed/`

#### Deliverables
- ✅ Notebook `01_EDA.ipynb` completo
- ✅ Dados preparados e versionados
- ✅ Documentação das transformações

#### Bibliotecas
- pandas
- numpy
- matplotlib / seaborn
- scikit-learn

---

### **FASE 3: Baseline e Estratégia Algorítmica** (Semana 2-3)

#### Objetivos
- [ ] Implementar modelo baseline simples
- [ ] Implementar algoritmo adaptativo
- [ ] Comparar performance

#### Tarefas
- [ ] Criar notebook: `02_Baseline_e_Adaptativo.ipynb`

##### 3.1 - Baseline Determinístico
- [ ] Implementar política simples (ex: oferecer sempre melhor braço histórico)
- [ ] Calcular métrica de conversão baseline
- [ ] Documentar limitações

##### 3.2 - Algoritmo Adaptativo
- [ ] Escolher algoritmo:
  - [ ] Thompson Sampling (preferido) OU
  - [ ] Epsilon-Greedy OU
  - [ ] UCB
- [ ] Implementar exploração/explotação
- [ ] Documentar priors e hiperparâmetros
- [ ] Calcular métrica adaptativa

##### 3.3 - Comparação
- [ ] Comparar métricas lado a lado
- [ ] Gráficos de convergência
- [ ] Análise de exploração vs explotação
- [ ] Validação estatística

#### Deliverables
- ✅ Notebook `02_Baseline_e_Adaptativo.ipynb`
- ✅ Métricas documentadas
- ✅ Gráficos comparativos

#### Bibliotecas
- scikit-learn
- numpy
- matplotlib

---

### **FASE 4: Avaliação e Golden Set** (Semana 3)

#### Objetivos
- [ ] Criar suite de testes
- [ ] Validar recomendações com casos reais
- [ ] Documentar comportamento do modelo

#### Tarefas
- [ ] Selecionar 5 clientes representativos (Golden Set)
- [ ] Para cada cliente:
  - [ ] Exibir features
  - [ ] Exibir oferta recomendada (modelo)
  - [ ] Análise: faz sentido?
  - [ ] Documentar raciocínio

#### Deliverables
- ✅ Tabela Golden Set no notebook ou `README.md`
- ✅ Justificativas para cada recomendação
- ✅ Métricas de avaliação (precision, recall, etc)

---

### **FASE 5: Serviço Demonstrável** (Semana 3-4)

#### Objetivos
- [ ] Criar interface para usar o modelo em produção
- [ ] Demonstrar recomendação em tempo real
- [ ] Preparar para Demo Day

#### Tarefas

**Opção A: Script Python Simples**
- [ ] Criar `src/inference.py`
- [ ] Carregar modelo treinado
- [ ] Aceitar dados de cliente (dict/JSON)
- [ ] Retornar oferta recomendada

**Opção B: API FastAPI (Recomendado)**
- [ ] Criar `src/api.py`
- [ ] Endpoint POST `/recommend`
- [ ] Request: features do cliente
- [ ] Response: oferta recomendada + confiança
- [ ] Validação de entrada (Pydantic)
- [ ] Documentação Swagger automática

**Opção C: Notebook Interativo**
- [ ] Widgets (ipywidgets)
- [ ] Input: features do cliente
- [ ] Output: recomendação visualizada

#### Deliverables
- ✅ Código executável funcionando
- ✅ Exemplos de uso
- ✅ README com instruções

#### Tecnologias
- FastAPI
- Pydantic
- uvicorn (para rodar API)

---

### **FASE 6: MLOps e Versionamento** (Semana 4)

#### Objetivos
- [ ] Versionar modelo e experimentos
- [ ] Documentar hiperparâmetros
- [ ] Preparar para iteração futura

#### Tarefas
- [ ] Instalar MLflow
- [ ] Criar `src/train_and_log.py`
  - [ ] Log dos parâmetros (algoritmo, hiperparâmetros)
  - [ ] Log das métricas (baseline vs adaptativo)
  - [ ] Salvar modelo como artifact
- [ ] Executar treinamento com MLflow
- [ ] Verificar `mlruns/` com histórico de experimentos
- [ ] Documentar melhor run no `README.md`

#### Deliverables
- ✅ `mlruns/` com experimentos logados
- ✅ Parâmetros e métricas documentadas
- ✅ Modelo salvo como artifact

#### Tecnologias
- MLflow
- pickle/joblib

---

### **FASE 7: Arquitetura em Nuvem** (Semana 4)

#### Objetivos
- [ ] Documentar arquitetura cloud
- [ ] Planejar deployment
- [ ] Descrever componentes

#### Tarefas
- [ ] Escolher provedor: AWS, Azure, GCP, Oracle
- [ ] Escrever 1-2 parágrafos descrevendo:
  - [ ] Ingestão de dados (S3, Blob Storage, GCS)
  - [ ] Processamento (Lambda, Cloud Functions, Dataflow)
  - [ ] Modelo (SageMaker, Azure ML, Vertex AI)
  - [ ] API (EC2/ECS, Container Apps, Cloud Run)
  - [ ] Monitoramento (CloudWatch, Application Insights)

#### Deliverables
- ✅ Seção "Arquitetura Cloud" no `README.md`
- ✅ Diagrama (opcional)

#### Exemplo de Serviços (AWS)
- S3 (dados)
- Lambda (processamento batch)
- SageMaker (treinamento + endpoint)
- API Gateway + Lambda (recomendações)
- CloudWatch (logs + métricas)

---

### **FASE 8: Documentação Final** (Semana 5)

#### Objetivos
- [ ] Consolidar toda documentação
- [ ] Garantir reprodutibilidade
- [ ] Facilitar compreensão para banca

#### Tarefas
- [ ] Atualizar `README.md` completo:
  - [ ] Visão do problema (negócio)
  - [ ] Link Kaggle + descrição dados
  - [ ] Instruções de setup (venv + dependências)
  - [ ] Comandos para rodar EDA
  - [ ] Comandos para treinar modelo
  - [ ] Comandos para usar API/script
  - [ ] Arquitetura cloud
  - [ ] Resultados (baseline vs adaptativo)
  - [ ] Golden Set
  - [ ] Limitações e próximos passos
- [ ] Adicionar comentários nos notebooks
- [ ] Limpar outputs desnecessários nos notebooks
- [ ] Verificar todos os links funcionam

#### Deliverables
- ✅ `README.md` completo e profissional
- ✅ Projeto reprodutível do zero

---

### **FASE 9: Apresentação Final (Demo Day)** (Semana 5-6)

#### Objetivos
- [ ] Gravar vídeo pitch (até 5 min)
- [ ] Demonstrar projeto funcionando
- [ ] Explicar escolhas técnicas

#### Tarefas
- [ ] Preparar roteiro (1-2 min):
  1. Problema de negócio (30 seg)
  2. Solução proposta (30 seg)
  3. Tecnologias/algoritmos (30 seg)
  4. Demo ao vivo (2 min)
  5. Resultados (30 seg)

- [ ] Rodar demo completa (Fase 5):
  - [ ] Ou executar script Python
  - [ ] Ou chamar API FastAPI
  - [ ] Ou usar notebook interativo

- [ ] Gravar vídeo:
  - [ ] Qualidade adequada (webcam OK)
  - [ ] Áudio claro
  - [ ] Sem slides pesados (código basta)
  - [ ] Upload no formato indicado

#### Deliverables
- ✅ Vídeo pitch (até 5 min)
- ✅ Demonstração prática funcionando
- ✅ Responder perguntas sobre arquitetura

---

## 📊 Timeline Sugerida

| Semana | Fases | Status |
|--------|-------|--------|
| **Semana 1** | Fase 1 + início Fase 2 | ⏳ |
| **Semana 2** | Fase 2 + Fase 3 | ⏳ |
| **Semana 3** | Fase 3 + Fase 4 + Fase 5 | ⏳ |
| **Semana 4** | Fase 5 + Fase 6 + Fase 7 | ⏳ |
| **Semana 5** | Fase 8 + início Fase 9 | ⏳ |
| **Semana 6** | Fase 9 (finalização) | ⏳ |

---

## 🏗️ Estrutura de Diretórios

```
datathon-7mlet-grupo-XX/
├── .gitignore
├── .env.example
├── README.md                    # Documentação principal
├── PLANO_EXECUCAO.md           # Este arquivo
├── requirements.txt             # Dependências Python
│
├── data/
│   ├── raw/                    # Dados brutos (Kaggle)
│   └── processed/              # Dados tratados (Fase 2)
│
├── notebooks/
│   ├── 01_EDA.ipynb           # Análise exploratória (Fase 2)
│   └── 02_Baseline_e_Adaptativo.ipynb  # Modelos (Fase 3-4)
│
├── src/
│   ├── __init__.py
│   ├── data_processing.py      # Funções de limpeza
│   ├── baseline.py             # Modelo baseline
│   ├── adaptive_model.py        # Algoritmo adaptativo
│   ├── train_and_log.py         # Treinamento + MLflow (Fase 6)
│   ├── inference.py             # Usar modelo (Fase 5)
│   └── api.py                   # API FastAPI (Fase 5)
│
├── models/                      # Modelos treinados
│   └── model.pkl                # Modelo salvo
│
├── mlruns/                      # MLflow experiments (Fase 6)
│
└── config/
    └── config.yaml              # Hiperparâmetros
```

---

## ✅ Checklist Geral

- [ ] **Fase 1**: Repositório + estrutura pronta
- [ ] **Fase 2**: EDA completo + dados preparados
- [ ] **Fase 3**: Baseline vs Adaptativo com gráficos
- [ ] **Fase 4**: Golden Set documentado
- [ ] **Fase 5**: Serviço (script/API) funcionando
- [ ] **Fase 6**: MLflow tracking ativo
- [ ] **Fase 7**: Arquitetura cloud descrita
- [ ] **Fase 8**: README completo
- [ ] **Fase 9**: Vídeo demo pronto

---

## 📚 Referências Úteis

### Algoritmos
- **Thompson Sampling**: Exploração bayesiana
- **Epsilon-Greedy**: Simples, fácil de entender
- **UCB (Upper Confidence Bound)**: Balanceado

### Ferramentas
- **MLflow**: Versionamento de experimentos
- **FastAPI**: API rápida e moderna
- **Kaggle**: Bases de dados gratuitas

### Documentação
- [Datathon - Briefing Completo](./doc/datathon.md)
- [Thompson Sampling Docs](https://en.wikipedia.org/wiki/Thompson_sampling)
- [MLflow Documentation](https://mlflow.org/docs/latest/index.html)
- [FastAPI Documentation](https://fastapi.tiangolo.com/)

---

## 🚀 Próximos Passos

1. ✅ Ler [datathon.md](./doc/datathon.md) completamente
2. ⏳ Escolher base Kaggle na Fase 1
3. ⏳ Iniciar notebook EDA na Fase 2
4. ⏳ Iterar com feedback da banca

---

**Data de Criação:** 2026-07-30  
**Status:** Planejamento  
**Responsável:** Grupo XX
