# EtharaAI
A modern, professional full-stack team task management application with polished UI, dark mode, and seamless Railway deployment.

Live Features:

✨ Modern glassmorphism UI with smooth animations
🌙 Light/Dark theme with persistent storage
👁️ Password visibility toggle on auth forms
🔐 JWT-based authentication with role-based access
📊 Real-time dashboard with task analytics
🎯 Project and task management system
📱 Fully responsive design
🚀 Single-service Railway deployment
Tech Stack
Frontend
React 19 + Vite (lightning-fast build)
Tailwind CSS with modern gradients and animations
Framer Motion for smooth micro-interactions
Axios for API communication
React Router v7 for navigation
Backend
Node.js + Express 5
MongoDB with Mongoose ODM
JWT for authentication
bcryptjs for password hashing
express-validator for input validation
Folder Structure
EtharaAI/
├─ backend/
│  ├─ src/
│  │  ├─ config/          (MongoDB connection)
│  │  ├─ controllers/     (Business logic)
│  │  ├─ middleware/      (Auth, validation, error handling)
│  │  ├─ models/          (User, Project, Task schemas)
│  │  ├─ routes/          (API endpoints)
│  │  ├─ validations/     (Input validation rules)
│  │  ├─ utils/           (JWT token generation)
│  │  ├─ app.js           (Express app with static serving)
│  │  └─ server.js        (Server startup)
│  ├─ .env.example        (Environment template)
│  └─ package.json
├─ frontend/
│  ├─ src/
│  │  ├─ api/             (Axios client configuration)
│  │  ├─ assets/          (Images, icons)
│  │  ├─ components/      (Layout, StatCard, ProtectedRoute)
│  │  ├─ context/         (AuthContext, ThemeContext)
│  │  ├─ pages/           (Login, Signup, Dashboard, Projects, Tasks)
│  │  ├─ App.jsx
│  │  ├─ App.css
│  │  ├─ main.jsx
│  │  └─ index.css        (Global styles + dark mode)
│  ├─ public/             (Static assets)
│  ├─ index.html          (HTML entry point)
│  ├─ vite.config.js      (Vite build config)
│  ├─ eslint.config.js    (ESLint rules)
│  ├─ .env.example        (Environment template)
│  └─ package.json
├─ .gitignore
├─ package.json           (Root monorepo orchestration)
├─ package-lock.json
└─ README.md
Features
🎨 Modern UI/UX
Professional glassmorphism design with gradient accents
Smooth page transitions and micro-interactions
Responsive grid layouts for all screen sizes
Light & Dark theme support
Password visibility toggle (Show/Hide) on login/signup
🔐 Authentication & Security
Secure signup/login with JWT tokens
Password hashing with bcryptjs
Token persistence in localStorage
Protected routes with automatic redirects
Role-based access control (Admin/Member)
👥 Role-Based Access Control
Admin: Create projects, manage members, create tasks, assign to team
Member: View assigned tasks, update status, view projects
📁 Project Management
Create projects with description
Add/remove team members
View all projects and member lists
Project overview and analytics
✅ Task Management
Create tasks under projects
Assign to team members
Update task status (pending, in progress, completed)
View overdue tasks
Filter by status
📊 Dashboard Analytics
Total tasks count
Completed tasks tracker
Pending tasks alert
Overdue tasks indicator
Quick action cards
Backend API Routes
Auth (/api/auth)
POST /signup - Create new account
POST /login - Login with email & password
GET /me - Get current user profile
Users (/api/users)
GET / - List all users (admin only)
Projects (/api/projects)
GET / - Get user's projects
POST / - Create new project (admin)
PATCH /:projectId/members - Add member (admin)
DELETE /:projectId/members/:userId - Remove member (admin)
Tasks (/api/tasks)
POST /projects/:projectId - Create task (admin)
GET /projects/:projectId - Get project tasks
PATCH /:taskId/status - Update task status
Dashboard (/api/dashboard)
GET /stats - Get dashboard statistics
Local Setup
Prerequisites
Node.js v16+
MongoDB (local or Atlas)
npm or yarn
Step 1: Install Dependencies
# From root directory
npm install
# This installs both backend and frontend dependencies
Step 2: Configure Environment Variables
Backend (.env)

cd backend
cp .env.example .env
# Edit .env with your values
Add to backend/.env:

PORT=5000
MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/dbname
JWT_SECRET=your_super_secret_key_here
NODE_ENV=development
Frontend (.env)

cd ../frontend
cp .env.example .env
Add to frontend/.env:

VITE_API_URL=/api
Step 3: Build Frontend
cd frontend
npm run build
# Creates optimized dist folder
Step 4: Start Backend
cd backend
npm start
# Backend runs on http://localhost:5000
# Frontend is served at http://localhost:5000
Open your browser at http://localhost:5000

Railway Single-Service Deployment
This setup deploys as a single service with the backend serving the built frontend.

Configuration in Railway
Connect Repository

Select GitHub repo (EtharaAI-assessment-)
Grant railway access
Service Settings

Root Directory: Leave empty (deploy from repo root)
Build Command: Automatic (uses root package.json)
Start Command: cd backend && npm start
Environment Variables

PORT - (Railway provides automatically)
MONGODB_URI - MongoDB connection string
JWT_SECRET - Your JWT secret key
NODE_ENV - production
Deploy

Railway will:
Run npm install (installs backend & frontend)
Run npm run build (builds frontend to dist)
Run npm start (starts backend, which serves frontend)
Access Your App

Visit the Railway deployment URL
Frontend loads from /
APIs available at /api/*
How It Works
The root package.json orchestrates the entire process:

npm install - Installs dependencies in both directories
npm run build - Builds the Vite frontend
npm start - Starts the backend server
Backend's app.js serves static files from frontend/dist
All requests to non-API routes are redirected to index.html (SPA)
Development Workflow
Frontend Development
cd frontend
npm run dev
# Hot reload on http://localhost:5173
Backend Development
cd backend
npm run dev
# Uses nodemon for auto-restart on file changes
Build for Production
# From root
npm run build
# Creates optimized production build
Theme Switcher
Click the ☀️ Light / 🌙 Dark button in the header to toggle theme. Your preference is saved automatically to localStorage.

Password Visibility Toggle
On login and signup pages, use the Show/Hide button next to the password field to toggle visibility for easier entry.

Key Features Breakdown
🎯 Authentication Flow
User signs up → password hashed → JWT token created
Login validates credentials → returns token
Token stored in localStorage
Protected routes check token validity
Logout clears token
🔒 Role-Based Authorization
Middleware checks user role before allowing actions
Admin can manage projects and members
Members can only view/update assigned tasks
📊 Real-Time Dashboard
Loads task statistics on page load
Displays total, completed, pending, and overdue tasks
Shows quick action cards for common operations
🎨 Modern UI System
Gradient backgrounds and text
Glassmorphism effects with backdrop blur
Smooth animations via Framer Motion
Responsive Tailwind grid system
Color-coded status indicators
