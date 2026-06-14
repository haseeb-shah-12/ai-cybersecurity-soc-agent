# 🔒 AI Cybersecurity SOC Agent

An advanced **multi-agent AI system** for Security Operations Centers (SOCs) powered by LangGraph, LLMs, and machine learning. This system automates threat detection, incident response, anomaly detection, and provides intelligent security insights through agentic AI workflows.

## 🎯 Core Features

### Agentic AI & Multi-Agent Systems
- **LangGraph-based Orchestration** - Stateful, graph-based agent workflows
- **Multi-Agent Architecture** - Specialized agents for different security domains
  - **Threat Detection Agent** - Identifies suspicious patterns and anomalies
  - **Incident Response Agent** - Coordinates automated response actions
  - **Log Analysis Agent** - Parses and extracts security events
  - **Threat Intelligence Agent** - Retrieves and correlates threat data
  - **Anomaly Detection Agent** - Uses ML for behavioral analysis
  - **Classification Agent** - Labels and prioritizes incidents

### Threat Detection & Response
- 🚨 **Real-time Log Analysis** - Process security logs from multiple sources
- 🔍 **Anomaly Detection** - Statistical and ML-based anomaly detection
- 📊 **Pattern Matching** - Identify known attack signatures
- 🎯 **Threat Classification** - ML-based threat severity and type classification
- ⚡ **Automated Response Playbooks** - Execute response actions based on threat type
- 📈 **Incident Correlation** - Link related security events

### Intelligence & Context
- 🧠 **RAG (Retrieval-Augmented Generation)** - Query security knowledge base
- 📚 **Security Knowledge Retrieval** - Custom threat intelligence integration
- 🔗 **LLM-powered Analysis** - GPT-4/Claude for contextual threat analysis
- 🎓 **Few-shot Learning** - Learn from historical incidents

### Deployment & Operations
- 🐳 **Docker Containerization** - Production-ready containerization
- ⚙️ **FastAPI Endpoints** - RESTful API for agent interactions
- 📊 **MLOps Pipeline** - Model training, evaluation, and deployment
- 📈 **Monitoring & Observability** - Prometheus metrics and structured logging
- 🔄 **CI/CD Ready** - GitHub Actions workflows

## 📋 Technology Stack

| Layer | Technologies |
|-------|---------------|
| **Agent Orchestration** | LangGraph, LangChain, Pydantic |
| **LLMs** | OpenAI GPT-4, Claude, Local LLMs |
| **ML/Anomaly Detection** | scikit-learn, PyOD, XGBoost |
| **Data Processing** | Pandas, NumPy, Elasticsearch |
| **API Framework** | FastAPI, Uvicorn |
| **Deployment** | Docker, Docker Compose |
| **Knowledge Retrieval** | FAISS/Chroma (RAG), Pinecone |
| **Monitoring** | Prometheus, Structured Logging |
| **Testing** | Pytest, Mock |

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────┐
│           Data Sources (Logs, Events, Streams)          │
│  ┌──────────────────────────────────────────────────┐   │
│  │ Elasticsearch | Splunk | AWS | GCP | Syslog     │   │
│  └──────────────────────────────────────────────────┘   │
└────────────────────┬────────────────────────────────────┘
                     │
┌────────────────────▼────────────────────────────────────┐
│         Log Ingestion & Pre-processing Layer            │
│  ┌──────────────────────────────────────────────────┐   │
│  │ Parsing | Normalization | Enrichment             │   │
│  └──────────────────────────────────────────────────┘   │
└────────────────────┬────────────────────────────────────┘
                     │
