# GenAI-Text-Processing-Pipeline
This repository contains a full-stack, AI-powered pipeline designed to process plain-text documents, extract structured information, and expose it via a lightweight API and an interactive web interface. This project was completed as an interview assignment for a Gen-AI Developer role at Xorstack.

Objective
The primary objective of this project is to build a small AI-powered pipeline that can process text, extract specific entities, and integrate into an automation workflow. The pipeline must, at a minimum, be able to extract dates and person names and output them in a JSON format.

The solution demonstrates the following key capabilities:

AI/ML Component: Implemented using an open-source model from Hugging Face.

Integration: Demonstrated via a lightweight Flask API and an example n8n workflow.

Data Storage: Stores processed results in both a CSV file and a SQLite database.

Deliverables: Provides all required components, including a code repository, working code, and example input/output.

Pipeline Components
The project is built with Python and consists of several interconnected parts:

AI/ML Core: The extract_entities function is the core of the pipeline. It uses the dbmdz/bert-large-cased-finetuned-conll03-english model for Named Entity Recognition (NER). It extracts persons, locations, and organizations. Additionally, it uses regular expressions to robustly identify and normalize various date formats.

Lightweight API (Flask Backend): A Flask application serves as the main integration point. It provides several endpoints:

POST /process_text: Processes raw text submitted in the request body.

POST /process_file: Processes an uploaded .txt file.

GET /download_csv: Allows downloading the results.csv file.

GET /download_db: Allows downloading the results.db database file.

GET /health: A simple health check endpoint.

Data Persistence: A save_result function stores the processed input and its extracted JSON output. This data is written to a local SQLite database (results.db) and appended to a CSV file (results.csv).

Interactive Frontend (Streamlit): A simple Streamlit UI (frontend.py) allows for easy demonstration of the pipeline. Users can paste text or upload a file, and the UI will send a request to the backend API, display the JSON output, and provide download links for the full results.

Automation Workflow: A sample n8n workflow export (n8n_workflow.json) is included. This JSON snippet demonstrates a practical use case where a new file uploaded to a folder triggers a webhook, which calls the Flask API to process the file. The result is then stored or further processed.

Getting Started
The entire pipeline is designed to be self-contained and can be run using a Jupyter notebook environment like Google Colab.

Prerequisites
Python 3.8+

pip package manager

Setup and Execution
The most straightforward way to run the project is by following the steps in the GenText.ipynb Jupyter notebook:

Clone the repository:
git clone https://github.com/Suhasbhat123/GenAI-Text-Processing-Pipeline.git
cd GenAI-Text-Processing-Pipeline

Open GenText.ipynb in a Jupyter-compatible environment (e.g., JupyterLab, VS Code, Google Colab).

Execute the cells in order. The notebook will automatically:

Install all necessary dependencies (flask, streamlit, transformers, pyngrok, etc.).

Define the entity extraction logic and data storage functions.

Start the Flask backend and Streamlit frontend in the background using pyngrok to create public URLs for access.

Create and process sample input files to demonstrate the pipeline's functionality.

Show the final contents of the SQLite database and CSV file.
