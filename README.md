# Product Intelligence AI 📋⚡

An autonomous customer telemetry and market diagnostics engine. This platform scrapes unstructured discussions across public web nodes (YouTube comments, HackerNews threads, forums), classifies customer sentiment with transformer-based NLP, isolates product failure vectors, and compiles actionable executive briefings using high-throughput open-weights LLMs.

Designed for product teams, strategy leads, and founders who need real customer signal without marketing noise.

---

## 🏗 System Architecture

```text
[Public Review Sources] (YouTube, HackerNews, Forums)
           │
           ▼
[Ingestion & Deduplication] (Normalization + MD5 Fingerprinting)
           │
           ▼
[Storage & Caching] (Local Analysis JSON / MongoDB Cache)
           │
           ▼
[Inference Pipeline]
  ├── Polarity Classification: PyTorch + cardiffnlp/twitter-roberta-base-sentiment-latest
  └── Topic & Defect Extraction: scikit-learn TF-IDF N-Gram Vectorization
           │
           ▼
[Strategic Synthesis Engine]
  └── Groq LPU Inference (openai/gpt-oss-20b or qwen/qwen3.8-27b)
      Strict schema enforcement: Summary, Moats, Failure Vectors, Turnaround Actions
           │
           ▼
[Executive Briefing Surface]
  ├── Streamlit Binder UI (Responsive anchor navigation, stacked telemetry, micro-surfaces)
  └── Multi-Page ReportLab PDF Engine (Paginated executive audit download)
✨ Key Features
Transformer-Grade Sentiment Classification: Evaluates public reviews using RoBERTa fine-tuned on social context, categorizing signal into positive, neutral, and negative metrics.

Substantive Feature Extraction: Identifies concrete product attributes, thermal states, workflow bottlenecks, and pricing grievances using n-gram frequency rather than broad labels.

Anti-Meta Strategic Synthesis: Enforces strict prompt boundaries on Groq LLM inference to ensure turnaround advice addresses the product itself (engineering, onboarding, positioning, and roadmap moats)—excluding internal pipeline noise.

Editorial Binder Interface: A distraction-free UI featuring smooth tab navigation (#tab-overview, #tab-voice, #tab-findings, #tab-actions) and clear data hierarchy.

Automated PDF Audit Generation: Compiles an executive-ready, multi-page briefing document on the fly using ReportLab with custom typography and clean pagination.

🚀 Getting Started
1. Prerequisites
Python 3.10+

A Groq Cloud API Key (Get one here)

2. Installation
Clone the repository and set up your virtual environment:

Bash
git clone [https://github.com/YOUR_USERNAME/product-intelligence-ai.git](https://github.com/YOUR_USERNAME/product-intelligence-ai.git)
cd product-intelligence-ai

# Create and activate virtual environment
python3 -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
(If you don't have a requirements.txt yet, run pip install streamlit plotly reportlab python-dotenv groq pandas torch transformers scikit-learn and then pip freeze > requirements.txt)

3. Environment Configuration
Create a .env file in the root directory:

Code snippet
GROQ_API_KEY=your_groq_api_key_here
4. Running the Application
Launch the Streamlit executive briefing console:

Bash
streamlit run dashboard/dashboard.py
Enter any target product (e.g., iPhone 15, Linear, Notion) and click Run audit.

📁 Repository Structure
Plaintext
├── dashboard/
│   └── dashboard.py          # Streamlit UI with Binder theme, Plotly charts, and PDF generator
├── data/                     # Cached JSON analysis files per audited product
├── insights/
│   └── insight_generator.py  # Groq API integration, JSON schema enforcement, and prompt logic
├── reports/                  # Formatted text summaries generated per product run
├── scraper/                  # Multi-source web scrapers (YouTube, HackerNews, etc.)
├── main.py                   # Central pipeline orchestration script
├── .gitignore                # Environment, build, and bytecode exclusions
├── README.md
└── requirements.txt
📄 Output Artifacts
Running an audit generates two persisted assets for each analyzed entity:

data/<product>_analysis.json: Raw telemetry, sentiment distribution, and structured JSON LLM dossier.

reports/<product>_product_report.txt: Formatted plain-text intelligence dossier.

Live Downloadable PDF: High-fidelity executive memo generated directly from the dashboard.

🛡 Security & Privacy
Sensitive credentials (.env) and local cache folders are ignored by Git.

Pipeline execution strips external platform metadata to focus reports strictly on product engineering and market positioning.
