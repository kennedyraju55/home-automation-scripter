# 🏠 Home Automation Scripter

Generate production-ready home automation scripts from natural language descriptions. Supports Home Assistant, IFTTT, openHAB, Node-RED, and SmartThings with 6 pre-built templates, script validation, and AI-powered suggestions — running 100% locally.

[![Python](https://img.shields.io/badge/Python-3.11+-3776AB.svg?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![Local LLM](https://img.shields.io/badge/Local_LLM-Ollama-000000.svg?style=for-the-badge&logo=ollama&logoColor=white)](https://ollama.com)
[![Privacy-First](https://img.shields.io/badge/100%25-Privacy--First-2ea043.svg?style=for-the-badge&logo=shield&logoColor=white)](#privacy-first)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)
[![FastAPI](https://img.shields.io/badge/FastAPI-REST_API-009688.svg?style=for-the-badge&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com)
[![Streamlit](https://img.shields.io/badge/Streamlit-Web_UI-FF4B4B.svg?style=for-the-badge&logo=streamlit&logoColor=white)](https://streamlit.io)

---

## ✨ Features

- **📝 Natural Language Scripts** - Describe automations in plain English
- **🏠 Multi-Platform Support** - Home Assistant, IFTTT, openHAB, Node-RED, SmartThings
- **📋 6 Pre-Built Templates** - Common automation patterns ready to customize
- **✅ Script Validation** - Platform-specific syntax checking
- **💡 AI Suggestions** - Get automation ideas based on your devices
- **🔍 Explainability** - AI explains what any script does
- **⚡ Quick Generation** - Go from description to working script in seconds
- **🔒 100% Local** - Your home config stays private
- **🎨 Web UI & API** - Web dashboard, CLI, or REST endpoints

---

## 🏗️ Architecture

```
┌──────────────────────┐
│   Natural Language   │
│   Description        │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│  Automation Engine   │
│ - Template Matching  │
│ - Code Generation    │
│ - Validation         │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│  Local LLM           │
│  (Ollama/Gemma)      │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│  Output Scripts      │
│ - Platform-Specific  │
│ - Ready to Deploy    │
└──────────────────────┘
```

---

## 📋 Project Structure

```
home-automation-scripter/
├── src/home_auto/
│   ├── __init__.py              # Package initialization
│   ├── core.py                  # Automation generation
│   ├── generators.py            # Platform generators
│   ├── validators.py            # Script validation
│   ├── cli.py                   # Click CLI interface
│   ├── api.py                   # FastAPI endpoints
│   └── web_ui.py                # Streamlit dashboard
├── templates/                   # Pre-built automation templates
│   ├── lighting.yaml
│   ├── climate.yaml
│   ├── security.yaml
│   ├── appliances.yaml
│   ├── notifications.yaml
│   └── schedules.yaml
├── tests/
│   ├── test_core.py             # Unit tests
│   └── __init__.py
├── config.yaml                  # Configuration
├── requirements.txt             # Dependencies
├── docker-compose.yml           # Docker setup
└── README.md                    # This file
```

---

## 🚀 Quick Start

### Prerequisites

- **Python 3.11+**
- **Ollama** (for local LLM)
- **Gemma 4 model** (via Ollama)

### Installation

```bash
# Clone the repository
git clone https://github.com/kennedyraju55/home-automation-scripter.git
cd home-automation-scripter

# Create and activate virtual environment
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Pull the AI model
ollama pull gemma4

# Verify installation
python -m home_auto.cli --help
```

### First Run

```bash
# Start Ollama
ollama serve &

# Generate an automation script
python -m home_auto.cli generate \
  --description "Turn on living room lights when I arrive home" \
  --platform "home-assistant" \
  --output automation.yaml

# Or launch web UI
streamlit run src/home_auto/web_ui.py

# Or use REST API
uvicorn src.home_auto.api:app --reload --port 8000
```

---

## 🛠️ Tech Stack

| Layer | Technology | Purpose |
|-------|-----------|---------|
| **Runtime** | Python 3.11+ | Core application |
| **CLI** | Click 8.1+ | Command-line interface |
| **Web** | Streamlit 1.28+ | Interactive dashboard |
| **API** | FastAPI | REST endpoints |
| **LLM** | Ollama + Gemma 4 | Script generation & suggestions |
| **Data** | YAML/JSON | Config & templates |
| **Testing** | pytest | Unit tests |
| **Deployment** | Docker | Container orchestration |

---

## 📖 CLI Reference

```bash
python -m home_auto.cli [COMMAND] [OPTIONS]
```

### Available Commands

| Command | Description | Example |
|---------|-------------|---------|
| generate | Create automation script | --description "..." --platform home-assistant |
| xplain | Explain existing script | --file automation.yaml |
| alidate | Check script syntax | --file automation.yaml --platform home-assistant |
| suggest | Get automation ideas | --devices "lights,thermostat" |
| list-templates | Show available templates | --category lighting |
| list-platforms | Show supported platforms | — |

---

## 🌐 Web UI

Launch the interactive dashboard:

```bash
streamlit run src/home_auto/web_ui.py
```

Access at **http://localhost:8501**

Features:
- ✍️ Natural language automation builder
- �� Template browser and customizer
- ✅ Real-time script validation
- 💡 AI suggestions based on your setup
- 📤 Export to multiple formats
- 🔍 Script explainability viewer
- 📚 Platform-specific documentation

---

## ⚡ REST API

All features via FastAPI endpoints.

```bash
uvicorn src.home_auto.api:app --reload --port 8000
```

Interactive docs: **http://localhost:8000/docs**

### API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /health | Health check |
| POST | /generate | Generate script from description |
| POST | /validate | Validate script syntax |
| POST | /explain | Explain script functionality |
| GET | /suggestions | Get automation ideas |
| GET | /templates | List available templates |

---

## 📋 Supported Platforms

| Platform | Support | Template Count |
|----------|---------|----------------|
| **Home Assistant** | ✅ Full | 6 templates |
| **IFTTT** | ✅ Full | 4 templates |
| **openHAB** | ✅ Full | 5 templates |
| **Node-RED** | ✅ Full | 5 templates |
| **SmartThings** | ✅ Full | 4 templates |

---

## 📋 Template Categories

### 1. Lighting (6 templates)
- Simple on/off
- Brightness control
- Color changes
- Scenes
- Motion-triggered
- Scheduled lighting

### 2. Climate (5 templates)
- Temperature control
- Humidity monitoring
- Fan automation
- Seasonal schedules
- Energy saving modes

### 3. Security (5 templates)
- Door/window alerts
- Motion detection
- Camera triggers
- Access control
- Emergency protocols

### 4. Appliances (4 templates)
- Smart plugs
- Washer/dryer
- Coffee makers
- Vacuum scheduling

### 5. Notifications (3 templates)
- Alert messages
- Email notifications
- Mobile push

### 6. Schedules (3 templates)
- Time-based routines
- Sunrise/sunset triggers
- Weekly patterns

---

## 🐳 Docker Deployment

```bash
git clone https://github.com/kennedyraju55/home-automation-scripter.git
cd home-automation-scripter

docker compose up

# Access at http://localhost:8501
```

---

## 🧪 Testing

```bash
# Run all tests
pytest tests/ -v

# Run with coverage
pytest tests/ --cov=home_auto --cov-report=term-missing

# Run specific test
pytest tests/test_core.py::test_script_generation -v
```

---

## ⚙️ Configuration

Create a config.yaml:

```yaml
llm:
  model: "gemma4"
  temperature: 0.3
  max_tokens: 2000

generators:
  home_assistant:
    version: "2024.1"
  ifttt:
    api_limit: 100
  openhab:
    version: "4.0"
  node_red:
    palette: ["node-red-dashboard"]
  smartthings:
    api_version: "v1"

validation:
  check_syntax: true
  check_compatibility: true
  suggest_optimizations: true
```

---

## 🔒 Privacy-First

100% local processing:
- ✅ No cloud API calls
- ✅ No home config tracking
- ✅ Your automation scripts stay private
- ✅ Full AI control
- ✅ GDPR/HIPAA compliant

---

## 📚 Python API

```python
from home_auto.core import generate_automation, validate_script
from home_auto.generators import HomeAssistantGenerator

# Generate automation from description
automation = generate_automation(
    description="Turn off all lights at bedtime",
    platform="home-assistant"
)

# Validate the generated script
validation = validate_script(
    script=automation['yaml'],
    platform="home-assistant"
)

print(f"Valid: {validation['is_valid']}")
print(f"Script:\n{automation['yaml']}")
```

---

## 🤝 Contributing

1. Fork the repository
2. Create feature branch: git checkout -b feature/amazing-feature
3. Commit changes: git commit -m 'Add amazing feature'
4. Push to branch: git push origin feature/amazing-feature
5. Open a Pull Request

---

## 📄 License

Licensed under the MIT License. See [LICENSE](LICENSE) for details.

---

## 👤 Author

**Nrk Raju Guthikonda**
- GitHub: [@kennedyraju55](https://github.com/kennedyraju55)
- Dev.to: [@kennedyraju55](https://dev.to/kennedyraju55)
- LinkedIn: [Nrk Raju Guthikonda](https://linkedin.com/in/nrk-raju-guthikonda)

---

<div align="center">

**Made with ❤️ by kennedyraju55**

[⭐ Star this repo if you found it helpful!](https://github.com/kennedyraju55/home-automation-scripter)

</div>