┌────────────────────▼────────────────────────────────────┐
│   LangGraph Multi-Agent Orchestration Layer             │
│  ┌──────────────────────────────────────────────────┐   │
│  │  ┌─────────────────────────────────────────┐    │   │
│  │  │ Threat Detection Agent                  │    │   │
│  │  │ ├─ Pattern Matching                     │    │   │
│  │  │ ├─ Anomaly Detection (ML)               │    │   │
│  │  │ └─ Threat Scoring                       │    │   │
│  │  └─────────────────────────────────────────┘    │   │
│  │  ┌─────────────────────────────────────────┐    │   │
│  │  │ Log Analysis Agent                      │    │   │
│  │  │ ├─ Parse & Normalize                    │    │   │
│  │  │ ├─ Extract IoCs                         │    │   │
│  │  │ └─ Correlate Events                     │    │   │
│  │  └─────────────────────────────────────────┘    │   │
│  │  ┌─────────────────────────────────────────┐    │   │
│  │  │ Threat Intelligence Agent (RAG)         │    │   │
│  │  │ ├─ Query Knowledge Base                 │    │   │
│  │  │ ├─ Retrieve Context                     │    │   │
│  │  │ └─ Enrich Findings                      │    │   │
│  │  └─────────────────────────────────────────┘    │   │
│  │  ┌─────────────────────────────────────────┐    │   │
│  │  │ Incident Response Agent                 │    │   │
│  │  │ ├─ Execute Playbooks                    │    │   │
│  │  │ ├─ Notify Teams                         │    │   │
│  │  │ └─ Track Response                       │    │   │
│  │  └─────────────────────────────────────────┘    │   │
│  │  ┌─────────────────────────────────────────┐    │   │
│  │  │ Classification Agent (ML)               │    │   │
│  │  │ ├─ Severity Classification              │    │   │
│  │  │ ├─ Threat Type Detection                │    │   │
│  │  │ └─ False Positive Filtering             │    │   │
│  │  └──��──────────────────────────────────────┘    │   │
│  └──────────────────────────────────────────────────┘   │
└────────────────────┬────────────────────────────────────┘
                     │
┌────────────────────▼────────────────────────────────────┐
│    LLM-Enhanced Analysis & Decision Making              │
│  ┌──────────────────────────────────────────────────┐   │
│  │ GPT-4 / Claude / Local LLM                       │   │
│  │ ├─ Contextual Threat Analysis                    │   │
│  │ ├─ Recommendation Generation                     │   │
│  │ └─ Report Writing                                │   │
│  └──────────────────────────────────────────────────┘   │
└────────────────────┬────────────────────────────────────┘
                     │
┌────────────────────▼────────────────────────────────────┐
│           Alert & Response Generation                   │
│  ┌──────────────────────────────────────────────────┐   │
│  │ Slack | Jira | PagerDuty | Email | Webhooks     │   │
│  └──────────────────────────────────────────────────┘   │
└────────────────────┬────────────────────────────────────┘
                     │
┌────────────────────▼────────────────────────────────────┐
│     FastAPI Dashboard & Monitoring                      │
│  ┌──────────────────────────────────────────────────┐   │
│  │ REST API | WebSocket | Prometheus | Logs        │   │
│  └──────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────┘
```

## 🚀 Quick Start

### Prerequisites
- Python 3.9+
- Docker & Docker Compose
- OpenAI API key (or alternative LLM)
- Elasticsearch (optional, for log source)

### Installation

```bash
# Clone repository
git clone https://github.com/haseeb-shah-12/ai-cybersecurity-soc-agent.git
cd ai-cybersecurity-soc-agent

# Create virtual environment
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Setup environment
cp .env.example .env
# Edit .env with your configuration
```

### Run Locally

```bash
# Start the FastAPI server
python -m uvicorn src.api.server:app --reload

# In another terminal, run the agent
python main.py
```

### Run with Docker

```bash
# Build and start services
docker-compose up --build

