# 🏛️ CivicIQ – AI Civic Learning Platform for Gen Z
**Team IQ | V.S.B Engineering College, Karur**
*Members: Nithishkumar S · Risanth S · Sanjay R · Nilavarasan N · Naveen N · Jagathish N*

---

## 📁 Project Structure

```
civiciq/
├── frontend/               ← React.js + Vite (Port 3000)
│   ├── src/
│   │   ├── pages/
│   │   │   ├── HomePage.jsx          ← Landing page with all features
│   │   │   ├── TutorPage.jsx         ← AI Civic Tutor chat
│   │   │   ├── NewsPage.jsx          ← Simplified political news
│   │   │   ├── QuizPage.jsx          ← Real-time quiz bot
│   │   │   ├── PollPage.jsx          ← Civic poll system
│   │   │   └── PolicySimPage.jsx     ← Policy simulation
│   │   ├── services/api.js           ← Axios API calls
│   │   ├── context/AuthContext.jsx   ← JWT auth state
│   │   └── App.jsx                   ← React Router + Navbar
│   ├── Dockerfile
│   └── nginx.conf
│
├── backend/                ← Java 17 + Spring Boot 3 (Port 8080)
│   └── src/main/java/com/civiciq/
│       ├── model/                    ← JPA Entities (User, Poll, Quiz, Bill...)
│       ├── repository/               ← Spring Data JPA repos
│       ├── controller/               ← REST API controllers
│       │   ├── AuthController.java   ← /api/auth (register, login)
│       │   ├── NewsController.java   ← /api/news
│       │   ├── PollController.java   ← /api/polls + voting
│       │   ├── QuizController.java   ← /api/quizzes
│       │   └── BillController.java   ← /api/bills
│       ├── security/                 ← JWT filter + JwtUtil
│       └── config/SecurityConfig.java← CORS + Auth rules
│
├── ai-service/             ← Python FastAPI (Port 5000)
│   └── main.py
│       ├── POST /api/tutor/ask       ← NLP Civic Tutor (NLTK + Sarvam AI)
│       ├── POST /api/news/summarize  ← Extractive text summarizer
│       ├── GET  /api/news/fetch      ← Live NewsAPI fetch
│       ├── POST /api/quiz/generate   ← AI quiz generator
│       ├── POST /api/policy/simulate ← Policy impact simulator
│       ├── POST /api/bills/explain   ← Bill explainer
│       └── POST /api/translate       ← Sarvam AI translation
│
├── database/
│   └── schema.sql          ← Full MySQL schema + seed data (14 tables)
│
└── deployment/
    ├── docker-compose.yml  ← Runs all 4 services together
    └── .env.example        ← API key template
```

---

## 🚀 Quick Start (Docker – Recommended)

```bash
# 1. Clone and navigate
cd civiciq/deployment

# 2. Set up environment variables
cp .env.example .env
# Edit .env → add your NewsAPI key (free at newsapi.org) and Sarvam AI key

# 3. Start everything
docker-compose up --build

# 4. Open in browser
# Frontend:    http://localhost:3000
# Backend API: http://localhost:8080/api
# AI Service:  http://localhost:5000/docs  (Swagger UI)
# Database:    localhost:3306
```

---

## 🛠️ Manual Setup (Development)

### Database
```sql
mysql -u root -p < database/schema.sql
```

### Backend (Spring Boot)
```bash
cd backend
./mvnw spring-boot:run
# Runs at http://localhost:8080
```

### AI Service (Python)
```bash
cd ai-service
pip install -r requirements.txt
python main.py
# Runs at http://localhost:5000
# Swagger docs at http://localhost:5000/docs
```

### Frontend (React)
```bash
cd frontend
npm install
npm run dev
# Runs at http://localhost:3000
```

---

## 🔌 API Reference

### Backend REST API (Spring Boot :8080)
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /api/auth/register | Create account |
| POST | /api/auth/login | Login → JWT token |
| GET | /api/news | Get news (paginated) |
| GET | /api/polls | Get active polls |
| POST | /api/polls/{id}/vote | Cast vote |
| GET | /api/polls/{id}/results | View poll results |
| GET | /api/quizzes | List quizzes |
| GET | /api/bills | List recent bills |

### AI Service (FastAPI :5000)
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /api/tutor/ask | Ask AI Civic Tutor |
| GET | /api/news/fetch | Fetch live news |
| POST | /api/news/summarize | Summarize text |
| POST | /api/quiz/generate | Generate quiz |
| POST | /api/policy/simulate | Simulate policy impact |
| POST | /api/bills/explain | Explain a bill |
| POST | /api/translate | Translate via Sarvam AI |

---

## 🗄️ Database Schema (14 Tables)

| Table | Purpose |
|-------|---------|
| users | Students, Educators, Admins with XP/streaks |
| civic_topics | Curated civics knowledge base |
| news_articles | Verified news with AI summaries |
| tutor_sessions | AI Tutor chat sessions |
| tutor_messages | Individual chat messages |
| quizzes | Quiz collections |
| quiz_questions | MCQ questions with explanations |
| quiz_attempts | User quiz scores |
| polls | Civic engagement polls |
| poll_options | Poll answer choices |
| poll_votes | User votes (1 per user per poll) |
| policy_scenarios | Policy simulation scenarios |
| policy_options | Policy choices with impact scores |
| policy_simulations | User simulation runs |
| bills | Passed parliament bills + AI summaries |
| lessons | Educator-created content |
| user_progress | XP, levels, badges |

---

## 🧠 Technology Stack

| Layer | Technology | Purpose |
|-------|-----------|---------|
| **Frontend** | React.js + Vite | Interactive SPA |
| | React Router | Client-side routing |
| | Axios | HTTP client |
| | Chart.js | Data visualization |
| **Backend** | Java 17 + Spring Boot 3 | REST API server |
| | Spring Security + JWT | Authentication |
| | Spring Data JPA | ORM / Database |
| | Hibernate | MySQL mapping |
| **AI/NLP** | Python + FastAPI | AI microservice |
| | NLTK | Text processing & summarization |
| | Sarvam AI API | 22+ Indian language translation |
| | NewsAPI | Verified real-time news |
| **Database** | MySQL 8 | Primary data store |
| **Deployment** | Docker + Compose | Containerization |
| | Nginx | Reverse proxy + static files |

---

## 📚 Data Sources
- **data.gov.in** – Government open data
- **eci.gov.in** – Election Commission of India
- **prsindia.org** – Bills, Laws, Parliament data
- **newsapi.org** – Real-time verified news
- **nltk.org** – NLP text processing
- **sarvam.ai** – Indian multilingual AI

---

## 🏆 Key USPs vs Existing Platforms

| Feature | CivicIQ | Traditional Platforms |
|---------|---------|----------------------|
| AI Tutor in 22+ Indian languages | ✅ | ❌ |
| Real-time verified news summary | ✅ | ❌ |
| Policy impact simulation | ✅ | ❌ |
| AI quiz generation from news | ✅ | ❌ |
| Civic poll with analytics | ✅ | ❌ |
| Bill explainer (plain language) | ✅ | ❌ |
| Gen Z-focused UX | ✅ | ❌ |
