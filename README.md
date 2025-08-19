# Multi-Agent AI System for Job Screening

A complete Python system with multiple agents working together to enhance the job screening process.

## 🌟 Features

- **Job Description Summarizer Agent**: Parses JDs into structured data
- **CV Extractor Agent**: Extracts key information from PDF resumes
- **Matching Agent**: Uses embeddings to calculate match scores
- **Shortlisting Agent**: Automatically selects candidates with scores ≥ 80%
- **Interview Scheduler Agent**: Generates personalized interview emails
- **SQLite Memory Persistence**: Stores all data for future reference
- **Streamlit UI**: User-friendly interface for easy interaction

## 🗂️ Project Structure

```
project/
├── main.py                 # Main entry point
├── app.py                  # Streamlit UI
├── agents/                 # Agent modules
│   ├── jd_summarizer.py    # Parse and summarize job descriptions
│   ├── cv_extractor.py     # Extract structured data from resumes
│   ├── matcher.py          # Match JDs with CVs using embeddings
│   ├── shortlister.py      # Shortlist candidates based on score
│   └── emailer.py          # Send interview invitation emails
├── utils/                  # Utility modules
│   ├── embeddings.py       # Embedding generation and similarity
│   ├── parser.py           # Text parsing utilities
│   └── diagram.py          # Agent interaction diagram generator
├── db/                     # Database module
│   └── memory.py           # SQLite memory persistence
├── resumes/                # Resume PDF files
│   └── *.pdf               # Example resumes
├── job_description.csv     # Example job descriptions
└── README.md               # Project documentation
```

## 🚀 Installation

1. Clone the repository:
   ```bash
   git clone rep
   
   ```

2. Create a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Set up Ollama:
   ```bash
   # Install Ollama from https://ollama.ai/
   # Pull the required model
   ollama pull nomic-embed-text
   ```

## 📊 Usage

Run the entire pipeline:

```bash
python main.py
```

Run the Streamlit UI:

```bash
streamlit run app.py
```

d)

## 🖥️ Streamlit UI

The Streamlit UI provides a user-friendly interface for interacting with the job screening system:

- **Home**: Overview and full pipeline execution
- **Job Descriptions**: Process and view job descriptions
- **Resumes**: Process and view resume data
- **Matching**: Run and view candidate matching results
- **Shortlisting**: View and manage shortlisted candidates
- **Emails**: Send and track interview invitations
- **Database**: Explore the SQLite database
- **About**: System information and architecture

To launch the UI:

```bash
streamlit run app.py
```

## 🤖 How It Works

1. **JD Summarizer Agent**:
   - Parses job descriptions from CSV file
   - Extracts structured data using Ollama or rule-based extraction
   - Stores in SQLite database

2. **CV Extractor Agent**:
   - Reads PDF resumes using PyMuPDF
   - Extracts name, email, phone, education, work experience, skills, etc.
   - Stores parsed data in database

3. **Matching Agent**:
   - Creates embeddings for JDs and CVs using Ollama's nomic-embed-text model
   - Calculates cosine similarity to get match scores
   - Stores scores in database

4. **Shortlisting Agent**:
   - Filters candidates with scores above threshold (default: 80%)
   - Generates shortlist for each job
   - Stores shortlisted candidates in database

5. **Interview Scheduler Agent**:
   - Generates personalized emails for shortlisted candidates
   - Highlights matched skills from the candidate's resume
   - Simulates or sends emails using SMTP

6. **Database Module**:
   - Stores all data for persistence across runs
   - Enables querying and reporting

## 📝 Dependencies

- `ollama`: For embedding generation
- `pymupdf`: For PDF parsing
- `numpy`, `scikit-learn`: For vector operations and similarity calculation
- `matplotlib`, `networkx`: For diagram generation 
- `sqlite3`: For database operations
- `streamlit`, `pandas`: For UI and data visualization

## 📋 Requirements

```
numpy>=2.0.0
scikit-learn>=1.6.0
matplotlib>=3.8.0
pandas>=2.1.1
networkx>=3.2.1
ollama>=0.4.7
streamlit>=1.27.2
pymupdf>=1.23.22
```

## 📊 Agent Interaction Diagram

```mermaid
graph TD
    A[JD Summarizer Agent] -->|Passes JD summaries| C[Matching Agent]
    B[CV Extractor Agent] -->|Passes parsed CVs| C
    C -->|Passes match scores| D[Shortlisting Agent]
    D -->|Passes shortlisted candidates| E[Interview Scheduler Agent]
    
    classDef agent fill:#f9f,stroke:#333,stroke-width:2px;
    class A,B,C,D,E agent;
```