# Check logs
docker-compose logs -f soc-agent
```

## 📁 Project Structure

```
ai-cybersecurity-soc-agent/
├── src/
│   ├── agents/                      # Multi-agent system (LangGraph)
│   │   ├── __init__.py
│   │   ├── base_agent.py           # Base agent class
│   │   ├── threat_detection.py     # Threat detection agent
│   │   ├── log_analysis.py         # Log analysis agent
│   │   ├── threat_intelligence.py  # RAG-based threat intel agent
│   │   ├── incident_response.py    # Incident response agent
│   │   ├── classification.py       # ML classification agent
│   │   ├── orchestrator.py         # LangGraph orchestration
│   │   └── workflows/
│   │       ├── threat_detection_workflow.py
│   │       └── incident_response_workflow.py
│   │
│   ├── detectors/                   # Threat detection modules
│   │   ├── __init__.py
│   │   ├── anomaly_detector.py     # Statistical & ML anomalies
│   │   ├── pattern_matcher.py      # Signature-based detection
│   │   ├── ioc_extractor.py        # IoC extraction
│   │   └── models/
│   │       ├── isolation_forest.pkl
│   │       └── threat_classifier.pkl
│   │
│   ├── ml/                          # Machine learning pipelines
│   │   ├── __init__.py
│   │   ├── anomaly_detection.py    # PyOD models
│   │   ├── classification.py       # Threat classification
│   │   ├── feature_engineering.py  # Feature extraction
│   │   └── training.py             # Model training pipeline
│   │
│   ├── rag/                         # RAG system for threat intelligence
│   │   ├── __init__.py
│   │   ├── knowledge_base.py       # Knowledge base setup
│   │   ├── retriever.py            # RAG retriever
│   │   ├── documents/
│   │   │   ├── mitre_attack.md
│   │   │   ├── cve_database.md
│   │   │   └── threat_intelligence.md
│   │   └── embeddings.py           # Embedding models
│   │
│   ├── integrations/                # External integrations
│   │   ├── __init__.py
│   │   ├── elasticsearch_client.py # Elasticsearch connector
│   │   ├── siem_connector.py       # SIEM integrations
│   │   ├── log_sources/
│   │   │   ├── cloudtrail.py
│   │   │   ├── windows_events.py
│   │   │   └── firewall_logs.py
│   │   ├── alerting.py             # Alert channels (Slack, Jira, etc.)
│   │   └── playbooks.py            # Incident response playbooks
│   │
│   ├── llm/                         # LLM integration
│   │   ├── __init__.py
│   │   ├── models.py               # LLM model wrappers
│   │   ├── prompts.py              # Prompt templates
│   │   └── callbacks.py            # LLM callbacks & monitoring
│   │
│   ├── api/                         # FastAPI server
│   │   ├── __init__.py
│   │   ├── server.py               # Main FastAPI app
│   │   ├── routes/
│   │   │   ├── agents.py           # Agent endpoints
│   │   │   ├── logs.py             # Log ingestion endpoints
│   │   │   ├── incidents.py        # Incident management endpoints
│   │   │   ├── threats.py          # Threat analysis endpoints
│   │   │   └── health.py           # Health check
│   │   ├── schemas.py              # Pydantic schemas
│   │   └── middleware.py           # Auth, logging, monitoring
│   │
│   ├── utils/                       # Utilities
│   │   ├── __init__.py
│   │   ├── logger.py               # Structured logging
│   │   ├── config.py               # Configuration management
│   │   ├── cache.py                # Caching utilities
│   │   └── validators.py           # Input validation
│   │
│   ├── models/                      # Data models
│   │   ├── __init__.py
│   │   ├── schemas.py              # Pydantic models
│   │   ├── threat.py               # Threat data models
│   │   └── incident.py             # Incident data models
│   │
│   └── monitoring/                  # Observability
│       ├── __init__.py
│       ├── metrics.py              # Prometheus metrics
│       └── tracing.py              # Distributed tracing
│
├── config/
│   ├── config.yaml                 # Main configuration
│   ├── agents.yaml                 # Agent configurations
│   ├── models.yaml                 # ML model configurations
│   ├── threats.yaml                # Threat definitions
│   └── playbooks.yaml              # Response playbooks
│
├── data/
│   ├── logs/                        # Sample logs
│   ├── models/                      # Trained ML models
│   └── knowledge_base/              # RAG knowledge base
│
├── tests/
│   ├── __init__.py
│   ├── unit/
│   │   ├── test_agents.py
│   │   ├── test_detectors.py
│   │   ├── test_ml.py
│   │   └── test_rag.py
│   ├── integration/
│   │   ├── test_workflows.py
│   │   └── test_api.py
│   └── fixtures/
│       └── sample_logs.json
│
├── docs/
│   ├── ARCHITECTURE.md
│   ├── SETUP.md
│   ├── API.md
│   ├── AGENTS.md
│   ├── ML_PIPELINE.md
│   └── RAG_SYSTEM.md
│
├── scripts/
│   ├── train_models.py             # Train ML models
│   ├── build_knowledge_base.py      # Build RAG KB
│   ├── generate_sample_logs.py      # Generate test data
│   └── deploy.sh                    # Deployment script
│
├── Dockerfile
├── docker-compose.yml
├── requirements.txt
├── requirements-dev.txt
├── .env.example
├── .gitignore
├── pytest.ini
├── main.py                          # Entry point
└── README.md
```

## 🔄 Agent Workflows

### Threat Detection Workflow
```
Log Input → Log Analysis Agent → Anomaly Detection → Pattern Matching 
→ Classification Agent → Threat Intelligence Agent (RAG) → LLM Analysis 
→ Alert Generation
```

### Incident Response Workflow
```
High-Severity Threat → Incident Response Agent → Execute Playbook 
→ Notify Teams → Track Response → Report Results
```

## 🤖 Multi-Agent System

| Agent | Responsibility |
|-------|-----------------|
| **Log Analysis Agent** | Parse, normalize, and enrich security logs |
| **Threat Detection Agent** | Identify suspicious patterns and anomalies |
| **Classification Agent** | Classify threats by severity and type (ML-based) |
| **Threat Intelligence Agent** | Query RAG knowledge base for context |
| **Incident Response Agent** | Execute automated response playbooks |
| **Orchestrator Agent** | Coordinate multi-agent workflows (LangGraph) |

## 📊 ML Components

- **Anomaly Detection**: Isolation Forest, LOF, Autoencoders
- **Classification**: XGBoost, Random Forest threat severity/type
- **Feature Engineering**: Log pattern extraction, statistical features
- **MLOps**: Model versioning, A/B testing, monitoring

## 🧠 RAG System

- **Knowledge Sources**: MITRE ATT&CK, CVE database, threat intelligence
- **Embedding Model**: OpenAI embeddings or sentence-transformers
- **Vector Store**: FAISS, Chroma, or Pinecone
- **Retrieval**: Semantic search for threat context

## 🐳 Docker Deployment

```bash
# Build images
docker-compose build

