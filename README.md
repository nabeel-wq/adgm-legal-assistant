ADGM Corporate Compliance Agent
Analyzes corporate documents against official ADGM regulations. This tool uses a hybrid approach: high-precision rules and an advanced AI (RAG) system. Highly recommended: Providing a valid OpenAI API key enables AI-verification for nuanced issues, relying on regex mode for ambiguous language may lead to several false positives. Made by me and ai assistants claude and gemini.

Overview
This project is an AI-powered agent designed to streamline the legal compliance process for businesses operating in the ADGM. It accepts corporate documents (.docx format), checks them against official ADGM regulations and templates, identifies missing documents for specific processes, and flags potential legal red flags and inconsistencies.

The agent uses a hybrid approach, combining high-precision, rule-based checks with an advanced AI model (powered by OpenAI and a FAISS vector database) to provide nuanced, context-aware analysis.

Key Features
Hybrid Analysis Engine:
Rules-Only Mode: Uses high-precision regular expressions to find clear-cut violations (e.g., incorrect jurisdiction).
Hybrid Mode (AI-Powered): Requires an OpenAI API key. This mode enables:
Retrieval-Augmented Generation (RAG): Analyzes document clauses against a knowledge base built from real ADGM legal documents for deep compliance checking.
AI-Verified Red Flags: Uses AI to validate ambiguous language (e.g., "may", "could") to reduce false positives and confirm if the phrasing poses a legal risk.
Document Checklist Verification:
Automatically detects the user's intended legal process (e.g., Company Incorporation) and verifies if all mandatory documents have been uploaded.
Inline DOCX Commenting:
Generates a reviewed version of the uploaded .docx file with red flags highlighted and contextual comments inserted directly into the document.
Structured Reporting:
Outputs a comprehensive JSON report and a .zip bundle containing all reviewed documents and a summary text file.
Web-Based UI:
Built with Gradio for an easy-to-use interface that requires no local frontend setup.
How It Works
Data Ingestion: The agent fetches official ADGM templates, checklists, and guidance documents from public URLs to build its knowledge base.
RAG Indexing: Using sentence-transformers and faiss, it creates a vector index of the ADGM legal documents for fast, semantic searching.
User Upload: The user uploads one or more .docx corporate documents via the Gradio interface.
Analysis:
Identifies the document types and the overall legal process.
Checks for missing documents based on predefined checklists.
Scans each document for red flags using both its regex rules and, if an API key is provided and valid, the RAG system.
Output Generation:
Summary of findings in the UI.
Downloadable .zip bundle containing the reviewed .docx files with inline comments.
Detailed JSON file for programmatic use.
Installation and Dependencies
Prerequisites
Python 3.8 or newer.
Access to a command line/terminal.
1. Clone the Repository
git clone https://github.com/2CentsCapitalHR/ai-engineer-task-nabeel-wq.git
cd ai-engineer-task-nabeel-wq
2. Create a Virtual Environment (Recommended)
# For macOS, Linux, and WSL
python3 -m venv venv
source venv/bin/activate

# For Windows (Command Prompt)
python -m venv venv
venv\Scripts\activate.bat

# For Windows (PowerShell)
python -m venv venv
venv\Scripts\Activate.ps1
3. Install Python Dependencies
Create a requirements.txt file with:

gradio
numpy
python-docx
spacy
sentence-transformers
openai
faiss-cpu
PyMuPDF
requests
Then run:

pip install -r requirements.txt
Download the SpaCy model:

python -m spacy download en_core_web_sm
4. Install System-Level Dependencies
Windows: Precompiled wheels for PyMuPDF and faiss-cpu should install without issue. If errors occur, install Microsoft C++ Build Tools.

macOS:

brew install libmagic
Linux (Debian/Ubuntu/WSL):

sudo apt-get update
sudo apt-get install -y libmagic1
Running the Application
Set Your API Key (Optional): To enable Hybrid Mode, enter a valid OpenAI API key in the UI.
Launch the Gradio App:
python adgm_agent.py
Access the Interface: Open the URL from the terminal, usually http://127.0.0.1:7860.
Usage
Enter API Key: Paste your OpenAI API key or leave blank for Rules-Only Mode.
Upload Documents: Drag and drop or click to upload .docx files.
Analyze: The tool starts automatically.
Review Results:
See high-level findings in the UI.
Download the Full JSON Report.
Download the Marked-up DOCX Bundle.
Check the 2 docx files and image for image of working ui and reviewed plus unreviewed docx

Disclaimer
This tool is for demonstration and guidance purposes only and is not a substitute for professional legal advice. Always consult with qualified legal counsel for any compliance matters.
