# EduDebate AI 🎓🤖

> An intelligent multi-agent debate system that transforms complex topics into structured learning materials using Google's Agent Development Kit (ADK) and Gemini models.

[![Made with ADK](https://img.shields.io/badge/Made%20with-Google%20ADK-4285F4?style=flat-square&logo=google)](https://github.com/google/genai-adk)
[![Gemini](https://img.shields.io/badge/Powered%20by-Gemini-8E75B2?style=flat-square)](https://deepmind.google/technologies/gemini/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](https://opensource.org/licenses/MIT)

## 🌟 Overview

EduDebate AI leverages a sophisticated multi-agent architecture to research, debate, and synthesize educational content on any topic. The system combines real-time research, balanced argumentation, and automated learning material generation.

---

## ⚙️ Setup & Environment

### 📦 Installation

```bash
pip install google-adk>=1.18.0
```

### 🔑 Configure API Key

**In Kaggle:**
1. Navigate to **Settings → Secrets**
2. Add a new secret:
   - **Name:** `GOOGLE_API_KEY`
   - **Value:** `<your-Gemini-API-key>`

**In Code:**

EduDebate AI automatically loads the API key:

```python
from kaggle_secrets import UserSecretsClient
import os

os.environ["GOOGLE_API_KEY"] = UserSecretsClient().get_secret("GOOGLE_API_KEY")
```

---

## 🧠 Agents Overview

| Agent | Model | Purpose | Tools |
|-------|-------|---------|-------|
| **Research Agent** | Gemini 2.5 Flash | Gather authoritative, recent sources | `google_search` |
| **Pro Agent** | Gemini 2.5 Flash | Argue for the topic | `calc` |
| **Con Agent** | Gemini 2.5 Flash | Argue against the topic | `calc` |
| **Scribe-Tutor Agent** | Gemini 2.0 Flash | Create learning materials | (none) |
| **Root Agent** | Gemini 2.5 Flash | Orchestrate all via AgentTool | `AgentTool(...)`, `calc` |

---

## 🚀 Usage

### ▶️ Run the Notebook

```python
await main(
    "What are the latest advancements in quantum computing and what do they mean for AI?",
    level="intermediate"
)
```

### 📊 Example Output

#### 🔎 RESEARCH — SOURCES
```
[src_1] "Quantum Supremacy in 2024" — Nature (2024)
[src_2] "AI-assisted Quantum Circuit Design" — arXiv (2025)
...
```

#### 🗣️ DEBATE — FINAL OUTPUT

**Pro:**
1. Quantum algorithms accelerate AI optimization processes ...

**Con:**
1. Hardware constraints limit commercial scalability ...

#### 🎓 LEARNING PACK
- ✅ Key Takeaways  
- ✅ Pros/Cons Table  
- ✅ Glossary (5 terms)  
- ✅ Quiz (5 questions + answers)

---

## 🧰 Implementation Highlights

| ADK Concept | Implementation |
|-------------|----------------|
| **Multi-Agent System** | Root → (Research + Pro + Con + Tutor) |
| **AgentTool Integration** | Root Agent calls sub-agents as tools |
| **Built-in Tools** | `google_search` |
| **Custom Tool** | `calc()` |
| **Observability** | `LoggingPlugin` across agents + tools |
| **Session Management** | `InMemoryRunner` |
| **Gemini Models** | 2.5 Flash / 2.0 Flash |
| **Deployment Ready** | Compatible with Cloud Run or Agent Engine |

---

## 📈 Sample Logging Output

```
[logging_plugin] Model: gemini-2.5-flash  
[logging_plugin] Agent: edudebate_root  
[logging_plugin] Tool Calls: [AgentTool(research_agent), AgentTool(pro_agent), 
                              AgentTool(con_agent), AgentTool(scribe_tutor)]  
[logging_plugin] Status: SUCCESS (elapsed_ms = 2380)
```

---

## 🧮 Evaluation Rubric Mapping

| Category | Points | How Satisfied |
|----------|--------|---------------|
| **Pitch** | 30 | Clear problem + educational impact + value |
| **Implementation** | 65–70 | Multi-agent pipeline + tools + observability |
| **Bonus** | 15–20 | Gemini use ✓ Logging ✓ Deployment Ready ✓ |

---

## 📚 Use Cases

- **STEM Education:** Explain advanced tech through balanced reasoning
- **Research Summarization:** Multi-view synthesis of emerging papers
- **AI Ethics Courses:** Structured debates on policy & impact
- **Academic Writing:** Generate balanced perspectives on complex topics
- **Professional Development:** Create custom learning materials on demand

---

## 🏁 Results

✅ Real-time factual grounding with Google Search  
✅ Structured multi-agent reasoning via AgentTool  
✅ Transparent execution logs with LoggingPlugin  
✅ Converts AI debate into structured learning material

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────┐
│           Root Agent (Orchestrator)         │
│         Gemini 2.5 Flash + AgentTool        │
└────────────┬────────────────────────────────┘
             │
     ┌───────┴───────┬───────────┬────────────┐
     ▼               ▼           ▼            ▼
┌─────────┐   ┌──────────┐ ┌──────────┐ ┌─────────────┐
│Research │   │   Pro    │ │   Con    │ │Scribe-Tutor │
│ Agent   │   │  Agent   │ │  Agent   │ │   Agent     │
└─────────┘   └──────────┘ └──────────┘ └─────────────┘
```



---

## 📜 License

MIT License © 2025 EduDebate AI Project Team

See [LICENSE](LICENSE) file for details.

---

## ✨ Acknowledgments

Built with [Google Agent Development Kit (ADK)](https://github.com/google/genai-adk) and Gemini Models  
for the **Kaggle + Google ADK Challenge 2025**

---

