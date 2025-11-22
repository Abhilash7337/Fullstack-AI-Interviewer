# 🎯 Full-Stack AI Interviewer

A comprehensive AI-powered interview platform that conducts technical interviews, evaluates candidates in real-time, and provides detailed feedback and scoring. Built with modern technologies and AI integration for intelligent question generation and answer evaluation.

## 📋 Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Running the Application](#running-the-application)
- [Project Structure](#project-structure)
- [API Documentation](#api-documentation)
- [Contributing](#contributing)
- [License](#license)

## ✨ Features

### For Candidates (Interviewee)
- 📄 **Resume Upload**: Upload PDF or DOCX resumes for automatic parsing
- 🤖 **AI-Generated Questions**: Dynamic question generation based on resume and job requirements
- ⏱️ **Timed Responses**: Time-limited answers with automatic submission
- 💬 **Interactive Chat Interface**: Natural conversation flow during the interview
- 📊 **Real-time Evaluation**: Instant AI-powered answer scoring and feedback
- 🎓 **Detailed Results**: Comprehensive performance analysis with scores and recommendations

### For Interviewers (Dashboard)
- 👥 **Candidate Management**: View all interview candidates and their details
- 📈 **Performance Analytics**: Track scores, completion rates, and overall performance
- 🔍 **Interview Review**: Access detailed interview transcripts and evaluations
- 📋 **Filtering & Search**: Find candidates by status, score, or personal information
- 💾 **Data Persistence**: All interviews stored in MongoDB for future reference

### AI Capabilities
- **Multi-AI Support**: Integrated with Google Gemini, OpenAI, and HuggingFace
- **Intelligent Evaluation**: Context-aware answer scoring using advanced LLMs
- **Fallback Mechanisms**: Automatic fallback to alternative AI services or keyword-based scoring
- **Rate Limit Handling**: Smart retry logic with exponential backoff

## 🛠️ Tech Stack

### Frontend
- **React 19** - Modern UI library with hooks
- **Redux Toolkit** - State management with Redux reducer pattern
- **Redux Persist** - Persistent state across sessions
- **Ant Design (antd)** - Professional UI component library
- **Vite** - Fast build tool and development server
- **Axios** - HTTP client for API requests
- **PDF.js** - PDF document parsing
- **Mammoth.js** - DOCX document parsing

### Backend
- **Node.js** - JavaScript runtime
- **Express.js** - Web application framework
- **MongoDB** - NoSQL database
- **Mongoose** - MongoDB ODM
- **JWT** - Authentication (optional)
- **Helmet** - Security middleware
- **CORS** - Cross-origin resource sharing
- **Express Rate Limit** - API rate limiting

### AI Integration
- **Google Gemini API** - Primary AI service for evaluation
- **OpenAI API** - Secondary AI service (optional)
- **HuggingFace API** - Tertiary AI service (optional)

## 📦 Prerequisites

Before running this application, ensure you have the following installed:

- **Node.js** (v16 or higher)
- **npm** or **yarn**
- **MongoDB** (v4.4 or higher) - Local or MongoDB Atlas
- **Git**

## 🚀 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/Abhilash7337/Fullstack-AI-Interviewer.git
cd Fullstack-AI-Interviewer
```

### 2. Install Backend Dependencies

```bash
cd backend
npm install
```

### 3. Install Frontend Dependencies

```bash
cd ../frontend
npm install
```

## ⚙️ Configuration

### Backend Environment Variables

Create a `.env` file in the `backend` directory:

```bash
cd backend
cp .env.example .env
```

Edit `.env` with your configuration:

```env
# Server Configuration
NODE_ENV=development
PORT=3000

# Database
MONGODB_URI=mongodb://localhost:27017/swipe-interview

# Security
JWT_SECRET=your-super-secret-jwt-key-change-this-in-production

# CORS Configuration
FRONTEND_URL=http://localhost:5173

# Rate Limiting (optional)
RATE_LIMIT_WINDOW_MS=60000
RATE_LIMIT_MAX=1000

# Body Parser Limits (optional)
BODY_PARSER_LIMIT=10mb

# Frontend Build Path (for production)
FRONTEND_BUILD_PATH=../frontend/dist
```

### Frontend Environment Variables

Create a `.env` file in the `frontend` directory:

```bash
cd ../frontend
cp .env.example .env
```

Edit `.env` with your configuration:

```env
# API Configuration
VITE_API_URL=http://localhost:3000/api

# Google Gemini API Key (Free tier available)
# Get from: https://makersuite.google.com/app/apikey
VITE_GEMINI_API_KEY=your_gemini_api_key_here

# OpenAI API Key (OPTIONAL - requires credits)
VITE_OPENAI_API_KEY=your_openai_api_key_here

# HuggingFace API Key (OPTIONAL - free tier available)
# Get from: https://huggingface.co/settings/tokens
VITE_HUGGINGFACE_API_KEY=your_huggingface_api_key_here

# HuggingFace Configuration
VITE_HUGGINGFACE_MODEL_URL=https://api-inference.huggingface.co/models/gpt2

# Gemini Configuration
VITE_GEMINI_BASE_URL=https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash-exp:generateContent
```

### ⚠️ Important Note About API Keys

**GEMINI API KEY REQUIREMENT:**
- The **free tier** of Google Gemini API has strict rate limits (15 requests per minute)
- For production use or heavy testing, you should:
  - **Upgrade to a paid tier** for higher rate limits
  - **Apply for increased quotas** through Google Cloud Console
  - **Implement request queuing** to stay within limits
  - **Use multiple API keys** for load distribution

**Recommended Actions:**
1. Start with the free tier for development and testing
2. Monitor your API usage in Google Cloud Console
3. Upgrade to pay-as-you-go billing when ready for production
4. Consider implementing caching to reduce API calls

## 🏃 Running the Application

### Development Mode

#### 1. Start MongoDB

Make sure MongoDB is running on your system:

```bash
# macOS (using Homebrew)
brew services start mongodb-community

# Linux
sudo systemctl start mongod

# Windows
net start MongoDB
```

Or use MongoDB Atlas (cloud) by updating the `MONGODB_URI` in your `.env` file.

#### 2. Start Backend Server

```bash
cd backend
npm run dev
```

Backend will run on `http://localhost:3000`

#### 3. Start Frontend Development Server

In a new terminal:

```bash
cd frontend
npm run dev
```

Frontend will run on `http://localhost:5173`

#### 4. Access the Application

Open your browser and navigate to:
- **Frontend**: http://localhost:5173
- **Backend API**: http://localhost:3000/api
- **Health Check**: http://localhost:3000/api/health

### Production Mode

#### 1. Build Frontend

```bash
cd frontend
npm run build
```

#### 2. Run Backend (serves both frontend and API)

```bash
cd backend
NODE_ENV=production npm start
```

Access the application at `http://localhost:3000`

## 📁 Project Structure

```
Fullstack-AI-Interviewer/
├── backend/
│   ├── middleware/
│   │   └── auth.js                 # Authentication middleware
│   ├── models/
│   │   ├── User.js                 # User schema
│   │   ├── Interview.js            # Interview schema
│   │   └── UnfinishedInterview.js  # In-progress interview schema
│   ├── routes/
│   │   ├── auth.js                 # Authentication routes
│   │   ├── users.js                # User management routes
│   │   └── interviews.js           # Interview CRUD routes
│   ├── .env.example                # Example environment variables
│   ├── package.json                # Backend dependencies
│   └── server.js                   # Express server entry point
│
├── frontend/
│   ├── src/
│   │   ├── cmp/
│   │   │   ├── Chat/
│   │   │   │   ├── ChatInput.jsx           # Chat input component
│   │   │   │   ├── ChatMessages.jsx        # Message display
│   │   │   │   ├── DataCollectionChat.jsx  # Resume upload flow
│   │   │   │   ├── InterviewChat.jsx       # Interview Q&A flow
│   │   │   │   ├── InterviewEngine.js      # AI evaluation logic
│   │   │   │   ├── InterviewResults.jsx    # Results display
│   │   │   │   └── ResumeUpload.jsx        # Resume upload UI
│   │   │   └── Dash/
│   │   │       └── CandidateDetailModal.jsx # Candidate details
│   │   ├── feat/
│   │   │   ├── cand.js             # Candidate Redux slice
│   │   │   ├── dashboard.js        # Dashboard Redux slice
│   │   │   ├── intr.js             # Interview Redux slice
│   │   │   └── session.js          # Session Redux slice
│   │   ├── pages/
│   │   │   ├── Chat.jsx            # Candidate interview page
│   │   │   └── Dash.jsx            # Interviewer dashboard page
│   │   ├── services/
│   │   │   └── apiService.js       # API client
│   │   ├── util/
│   │   │   ├── documentExtraction.js # Document parsing
│   │   │   ├── indexedDbService.js   # IndexedDB operations
│   │   │   └── pdfExtraction.js      # PDF parsing
│   │   ├── App.jsx                 # Root component
│   │   ├── main.jsx                # React entry point
│   │   └── store.js                # Redux store configuration
│   ├── .env.example                # Example frontend env vars
│   ├── package.json                # Frontend dependencies
│   └── vite.config.js              # Vite configuration
│
├── .gitignore                      # Git ignore rules
├── SETUP_AND_FIXES.md             # Setup guide and troubleshooting
└── README.md                       # This file
```

## 🔌 API Documentation

### Base URL
```
http://localhost:3000/api
```

### Authentication Routes

#### Register User
```http
POST /api/auth/register
Content-Type: application/json

{
  "name": "John Doe",
  "email": "john@example.com",
  "phone": "+1234567890",
  "resumeData": {
    "text": "Resume content...",
    "fileType": "pdf"
  }
}
```

#### Login User
```http
POST /api/auth/login
Content-Type: application/json

{
  "email": "john@example.com"
}
```

### Interview Routes

#### Create Interview
```http
POST /api/interviews/create
Content-Type: application/json

{
  "email": "john@example.com",
  "candidateInfo": {
    "name": "John Doe",
    "email": "john@example.com",
    "phone": "+1234567890",
    "resumeText": "Resume content..."
  }
}
```

#### Get Unfinished Interview
```http
GET /api/interviews/unfinished/:email
```

#### Update Interview Question
```http
PUT /api/interviews/:interviewId/question
Content-Type: application/json

{
  "questionData": {
    "id": 1,
    "question": "What is React?",
    "answer": "React is a JavaScript library...",
    "score": 85,
    "timeTaken": 120,
    "feedback": "Good answer!"
  }
}
```

#### Complete Interview
```http
POST /api/interviews/:interviewId/complete
Content-Type: application/json

{
  "allAnswers": [...]
}
```

#### Get All Interviews
```http
GET /api/interviews?status=all&sortBy=createdAt&sortOrder=desc&search=
```

## 🎨 Redux State Management

The application uses **Redux Toolkit** with multiple slices:

### Slices
- **`cand`** - Candidate information and resume data
- **`dashboard`** - Dashboard state and filters
- **`intr`** - Interview questions and progress
- **`session`** - User session and authentication

### Redux Persist
State is persisted to localStorage for seamless user experience across page refreshes.

## 🎭 Ant Design Components Used

- **Layout**: Tabs, Card, Space, Divider
- **Forms**: Input, Button, Upload, Form
- **Data Display**: Table, Tag, Progress, Statistic, Avatar
- **Feedback**: Message, Modal, Spin, Alert
- **Navigation**: Menu, Pagination

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the ISC License.

## 🐛 Troubleshooting

### Port Already in Use
If you get an error about port 3000 or 5173 being in use:
```bash
# Find and kill the process
lsof -ti:3000 | xargs kill -9
lsof -ti:5173 | xargs kill -9
```

### MongoDB Connection Error
- Ensure MongoDB is running
- Check the `MONGODB_URI` in your `.env` file
- For MongoDB Atlas, ensure your IP is whitelisted

### API Rate Limit Errors
- The Gemini API free tier has limits
- Wait a few minutes between requests
- Consider upgrading to a paid tier
- Check the console for retry attempts

### Build Errors
```bash
# Clear node_modules and reinstall
rm -rf node_modules package-lock.json
npm install
```

## 📧 Contact

**Abhilash Podisetty**
- GitHub: [@Abhilash7337](https://github.com/Abhilash7337)
- Repository: [Fullstack-AI-Interviewer](https://github.com/Abhilash7337/Fullstack-AI-Interviewer)

---

**Built with ❤️ using React, Redux, Node.js, MongoDB, and AI**
