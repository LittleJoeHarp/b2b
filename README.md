# b2b
This repository contains a **Streamlit-based Business-to-Business (B2B) and job matching web app**, along with a supporting Jupyter notebook for data exploration and feature development.  
It is designed for easy local deployment and experimentation with datasets to automate job matching, PDF parsing, and business data analytics.

---

## Table of Contents
- [Overview](#overview)
- [Repository Structure](#repository-structure)
- [1. Prerequisites](#1-prerequisites)
- [2. Setup and Installation](#2-setup-and-installation)
- [3. Running the App Locally](#3-running-the-app-locally)
- [4. Running the Jupyter Notebook](#4-running-the-jupyter-notebook)
- [5. Expected Dependencies](#5-expected-dependencies)
- [6. System Requirements](#6-system-requirements)
- [7. Evaluation & Verification](#7-evaluation--verification)
- [8. Troubleshooting](#8-troubleshooting)
- [9. Contribution](#9-contribution)
---

## Overview

The **B2B Job Finder** app provides an AI-assisted pipeline for:
- Parsing structured data (like PDFs or Excel files),
- Matching candidates or companies using configurable filters,
- Visualizing relevant statistics interactively through Streamlit.

It integrates machine learning / text processing components and supports local PDF data extraction using `pdfplumber`.

---

## Repository Structure

```

b2b/
│
├── app_complete.py              # Streamlit app entry point
├── Company_Job_Finder.ipynb     # Jupyter notebook for exploration
├── requirements.txt             # All Python dependencies
├── data/                        # (optional) Directory for local CSVs/PDFs
└── README.md                    # Project documentation (this file)

````

---

## 1. Prerequisites

| Tool | Version | Notes |
|------|----------|-------|
| **Python** | 3.8 – 3.11 | Recommended: 3.10 |
| **pip** | ≥ 22.0 | For installing packages |
| **Git** | Any recent version | For cloning the repository |
| **Streamlit** | ≥ 1.25 | For running the web app |
| **Jupyter** | ≥ 6.5 | Optional, for `.ipynb` notebook |

> On Windows, **WSL (Ubuntu)** is recommended for a smoother experience with Python environments.

---

## 2. Setup and Installation

### Step 1 — Clone the repository
```bash
git clone https://github.com/LittleJoeHarp/b2b.git
cd b2b
````

### Step 2 — Create a virtual environment

**Linux / macOS:**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

**Windows (PowerShell):**

```bash
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

### Step 3 — Install dependencies

Make sure `pip` is up to date:

```bash
python -m pip install --upgrade pip
```

Then install required packages:

```bash
pip install -r requirements.txt
```

If you don’t have `requirements.txt`, create it manually using:

```bash
pip install streamlit pdfplumber pandas numpy matplotlib scikit-learn openpyxl PyYAML tqdm
pip freeze > requirements.txt
```

---

## 3. Running the App Locally

Once the dependencies are installed, run the Streamlit app:

```bash
streamlit run app_complete.py
```

This will start a local server (default port **8501**).
Open the browser and go to [http://localhost:8501](http://localhost:8501)

If you need a different port:

```bash
streamlit run app_complete.py --server.port 8502
```

---

## 4. Running the Jupyter Notebook

If you want to explore or test the notebook:

```bash
pip install jupyterlab notebook
jupyter notebook Company_Job_Finder.ipynb
```

You can also open it in **VS Code** or **JupyterLab**.

Run all cells sequentially to reproduce the notebook’s results.

---

## 5. Expected Dependencies

Below is a typical dependency list that supports this app:

| Package            | Purpose                                                 |
| ------------------ | ------------------------------------------------------- |
| `streamlit`        | Web app frontend framework                              |
| `pdfplumber`       | PDF parsing and text extraction                         |
| `pandas`, `numpy`  | Data processing and manipulation                        |
| `matplotlib`       | Visualization                                           |
| `scikit-learn`     | ML / data preprocessing (if used in job matching logic) |
| `openpyxl`, `xlrd` | Excel read/write support                                |
| `PyYAML`, `tqdm`   | Configuration and progress bars                         |

You can verify installation with:

```bash
pip list
```

---

## 6. System Requirements

| Resource         | Minimum      | Recommended                   |
| ---------------- | ------------ | ----------------------------- |
| **CPU**          | Dual-core    | Quad-core+                    |
| **Memory (RAM)** | 4 GB         | 8 GB+                         |
| **Disk Space**   | 500 MB       | 1 GB (with datasets)          |
| **GPU**          | Not required | Optional (if ML models added) |

---

## 7. Evaluation & Verification

### App verification

After running:

```bash
streamlit run app_complete.py
```

Check:

* The browser opens the Streamlit interface.
* No `ModuleNotFoundError` or traceback appears in the terminal.
* UI elements load properly (buttons, uploaders, text fields).
* Upload a sample file (PDF or CSV) and confirm that results / analysis appear correctly.

### Notebook verification

* Launch Jupyter and run all cells in `Company_Job_Finder.ipynb`.
* Verify that:

  * All cells execute without errors.
  * Dataframes / charts are displayed.
  * Any intermediate files (e.g., outputs) are created in the local directory.

### Optional Test Run

If you wish to verify imports:

```bash
python -c "import streamlit, pdfplumber, pandas, numpy; print('All good!')"
```

---

## 8. Troubleshooting

| Problem                                      | Cause                                    | Solution                                           |
| -------------------------------------------- | ---------------------------------------- | -------------------------------------------------- |
| `ModuleNotFoundError: pdfplumber`            | Missing package                          | `pip install pdfplumber`                           |
| Streamlit Cloud deployment fails             | Missing dependency in `requirements.txt` | Add all imports to `requirements.txt` and redeploy |
| `ImportError: openpyxl`                      | Missing Excel library                    | `pip install openpyxl`                             |
| App shows “Error has been redacted”          | Streamlit Cloud sandbox error            | Debug locally first, check logs via “Manage App”   |
| `OSError: [Errno 98] Address already in use` | Port conflict                            | Use another port: `--server.port 8502`             |

---

## 9. Contribution

1. Fork the repository.
2. Create a feature branch:

   ```bash
   git checkout -b feature/new-improvement
   ```
3. Commit your changes and push:

   ```bash
   git add .
   git commit -m "Add feature XYZ"
   git push origin feature/new-improvement
   ```
4. Create a Pull Request (PR) on GitHub.

---

## Notes

* Always ensure your virtual environment is activated before running Streamlit.
* If deploying on **Streamlit Cloud**, check that your main entrypoint (`app_complete.py`) is at the repo root and that your `requirements.txt` includes every imported library.
* The notebook and app share the same environment, so reusing the same `.venv` is recommended.

---