# Start services
docker-compose up -d

# View logs
docker-compose logs -f soc-agent

# Stop services
docker-compose down
```

## 📡 API Endpoints

- `POST /api/v1/agents/analyze` - Analyze security events
- `POST /api/v1/logs/ingest` - Ingest security logs
- `GET /api/v1/incidents` - List incidents
- `POST /api/v1/incidents/{id}/respond` - Execute incident response
- `GET /api/v1/threats` - Get threat analysis
- `GET /api/v1/health` - Health check
- `GET /metrics` - Prometheus metrics

## 🧪 Testing

```bash
# Run all tests
pytest

# Run with coverage
pytest --cov=src

# Run specific test
pytest tests/unit/test_agents.py
```

## 📚 Documentation

- [Architecture](docs/ARCHITECTURE.md) - System design and data flow
- [Setup Guide](docs/SETUP.md) - Installation and configuration
- [API Reference](docs/API.md) - REST API endpoints
- [Agent Guide](docs/AGENTS.md) - Agent behaviors and workflows
- [ML Pipeline](docs/ML_PIPELINE.md) - Model training and evaluation
- [RAG System](docs/RAG_SYSTEM.md) - Knowledge retrieval setup

## 🛠️ Development

```bash
# Install dev dependencies
pip install -r requirements-dev.txt

# Format code
black src tests

# Lint
flake8 src tests

# Type checking
mypy src
```

## 🔐 Security Best Practices

- Store API keys in environment variables
- Use secrets management (HashiCorp Vault, AWS Secrets Manager)
- Validate all inputs
- Implement rate limiting
- Enable audit logging
- Use HTTPS for API
- Regular security testing

## 📈 Monitoring & Observability

- Prometheus metrics for all agents
- Structured logging with JSON format
- Distributed tracing (OpenTelemetry)
- Alert thresholds and SLOs
- Performance dashboards (Grafana)

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

MIT License - see LICENSE file

## 📞 Support & Contact

For questions, issues, or suggestions:
- Open an [GitHub Issue](https://github.com/haseeb-shah-12/ai-cybersecurity-soc-agent/issues)
- Reach out to the maintainer

## 🌟 Roadmap

- [ ] WebSocket support for real-time alerts
- [ ] Advanced visualization dashboard
- [ ] Kubernetes deployment manifests
- [ ] Multi-LLM support (Claude, Llama)
- [ ] Advanced threat modeling
- [ ] Automated playbook generation
- [ ] Integration with more SIEM platforms
- [ ] Custom model fine-tuning

---

**Built with ❤️ for cybersecurity teams**
