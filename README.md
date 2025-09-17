[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

# GenAI-Text-Processing-Pipeline

This repository contains a **full-stack AI-powered pipeline** for processing plain-text documents, extracting structured information, and exposing it through both an **API** and an **interactive UI**.  

This project was built as part of an interview assignment for a **Gen-AI Developer role at Xorstack**.

---

## 🎯 Objective
The goal is to build a pipeline that can:
- Process raw text  
- Extract **dates** and **person names** (minimum requirement)  
- Output structured results in **JSON format**  

---

## 🔑 Key Features
- **Entity Extraction (NER)** → Hugging Face `dbmdz/bert-large-cased-finetuned-conll03-english`  
- **Regex-based Date Parsing** → Handles multiple formats & normalizes to ISO  
- **Flask Backend API** → Lightweight endpoints for integration  
- **Data Persistence** → Results saved in both **CSV** and **SQLite DB**  
- **Streamlit Frontend** → Interactive web UI for demonstration  
- **n8n Workflow** → Example automation integration  
- **Ngrok Integration** → Public URL tunneling for backend/frontend  

---

## ⚙️ Pipeline Components

### 1. AI/ML Core
- `extract_entities(text)` handles NER + date extraction.  
- Identifies:
  - **Persons**
  - **Locations**
  - **Organizations**
  - **Dates** (NER + regex-based)  

### 2. Flask API
Endpoints:
- `POST /process_text` → Process raw text  
- `POST /process_file` → Process uploaded `.txt` file  
- `GET /download_csv` → Download results in CSV  
- `GET /download_db` → Download results in SQLite DB  
- `GET /health` → Health check  

### 3. Data Persistence
- Results stored in:
  - **SQLite DB** → `results.db`  
  - **CSV file** → `results.csv`  

### 4. Streamlit Frontend
- Simple web UI (`frontend.py`)  
- Users can paste/upload text  
- JSON output displayed  
- Links to download CSV & DB  

### 5. Automation Workflow
- Sample **n8n workflow** (`n8n_workflow.json`) included  
- Example: new file in a folder → webhook → Flask API → results stored  

---

## 🚀 Getting Started
The pipeline is **self-contained** and best run via **Jupyter Notebook** (works well in **Google Colab**).

### ✅ Prerequisites
- Python **3.8+**  
- `pip` package manager  

---

## 🛠️ Setup & Execution
1. **Clone the repository**
   ```bash
   git clone https://github.com/Suhasbhat123/GenAI-Text-Processing-Pipeline.git
   cd GenAI-Text-Processing-Pipeline
2. **Open `GenText.ipynb`** in:
   - JupyterLab  
   - VS Code  
   - Google Colab (recommended for better user experience)  

3. **Run all cells in order. The notebook will:**

   - Install dependencies (`flask`, `streamlit`, `transformers`, `pyngrok`, etc.)  
   - Define entity extraction and persistence logic  
   - Start Flask backend (with ngrok URL)  
   - Launch Streamlit frontend (with ngrok URL)  
   - Process sample inputs & save results  
   - Show final CSV and DB contents
  
## 📊 Output & Results

Once the pipeline is running, the output can be accessed in three ways:

### 1. Direct API Response (JSON)

Send a request to the Flask backend:
<pre> ``` // Example response: { "persons": [{"text": "John Doe", "label": "PER"}], 
  "locations": [], "organizations": [], 
  "ner_dates": [{"text": "2025"}],
  "regex_dates": [{"text": "September 23, 2025", "iso": "2025-09-23"}] } ``` </pre>


### 2. Results in CSV

All processed results are automatically appended to results.csv.

Open with:
<pre>```cat results.csv``` </pre>


### 3. Results in SQLite Database

The same results are also stored in results.db.

##Query directly:

<pre>```sqlite3 results.db "SELECT id, input_text, extracted_json, created_at FROM results LIMIT 10;"``` </pre>


##Or use the helper script:

<pre>```python show_results.py``` </pre>









  ## 📝 License
This project is licensed under the [MIT License](LICENSE) © 2025 Suhas Bhat.
