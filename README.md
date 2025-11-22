# 🎯 Full-Stack AI Interviewer

A comprehensive AI-powered interview platform that conducts technical interviews, evaluates candidates in real-time, and provides detailed feedback and scoring. Built with modern technologies and AI integration for intelligent question generation and answer evaluation.

## ✨ Features

### For Candidates (Interviewee)
- 📄 **Resume Upload** - Upload PDF or DOCX resumes for automatic parsing
- 🤖 **AI-Generated Questions** - Dynamic question generation based on resume and job requirements
- ⏱️ **Timed Responses** - Time-limited answers with automatic submission
- 💬 **Interactive Chat Interface** - Natural conversation flow during the interview
- 📊 **Real-time Evaluation** - Instant AI-powered answer scoring and feedback
- 🎓 **Detailed Results** - Comprehensive performance analysis with scores and recommendations

### For Interviewers (Dashboard)
- 👥 **Candidate Management** - View all interview candidates and their details
- 📈 **Performance Analytics** - Track scores, completion rates, and overall performance
- 🔍 **Interview Review** - Access detailed interview transcripts and evaluations
- 📋 **Filtering & Search** - Find candidates by status, score, or personal information
- 💾 **Data Persistence** - All interviews stored in MongoDB for future reference

### AI Capabilities
- **Multi-AI Support** - Integrated with Google Gemini, OpenAI, and HuggingFace
- **Intelligent Evaluation** - Context-aware answer scoring using advanced LLMs
- **Fallback Mechanisms** - Automatic fallback to alternative AI services or keyword-based scoring
- **Rate Limit Handling** - Smart retry logic with exponential backoff

## 🛠️ Tech Stack

### Frontend
- **React 19** - Modern UI library with hooks
- **Redux Toolkit** - State management with Redux reducer pattern
- **Redux Persist** - Persistent state across sessions
- **Ant Design (antd)** - Professional UI component library
- **Vite** - Fast build tool and development server
- **Axios** - HTTP client for API requests
- **PDF.js & Mammoth.js** - Document parsing

### Backend
- **Node.js & Express.js** - Server runtime and web framework
- **MongoDB & Mongoose** - NoSQL database and ODM
- **JWT** - Authentication
- **Helmet** - Security middleware
- **CORS** - Cross-origin resource sharing
- **Express Rate Limit** - API rate limiting

### AI Integration
- **Google Gemini API** - Primary AI service for evaluation
- **OpenAI API** - Secondary AI service (optional)
- **HuggingFace API** - Tertiary AI service (optional)

## 🎨 Key Libraries & Patterns

### State Management
- **Redux Toolkit** - Modern Redux with simplified configuration
- **Redux Reducers** - Organized state slices:
  - `cand` - Candidate information and resume data
  - `dashboard` - Dashboard state and filters
  - `intr` - Interview questions and progress
  - `session` - User session and authentication
- **Redux Persist** - Automatic state persistence to localStorage

### UI Components (Ant Design)
- **Layout** - Tabs, Card, Space, Divider
- **Forms** - Input, Button, Upload, Form
- **Data Display** - Table, Tag, Progress, Statistic, Avatar
- **Feedback** - Message, Modal, Spin, Alert
- **Navigation** - Menu, Pagination

## ⚠️ Important Note About API Keys

**The Google Gemini API free tier has strict rate limits (15 requests per minute).**

For production use or extensive testing:
- **Upgrade to a paid tier** for higher rate limits and better performance
- **Apply for increased quotas** through Google Cloud Console
- **Monitor usage** to avoid service interruptions
- Consider implementing **request queuing** or **caching** to optimize API calls

*It's recommended to upgrade from the free tier before deploying to production.*

## 📦 Prerequisites

- **Node.js** (v16 or higher)
- **MongoDB** (local installation or MongoDB Atlas)
- **Git**
- **API Keys** (Google Gemini required, OpenAI/HuggingFace optional)

## 🚀 Quick Start

1. **Clone the repository**
   ```bash
   git clone https://github.com/Abhilash7337/Fullstack-AI-Interviewer.git
   cd Fullstack-AI-Interviewer
   ```

2. **Install dependencies**
   ```bash
   # Backend
   cd backend
   npm install
   
   # Frontend
   cd ../frontend
   npm install
   ```

3. **Configure environment variables**
   - Copy `.env.example` to `.env` in both `backend` and `frontend` folders
   - Add your MongoDB connection string
   - Add your API keys (Gemini, OpenAI, HuggingFace)

4. **Start the application**
   ```bash
   # Terminal 1 - Backend
   cd backend
   npm run dev
   
   # Terminal 2 - Frontend
   cd frontend
   npm run dev
   ```

5. **Access the application**
   - Frontend: http://localhost:5173
   - Backend API: http://localhost:3000/api

## 📁 Project Structure

```
Fullstack-AI-Interviewer/
├── backend/
│   ├── middleware/        # Authentication & authorization
│   ├── models/           # MongoDB schemas (User, Interview, UnfinishedInterview)
│   ├── routes/           # API routes (auth, users, interviews)
│   └── server.js         # Express server entry point
│
├── frontend/
│   ├── src/
│   │   ├── cmp/          # React components (Chat, Dashboard)
│   │   ├── feat/         # Redux slices (reducers)
│   │   ├── pages/        # Main pages (Chat, Dash)
│   │   ├── services/     # API client
│   │   ├── util/         # Utilities (document parsing, IndexedDB)
│   │   ├── App.jsx       # Root component
│   │   └── store.js      # Redux store configuration
│   └── vite.config.js    # Vite configuration
│
└── README.md             # This file
```

## 🤝 Contributing

Contributions are welcome! Please:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the ISC License.

## 📧 Contact

**Abhilash Podisetty**
- GitHub: [@Abhilash7337](https://github.com/Abhilash7337)
- Repository: [Fullstack-AI-Interviewer](https://github.com/Abhilash7337/Fullstack-AI-Interviewer)

---

**Built with ❤️ using React, Redux, Ant Design, Node.js, MongoDB, and AI**
