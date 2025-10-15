Here’s a polished **README.md** version of your Smart Task Planner project, properly formatted for GitHub with clear structure, Markdown styling, and emoji sections 👇

---

# 🧠 Smart Task Planner

An **AI-powered task planning system** that intelligently breaks down goals into actionable tasks with timelines, dependencies, and priorities using **Large Language Models (LLMs)**.

---

## 🚀 Features

✅ **AI-Powered Planning** – Uses GPT-4 to intelligently decompose complex goals
✅ **Smart Dependency Tracking** – Automatically identifies task prerequisites and sequences
✅ **Realistic Timeline Estimation** – Provides accurate time estimates based on task complexity
✅ **Priority Management** – Assigns priority levels (High / Medium / Low)
✅ **Progress Tracking** – Update task status and visualize progress
✅ **RESTful API** – Clean, well-documented backend API
✅ **Responsive Frontend** – Modern React-based user interface
✅ **Docker Support** – Containerized for easy deployment

---

## 🏗️ System Architecture

```
Frontend (React) ←→ Backend (FastAPI) ←→ OpenAI API
                         ↓
                   SQLite / PostgreSQL Database
```

---

## 📋 Prerequisites

* **Docker** and **Docker Compose**
* **OpenAI API key**
* **Python 3.11+** (for local development)
* **Node.js 18+** (for local development)

---

## 🛠️ Quick Start

### **Option 1: Docker (Recommended)**

```bash
git clone <repository-url>
cd smart-task-planner
```

**Set up environment variables**

```bash
cp .env.example .env
# Edit .env and add your OpenAI API key
```

**Start the application**

```bash
docker-compose up --build
```

**Access the application**

* Frontend → [http://localhost:3000](http://localhost:3000)
* Backend API → [http://localhost:8000](http://localhost:8000)
* API Docs → [http://localhost:8000/docs](http://localhost:8000/docs)

---

### **Option 2: Local Development**

#### **Backend Setup**

```bash
cd backend
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

**Set environment variables**

```bash
export OPENAI_API_KEY=your_openai_api_key
export DATABASE_URL=sqlite:///./planner.db
```

**Run the backend**

```bash
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```

#### **Frontend Setup**

```bash
cd frontend
npm install
npm run dev
```

**Access:** [http://localhost:3000](http://localhost:3000)

---

## 📚 API Documentation

### **Generate Task Plan**

**POST** `/plan`

**Request:**

```json
{
  "goal": "Launch a mobile app in 3 weeks",
  "timeframe": "3 weeks"
}
```

**Response:**

```json
{
  "goal_id": "uuid",
  "tasks": [
    {
      "id": "uuid",
      "title": "Define app requirements",
      "description": "List core features and user stories",
      "estimated_duration_hours": 8,
      "dependencies": [],
      "priority": "high",
      "order": 1,
      "status": "pending"
    }
  ],
  "timeline_summary": "Overall timeline description"
}
```

### **Get Goal Details**

**GET** `/goals/{goal_id}`

### **Update Task Status**

**PUT** `/tasks/{task_id}?status=completed`

---

## 🔧 Configuration

### **Environment Variables**

Create a `.env` file in the project root:

```env
# OpenAI API Configuration
OPENAI_API_KEY=your_openai_api_key_here

# Database Configuration
DATABASE_URL=sqlite:///./planner.db

# For PostgreSQL
# DATABASE_URL=postgresql://user:password@localhost:5432/planner

# Optional: Ports
BACKEND_PORT=8000
FRONTEND_PORT=3000
```

### **Database**

Default: **SQLite**
Production: **PostgreSQL**

Example:

```env
DATABASE_URL=postgresql://user:password@localhost:5432/planner
```

---

## 🗂️ Project Structure

```
smart-task-planner/
├── backend/
│   ├── app/
│   │   ├── main.py           # FastAPI application
│   │   ├── models.py         # SQLAlchemy models
│   │   ├── schemas.py        # Pydantic schemas
│   │   ├── llm_service.py    # OpenAI integration
│   │   └── database.py       # Database configuration
│   ├── requirements.txt
│   └── Dockerfile
├── frontend/
│   ├── src/
│   │   ├── components/       # React components
│   │   ├── pages/            # Page components
│   │   ├── utils/            # API utilities
│   │   └── App.jsx           # Main app component
│   ├── public/
│   └── package.json
└── docker-compose.yml
```

---

## 🧪 Testing

**Backend Tests**

```bash
cd backend
pytest
```

**Frontend Tests**

```bash
cd frontend
npm test
```

**API Testing**

```bash
curl -X POST "http://localhost:8000/plan" \
  -H "Content-Type: application/json" \
  -d '{"goal": "Learn React in 2 weeks", "timeframe": "2 weeks"}'
```

---

## 📊 Evaluation Criteria Met

✅ **Task Completeness**

* AI generates comprehensive, multi-level task breakdowns
* Covers strategic and tactical aspects of goals

✅ **Timeline Logic**

* Realistic time estimates
* Proper dependency mapping and sequential ordering

✅ **LLM Reasoning**

* Intelligent GPT-4-based decomposition
* Context-aware planning
* API failure fallback

✅ **Code & API Design**

* Modular FastAPI backend
* Modern React frontend
* RESTful endpoints with error handling

✅ **Database Integration**

* SQLAlchemy ORM
* Persistent storage for goals and tasks

✅ **Deployment Ready**

* Dockerized architecture
* Configurable for production
* Scalable setup

---

## 🚀 Deployment

**Production (Docker):**

```bash
docker-compose -f docker-compose.prod.yml up -d
```

**Supported Cloud Platforms:**

* AWS (ECS / EKS)
* Google Cloud Platform
* Azure Container Instances
* Heroku
* DigitalOcean App Platform

---

## 🤝 Contributing

1. **Fork** the repository
2. **Create a feature branch**

   ```bash
   git checkout -b feature/amazing-feature
   ```
3. **Commit changes**

   ```bash
   git commit -m 'Add some amazing feature'
   ```
4. **Push to branch**

   ```bash
   git push origin feature/amazing-feature
   ```
5. **Open a Pull Request**

---

## 📝 License

This project is licensed under the **MIT License** – see the [LICENSE](LICENSE) file for details.

---

## 🆘 Troubleshooting

**OpenAI API Errors**

* Verify your API key
* Check account balance
* Ensure correct permissions

**Database Issues**

* Verify database URL
* Check file permissions
* Ensure DB server is running

**CORS Errors**

* Verify allowed origins
* Check backend CORS setup

**Build Failures**

* Clear Docker cache
* Reinstall dependencies
* Check Node.js and Python versions

---

## 🎯 Demo

### Example Usage

**Input:**

> “Launch a product in 2 weeks”

**AI Output:**

* 15+ actionable tasks
* Realistic time estimates (4–8 hours each)
* Prioritized sequence
* Timeline visualization

---
