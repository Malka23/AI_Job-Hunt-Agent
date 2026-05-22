# 🤖 AI Job Hunt Agent

![Python](https://img.shields.io/badge/Python-3.10+-blue?style=flat-square&logo=python)
![Streamlit](https://img.shields.io/badge/Streamlit-UI-FF4B4B?style=flat-square&logo=streamlit)
![Ollama](https://img.shields.io/badge/Ollama-LLM-black?style=flat-square)
![Selenium](https://img.shields.io/badge/Selenium-Automation-43B02A?style=flat-square&logo=selenium)
![SQLite](https://img.shields.io/badge/SQLite-Database-003B57?style=flat-square&logo=sqlite)
![Docker](https://img.shields.io/badge/Docker-Compose-2496ED?style=flat-square&logo=docker)

> An end-to-end agentic AI system that **searches jobs, scores your resume, rewrites it for each role, auto-applies, and learns from rejections** — all from a single Streamlit dashboard.

---

## 🧠 About the Project

Job hunting is broken. Candidates spend hours manually searching across LinkedIn, Indeed, Naukri, and Internshala — tailoring resumes, writing cover letters, filling forms — only to get rejected by ATS before a human ever reads their application.

**AI Job Hunt Agent** automates the entire pipeline:

- Scrapes jobs across 4 platforms simultaneously
- Scores your resume against each job using ATS keyword matching
- Rewrites your resume and generates a cover letter using a local LLM (Ollama)
- Auto-fills and submits job applications using Selenium
- Tracks every application and surfaces weekly feedback insights

---

## ✨ Features

| Module | What It Does |
|--------|-------------|
| 🔍 **Job Search** | Async scraping across LinkedIn, Indeed, Naukri, Internshala |
| 📄 **Resume Management** | Upload PDF, extract text, store multiple versions |
| 🎯 **ATS Scoring** | Keyword match score, missing keywords, improvement tips |
| ✍️ **Resume Rewriting** | LLM tailors resume + generates cover letter per job |
| 📝 **PDF Generation** | Exports polished resume/cover letter as downloadable PDF |
| ❓ **Screening Q&A** | Extracts screening questions and generates LLM answers |
| 🖱️ **Auto-Apply** | Selenium fills forms, uploads resume, submits application |
| 📊 **Application Tracking** | Tracks status: Pending → Sent → Rejected → Interview |
| 📈 **Feedback & Analytics** | Weekly metrics — applied, rejected, interviews, avg ATS score |
| 🤖 **Full Agent Pipeline** | One-click: search → score → shortlist → rewrite → apply |

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|------------|
| Frontend | Streamlit |
| Backend | Python, Asyncio |
| AI / LLM | Ollama (local), OpenAI API (optional) |
| ATS Scoring | Keyword matching engine |
| Scraping | Jobspy, BeautifulSoup, Selenium |
| Automation | Selenium (autofill + form submission) |
| PDF | ReportLab (generation), PyPDF (parsing) |
| Database | SQLite + SQLAlchemy |
| Data | Pandas |
| Infrastructure | Docker Compose |

---

## 📁 Project Structure

```
AI_JOBHUNTAGENT/
│
├── app/
│   ├── agent/           # LangChain ReAct agent logic
│   ├── db/              # SQLAlchemy models
│   ├── routers/         # API route handlers
│   ├── scoring/         # ATS scoring engine
│   ├── scrapers/        # Platform-specific scrapers
│   ├── services/        # Resume rewrite, cover letter, Q&A
│   ├── tools/           # Agent tools (search, score, apply, log)
│   ├── llm.py           # LLM interface (Ollama / OpenAI)
│   └── __init__.py
│
├── config/
│   ├── settings.py      # App configuration
│   └── .env.example     # Environment variable template
│
├── outputs/             # Generated resumes & cover letters
├── final.py             # Full pipeline runner
├── main.ipynb           # Development & testing notebook
├── user_profile.json    # User profile config
├── docker-compose.yml
├── requirements.txt
└── README.md
```

---

## ⚙️ Full Agent Pipeline

```
User Profile + Resume Upload
          ↓
Async Job Scraping (LinkedIn / Indeed / Naukri / Internshala)
          ↓
SQLite Storage → ATS Scoring Engine
          ↓
Filter by Score, Keywords, Blacklist
          ↓
LLM Resume Rewriting (Ollama) + Cover Letter Generation
          ↓
Screening Q&A Generation
          ↓
Selenium Auto-Apply (Form Fill + Upload + Submit)
          ↓
Application Logged → Weekly Feedback Dashboard
```

---

## 🗄️ Database Schema

```
jobs          → id, title, company, location, description, match_score, status, source, url
resumes       → id, version, resume_text, cover_letter, is_base, target_role, created_at
applications  → id, job_id, status, applied_to, outcome_notes, applied_at
feedback      → week_number, jobs_scraped, jobs_applied, rejections, interviews, avg_match_score
```

---

## 🚀 Getting Started

### Prerequisites
- Python 3.10+
- [Ollama](https://ollama.ai) installed locally
- Chrome + ChromeDriver (for Selenium)
- Docker (optional, for PostgreSQL + Redis)

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/yourusername/AI_JobHuntAgent.git
cd AI_JobHuntAgent

# 2. Set up environment variables
cp config/.env.example .env
# Fill in your API keys and credentials

# 3. Install dependencies
pip install -r requirements.txt

# 4. Pull Ollama model
ollama pull llama3

# 5. Run the app
streamlit run app/main.py
```

---

## 🖥️ Usage

1. **Set up your profile** — fill in `user_profile.json` with your skills, target roles, and preferences
2. **Upload your base resume** (PDF) via the Resume Management tab
3. **Run Job Search** — select platforms and keywords, let the scraper run
4. **Review ATS Scores** — see which jobs match your profile best
5. **Rewrite & Apply** — let the agent rewrite your resume and auto-apply to shortlisted jobs
6. **Track Progress** — monitor application statuses and weekly feedback analytics

---

## ⚠️ Known Limitations

- Selenium automation may break if job platform UIs change
- Requires Ollama running locally for LLM features
- Credential storage is local — not production-secure
- Scraping depends on external libraries; rate limits may apply

---

## 🔮 Future Enhancements

- ☁️ Cloud deployment (AWS / GCP)
- 🔐 Secure authentication system
- 🧠 Semantic ATS matching (vector embeddings)
- 🔗 Official API integrations instead of scraping
- 📊 Enhanced analytics dashboard

---

## 🙋‍♂️ Author

**Malka Naaz**
- GitHub: [@Malka23](https://github.com/Malka23)
- LinkedIn: [LinkedIn](https://www.linkedin.com/in/malka-naaz-870338145)

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

⭐ **If you found this project helpful, please give it a star!**
