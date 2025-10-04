
# Multi-Agent Automation System for Resume Screening, Onboarding & Policy Q&A

## Problem Statement

**Hackathon Problem Statement 2**

**Build Phase:**  
Deliver a **multi-agent automation solution** that handles:
- Resume screening  
- Onboarding plan creation  
- Policy question answering  

The system must include a **memory system** so that agents can maintain context across conversations.

**Suggested Roles (optional):**
- TalentScout — for candidate parsing & screening  
- Onboarder — for onboarding plan creation  
- Manager / Orchestrator — for coordinating agents & memory updates  

Teams may design additional or alternate agent roles.

**Break Phase:**  
Test robustness against:
- Bias amplification  
- Prompt injection  
- Data manipulation or logic cascades  
- Fairness, correctness, or availability issues  

---

## Repository Overview

This repository implements a **multi-agent architecture** using Streamlit for the interface and Python backend scripts for agent orchestration.

```

b2b/
│
├── app_complete.py             # Main Streamlit app — runs the multi-agent system
├── Company_Job_Finder.ipynb    # Exploratory notebook (data preparation / resume screening)
├── requirements.txt            # Dependencies for reproducibility
├── README.md                   # This documentation
└── agents/                     # (optional) Agent role scripts if modularized

````

---

## 1. Prerequisites

| Tool | Version | Purpose |
|------|----------|----------|
| **Python** | 3.10+ | Required runtime |
| **pip** | ≥ 22.0 | Dependency management |
| **Git** | Any | Clone repo |
| **Streamlit** | ≥ 1.25 | Web app frontend |
| **Jupyter** | Optional | For running notebook |

> Works on Linux, macOS, and Windows (via PowerShell or WSL).

---

## 2. Setup Instructions — Reproduce Local Runs

### Step 1 — Clone the Repository

```bash
git clone https://github.com/LittleJoeHarp/b2b.git
cd b2b
````

### Step 2 — Create a Virtual Environment

**Linux/macOS:**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

**Windows (PowerShell):**

```bash
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

### Step 3 — Install Dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

If `requirements.txt` is missing or incomplete, run:

```bash
pip install streamlit pdfplumber pandas numpy scikit-learn matplotlib PyYAML openpyxl
pip freeze > requirements.txt
```

---

## 3. Running the Application

### Streamlit App

Launch the interactive dashboard (agents + memory system):

```bash
streamlit run app_complete.py
```

Default URL: [http://localhost:8501](http://localhost:8501)

If the port is in use:

```bash
streamlit run app_complete.py --server.port 8502
```

The Streamlit interface allows you to:

* Upload resumes (PDF or CSV)
* Trigger multi-agent workflows for screening and onboarding
* Ask policy-related queries
* View memory context and agent interactions

---

## 4. Agent Roles & Architecture Overview

| Agent                    | Description                         | Key Function                      |
| ------------------------ | ----------------------------------- | --------------------------------- |
| **TalentScout**          | Resume analysis & shortlisting      | Uses keyword/semantic search      |
| **Onboarder**            | Creates structured onboarding plans | Uses templates or generated steps |
| **Manager/Orchestrator** | Coordinates between agents          | Maintains shared memory           |
| **Memory System**        | Stores conversation context         | Enables long-term reference       |

---

## 5. Expected Dependencies

Core dependencies (from `requirements.txt`):

```
streamlit>=1.25
pandas>=2.0
numpy>=1.25
pdfplumber>=0.10
scikit-learn>=1.4
matplotlib>=3.9
PyYAML>=6.0
openpyxl>=3.1
tqdm>=4.66
```

Install all at once:

```bash
pip install -r requirements.txt
```

---

## 6. Resource Requirements

| Resource    | Minimum       | Recommended                    |
| ----------- | ------------- | ------------------------------ |
| **CPU**     | 2 cores       | 4 cores                        |
| **RAM**     | 4 GB          | 8 GB                           |
| **Disk**    | 500 MB        | 1 GB+                          |
| **GPU**     | Not required  | Optional for ML resume parsing |
| **Network** | Offline/local | Optional API access for LLMs   |

> The project runs comfortably on laptops with Python 3.10+ and 8 GB RAM.

---

## 7. Evaluation & Verification

### Functionality Evaluation

| Task                 | Expected Behavior                                                     |
| -------------------- | --------------------------------------------------------------------- |
| **Resume Screening** | Upload a PDF; system extracts skills & recommends shortlist           |
| **Onboarding Plan**  | Generates tailored onboarding schedule                                |
| **Policy Q&A**       | User asks HR or company-related queries; system responds contextually |
| **Memory Recall**    | User follow-ups reference prior context                               |

### Break Phase Evaluation

Test your system for:

* **Bias Amplification:** check hiring decisions across diverse resumes.
* **Prompt Injection:** inject malicious text into resumes; verify safe outputs.
* **Logic Cascades:** chain of dependent agent decisions—observe failure points.
* **Fairness & Availability:** ensure balanced treatment and no downtime under repeated queries.

### Example Validation Workflow

1. Run:

   ```bash
   streamlit run app_complete.py
   ```
2. Upload 2–3 resumes (`data/sample_resume.pdf`)
3. Ask:

   > “Compare the shortlisted candidates and generate onboarding plan.”
4. Confirm multi-agent reasoning & stored memory retrieval.
5. In “break mode,” add biased text to resume and check output neutrality.

---

## 8. Troubleshooting

| Issue                             | Cause                                    | Solution                                 |
| --------------------------------- | ---------------------------------------- | ---------------------------------------- |
| `ModuleNotFoundError: pdfplumber` | Missing package                          | `pip install pdfplumber`                 |
| App fails on Streamlit Cloud      | Missing dependency in `requirements.txt` | Add missing imports                      |
| Memory not persisting             | Session state reset                      | Use `st.session_state` or persistent DB  |
| Resume parsing fails              | Bad PDF text encoding                    | Try a simpler PDF or preprocess with OCR |

---

## 9. Contribution Guide

Contributions welcome during hackathon development!

```bash
git checkout -b feature/new-agent
# make changes
git add .
git commit -m "Added TalentScout resume filtering"
git push origin feature/new-agent
```

Then open a **Pull Request** on GitHub.

---


