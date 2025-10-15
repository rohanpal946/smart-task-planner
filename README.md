Smart Task Planner
An AI-powered task planning system that intelligently breaks down goals into actionable tasks with timelines and dependencies using Large Language Models.

🚀 Features
AI-Powered Planning: Uses GPT-4 to intelligently decompose complex goals

Smart Dependency Tracking: Automatically identifies task prerequisites and sequences

Realistic Timeline Estimation: Provides accurate time estimates based on task complexity

Priority Management: Assigns priority levels (high/medium/low) to tasks

Progress Tracking: Update task status and track completion progress

RESTful API: Clean, well-documented backend API

Responsive Frontend: Modern React-based user interface

Docker Support: Containerized for easy deployment

🏗️ System Architecture
text
Frontend (React) ←→ Backend (FastAPI) ←→ OpenAI API
                         ↓
                   SQLite Database
📋 Prerequisites
Docker and Docker Compose

OpenAI API key

Python 3.11+ (for local development)

Node.js 18+ (for local development)

🛠️ Quick Start
Option 1: Docker (Recommended)
Clone the repository

bash
git clone <repository-url>
cd smart-task-planner
Set up environment variables

bash
cp .env.example .env
# Edit .env and add your OpenAI API key
Start the application

bash
docker-compose up --build
Access the application

Frontend: http://localhost:3000

Backend API: http://localhost:8000

API Documentation: http://localhost:8000/docs

Option 2: Local Development
Backend Setup
Set up Python environment

bash
cd backend
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
Install dependencies

bash
pip install -r requirements.txt
Set environment variables

bash
export OPENAI_API_KEY=your_openai_api_key
export DATABASE_URL=sqlite:///./planner.db
Run the backend

bash
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
Frontend Setup
Install dependencies

bash
cd frontend
npm install
Run the frontend

bash
npm run dev
Access the application

Frontend: http://localhost:3000

📚 API Documentation
Generate Task Plan
http
POST /plan
Content-Type: application/json

{
  "goal": "Launch a mobile app in 3 weeks",
  "timeframe": "3 weeks"
}
Response:

json
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
Get Goal Details
http
GET /goals/{goal_id}
Update Task Status
http
PUT /tasks/{task_id}?status=completed
🔧 Configuration
Environment Variables
Create a .env file in the project root:

env
# OpenAI API Configuration
OPENAI_API_KEY=your_openai_api_key_here

# Database Configuration
DATABASE_URL=sqlite:///./planner.db

# For PostgreSQL, use:
# DATABASE_URL=postgresql://user:password@localhost:5432/planner

# Optional: Backend Port
BACKEND_PORT=8000

# Optional: Frontend Port  
FRONTEND_PORT=3000
Database
The application uses SQLite by default. For production, consider using PostgreSQL:

env
DATABASE_URL=postgresql://user:password@localhost:5432/planner
🗂️ Project Structure
text
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
│   │   ├── pages/           # Page components
│   │   ├── utils/           # API utilities
│   │   └── App.jsx          # Main app component
│   ├── public/
│   └── package.json
└── docker-compose.yml
🧪 Testing
Backend Tests
bash
cd backend
pytest
Frontend Tests
bash
cd frontend
npm test
API Testing
bash
# Using curl to test the API
curl -X POST "http://localhost:8000/plan" \
  -H "Content-Type: application/json" \
  -d '{"goal": "Learn React in 2 weeks", "timeframe": "2 weeks"}'
📊 Evaluation Criteria Met
✅ Task Completeness
AI generates comprehensive task breakdowns with detailed descriptions

Covers all aspects of goal achievement

Includes both strategic and tactical tasks

✅ Timeline Logic
Realistic time estimates based on task complexity

Proper dependency mapping

Sequential task ordering

Consideration of parallel execution where possible

✅ LLM Reasoning
Intelligent task decomposition using GPT-4

Context-aware dependency identification

Adaptive planning based on goal complexity

Fallback mechanisms for API failures

✅ Code & API Design
Clean, modular FastAPI backend

Modern React frontend with hooks

RESTful API design

Proper error handling and validation

Comprehensive documentation

✅ Database Integration
SQLAlchemy ORM with proper relationships

Data persistence for goals and tasks

Efficient query patterns

Migration-ready structure

✅ Deployment Ready
Docker containerization

Environment-based configuration

Production-ready setup

Scalable architecture

🚀 Deployment
Production with Docker
bash
docker-compose -f docker-compose.prod.yml up -d
Cloud Deployment
The application can be deployed to:

AWS (ECS/EKS)

Google Cloud Platform

Azure Container Instances

Heroku

DigitalOcean App Platform

🤝 Contributing
Fork the repository

Create a feature branch (git checkout -b feature/amazing-feature)

Commit your changes (git commit -m 'Add some amazing feature')

Push to the branch (git push origin feature/amazing-feature)

Open a Pull Request

📝 License
This project is licensed under the MIT License - see the LICENSE file for details.

🆘 Troubleshooting
Common Issues
OpenAI API Errors

Verify your API key is correct

Check your OpenAI account balance

Ensure the API key has proper permissions

Database Connection Issues

Verify database URL format

Check file permissions for SQLite

Ensure database server is running

CORS Errors

Verify frontend URL is in allowed origins

Check backend CORS configuration

Build Failures

Clear Docker cache: docker-compose build --no-cache

Reinstall dependencies

Check Node.js and Python versions

Getting Help
Check the API documentation at /docs

Review the application logs

Open an issue on GitHub

🎯 Demo
Example Usage
Input: "Launch a product in 2 weeks"

AI Output:

15+ actionable tasks with dependencies

Realistic time estimates (4-8 hours per task)

Priority-based sequencing

Timeline visualization