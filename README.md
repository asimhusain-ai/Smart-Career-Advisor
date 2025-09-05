Smart Career Advisor
A modern web application that helps users discover their ideal career path based on their skills, experience, and aspirations.


Features
Resume Parsing – Upload and parse PDF resumes to extract skills and experience.

Skill Detection – AI-powered skill detection and normalization.

Role Matching – Intelligent role matching based on skills, experience, and education.

Visual Analytics – Interactive charts showing skill importance and gaps.

Modern UI – Dark theme with smooth animations and responsive design.


Tech Stack
Frontend
React 18 with Hooks
TailwindCSS for styling
Framer Motion for animations
Recharts for data visualization
React Router for navigation


Backend
FastAPI (Python) with Uvicorn server
PyPDF2 for PDF parsing
OpenAI API for skill detection
Pydantic for data validation


Quick Start
Prerequisites
Node.js 18+ and npm
Python 3.11+
OpenAI API key


Installation

Clone the repository
git clone <repository-url>
cd smart-career-advisor


Set up the backend

cd backend
python -m venv venv
# Activate virtual environment
# Linux / Mac: source venv/bin/activate
# Windows: venv\Scripts\activate
pip install -r requirements.txt

Configure environment variables
cp .env.example .env
# Edit .env and add your OPENAI_API_KEY


Set up the frontend

cd ../frontend
npm install

Running the Application
Backend
cd backend
uvicorn app.main:app --reload

Frontend
cd frontend
npm start

Open http://localhost:3000
 in your browser

Docker Deployment
docker-compose up --build

Frontend: http://localhost:3000
Backend API: http://localhost:8000


API Endpoints
Endpoint	        Method  	Description
/api/degrees	    GET     	Get list of degree options
/api/parse-resume	POST	    Parse PDF resume and extract text
/api/detect-skills	POST	    Detect skills from resume text
/api/role-fit	    POST	    Calculate role fit based on profile and skills


Testing
cd backend
pytest tests/


Example Test Data

<!-- Experienced Python developer with 3 years of experience in data science and machine learning. 
Proficient in Pandas, NumPy, Scikit-learn, and TensorFlow.
Strong background in statistics and data visualization.
Worked on multiple ML projects including predictive modeling and natural language processing. -->

Expected Detected Skills: Python, Machine Learning, Pandas, TensorFlow, Statistics, Data Visualization

Algorithm
Role fit score calculation:
<!-- skill_score = weighted_sum(min(user_level / required_level, 1) * weight) / sum(weights)
experience_score = clamp(years_experience / (min_years_experience + 1), 0, 1)
education_score = 1 if exact match, 0.5 if related, 0 otherwise
final_fit = 0.66 * skill_score + 0.20 * experience_score + 0.14 * education_score -->

Security
<!-- API keys are stored server-side only
File uploads are validated for type and size
CORS is configured for frontend origins only
Input validation using Pydantic models -->


Contributing
<!-- Fork the repository
Create a feature branch
Make your changes
Add tests for new functionality
Submit a pull request -->


License
<!-- This project is licensed under the MIT License. -->


Sample Test Commands
<!-- Test Degrees Endpoint
curl -X GET "http://localhost:8000/api/degrees" -->

Test Resume Parsing
<!-- curl -X POST "http://localhost:8000/api/parse-resume" \
  -H "Content-Type: multipart/form-data" \
  -F "file=@sample_resume.pdf" -->

Test Skill Detection
<!-- curl -X POST "http://localhost:8000/api/detect-skills" \
  -H "Content-Type: application/json" \
  -d '{
    "profile": {
      "name": "John Doe",
      "age": 30,
      "years_of_experience": 5,
      "interest_areas": ["AI", "Machine Learning"],
      "education": "BS Computer Science"
    },
    "resume_text": "Experienced Python developer with machine learning expertise. Proficient in TensorFlow and PyTorch.",
    "ui_settings": {}
  }' -->

Test Role Fit Calculation
<!-- curl -X POST "http://localhost:8000/api/role-fit" \
  -H "Content-Type: application/json" \
  -d '{
    "profile": {
      "name": "Asim Husain",
      "age": 21,
      "years_of_experience": 1,
      "interest_areas": ["AI", "Machine Learning"],
      "education": "BS Computer Science"
    },
    "skills": [
      {"name": "Python", "level": 8},
      {"name": "Machine Learning", "level": 7},
      {"name": "TensorFlow", "level": 6}
    ],
    "top_n": 3
  }' -->