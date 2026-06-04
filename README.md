# WIPO IP Protection Platform
## Overview

The WIPO IP Protection Platform is a comprehensive web-based solution that enables creators, startups, and innovators to protect their intellectual property through digital timestamping using SHA-256 hashing, blockchain verification for immutable ownership records, automated infringement detection, and AI-powered similarity search.

This project was developed as a final-year BSc IT (Security and Network Engineering) project and is submitted for WIPO internship consideration.

## Features

| Feature                | Technology       | Description                           |
|------------------------|----------------- |---------------------------------------|
|  JWT Authentication    | SimpleJWT       | Secure user login and registration     |
| SHA-256 Hashing        | hashlib         | Cryptographic file fingerprinting      |
|  Blockchain Ledger     | Custom Python   | Immutable proof-of-work timestamping   |
|  AI-Powered Search     | Scikit-learn    | TF-IDF similarity search for prior art |
| Infringement Alerts    | Hash Matching   | Automatic duplicate detection          |
| React Dashboard        | Vite + Tailwind | Modern, responsive GitHub-style UI     |
| Cloud Deployment       | Microsoft Azure | Production-ready hosting               |


## Tech Stack
### Backend
1. Django 
2. Django REST Framework 
3. SimpleJWT 
4. Scikit-learn 
5. SQLite 

### Frontend
1. React 
2. Vite 
3. TailwindCSS 
4. Axios 
5. React Router DOM 

### DevOps
1. Git 
2. Azure App Service 
3. Azure Storage 

### Backend Setup
# Clone the repository
git clone https://github.com/Arielle-Milan/wipo-ip-platform.git 
cd wipo-ip-platform/backend

# Create virtual environment
python -m venv venv
source venv/bin/activate      # Linux/Mac
# venv\Scripts\activate        # Windows

# Install dependencies
pip install -r requirements.txt

# Run migrations
python manage.py makemigrations
python manage.py migrate

# Create superuser
python manage.py createsuperuser

# Start server
python manage.py runserver


### Frontend Setup
# Open new terminal
cd wipo-ip-platform/frontend

# Install dependencies
npm install

# Start development server
npm run dev


### Access the Application
| Service | URL |
|---------|-----|
| Frontend | http://localhost:5173 |
| Backend API | http://localhost:8000 |
| Admin Panel | http://localhost:8000/admin |

##  API Documentation
### Authentication Endpoints

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| POST | `/api/auth/register/` | Register new user | None |
| POST | `/api/auth/login/` | Login | None |
| POST | `/api/auth/refresh/` | Refresh token | Refresh |
| GET | `/api/auth/profile/` | Get profile | JWT |

### Works Endpoints

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| POST | `/api/works/upload/` | Upload IP work | JWT |
| GET | `/api/works/dashboard/` | Dashboard stats | JWT |
| GET | `/api/works/search/?q=query` | AI search | JWT |

### Example API Calls

# Register
curl -X POST http://localhost:8000/api/auth/register/ \
  -H "Content-Type: application/json" \
  -d '{"email":"test@example.com","username":"test","password":"Test123!","password2":"Test123!"}'

# Login
curl -X POST http://localhost:8000/api/auth/login/ \
  -H "Content-Type: application/json" \
  -d '{"email":"test@example.com","password":"Test123!"}'

# Search (use token from login)
curl -X GET "http://localhost:8000/api/works/search/?q=blockchain+patent" \
  -H "Authorization: Bearer YOUR_TOKEN"


## Testing
cd backend
python manage.py test apps --verbosity=2


##  Live Demo
The application is deployed on Microsoft Azure:
1. **Frontend**: https://wipofrontend.z13.web.core.windows.net 
2. **Backend API**: https://wipo-ip-platform.azurewebsites.net 
3. **Admin Panel**: https://wipo-ip-platform.azurewebsites.net/admin 
