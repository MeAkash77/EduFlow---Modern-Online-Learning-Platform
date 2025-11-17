# EduFlow - Modern Online Learning Platform

<div align="center">
  <img src="client/public/favicon.svg" alt="EduFlow Logo" width="180"/>
  <h3>Learn Anywhere, Anytime</h3>
  
  ![Tech Stack](https://skillicons.dev/icons?i=react,ts,nodejs,mongodb,express,tailwind,firebase)
</div>

---

## Overview

EduFlow is a comprehensive full-stack e-learning platform built with the MERN stack (MongoDB, Express, React, Node.js). It delivers a modern learning experience with an intuitive interface, interactive courses, and powerful administrative tools.

<div align="center">
  <img src="client/public/placeholder.png" alt="EduFlow Platform Screenshot" width="800"/>
  <p><i>Transform your learning journey with EduFlow's interactive experience</i></p>
</div>

---

## Key Features

### Authentication & Authorization
- **Multiple Login Methods**: Email/password and Google OAuth integration
- **Role-Based Access Control**: Separate admin and student portals with appropriate permissions
- **Secure Sessions**: JWT-based authentication with "Remember Me" functionality
- **Streamlined Onboarding**: Quick and intuitive signup process

### Course Management
- **Intuitive Course Catalog**: Browse, search, and filter courses with ease
- **Admin Dashboard**: Comprehensive course creation and management tools
- **Rich Content Support**: Video lectures, documents, and interactive quizzes
- **Analytics Dashboard**: Detailed course performance metrics with visual representations

### Student Experience
- **Personalized Dashboard**: Track enrolled courses and monitor progress
- **Interactive Learning**: Video playback, quiz attempts, and progress tracking
- **Achievement System**: Earn certificates upon course completion
- **Course Bookmarking**: Save courses for later viewing
- **Responsive Design**: Optimized for all devices and screen sizes

### Certificate System
- **Automatic Generation**: PDF certificates generated upon course completion
- **Verification Portal**: Public certificate authenticity verification
- **Professional Templates**: Customizable certificate designs
- **Social Sharing**: Easy sharing to LinkedIn and other professional networks

### User Profile Management
- **Customizable Profiles**: Update personal information and preferences
- **Avatar Management**: Upload and manage profile pictures
- **Learning Statistics**: Visual representation of learning progress and achievements
- **Settings Panel**: Manage notifications and account preferences

### AI Assistant
- **24/7 Support**: Intelligent chatbot for course recommendations and assistance
- **Contextual Help**: Location-aware assistance throughout the platform
- **Voice Capability**: Optional voice interaction mode
- **Personalized Recommendations**: Smart suggestions based on learning history

---

## Tech Stack

### Frontend
![Frontend Stack](https://skillicons.dev/icons?i=react,ts,tailwind,vite,firebase)

- React 18 with TypeScript for type-safe development
- Tailwind CSS for utility-first styling
- React Router for client-side routing
- shadcn/ui component library
- jsPDF and html2canvas for certificate generation
- Firebase Authentication for Google OAuth

### Backend
![Backend Stack](https://skillicons.dev/icons?i=nodejs,express,mongodb)

- Node.js with Express framework
- MongoDB with Mongoose ODM
- JWT for authentication and authorization
- Express Validator for request validation
- Multer for file upload handling
- RESTful API architecture

---

## Getting Started

### Prerequisites
- Node.js (v14 or higher)
- MongoDB (local installation or MongoDB Atlas account)
- Firebase account for authentication setup
- npm or yarn package manager

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/MeAkash77/EduFlow---Modern-Online-Learning-Platform.git
   cd eduflow
   ```

2. **Install dependencies**
   ```bash
   npm run install-all
   ```

3. **Configure environment variables**
   
   Create a `.env` file in the server directory:
   ```env
   PORT=5000
   MONGODB_URI=your_mongodb_connection_string
   JWT_SECRET=your_jwt_secret
   CLIENT_URL=http://localhost:5173
   FIREBASE_PROJECT_ID=your_firebase_project_id
   FIREBASE_PRIVATE_KEY=your_firebase_private_key
   FIREBASE_CLIENT_EMAIL=your_firebase_client_email
   ```
   
   Create `.env.development` in the client directory:
   ```env
   VITE_API_URL=http://localhost:5000/api
   VITE_FIREBASE_API_KEY=your_firebase_api_key
   VITE_FIREBASE_AUTH_DOMAIN=your_firebase_auth_domain
   VITE_FIREBASE_PROJECT_ID=your_firebase_project_id
   VITE_FIREBASE_STORAGE_BUCKET=your_firebase_storage_bucket
   VITE_FIREBASE_APP_ID=your_firebase_app_id
   ```

4. **Run the application**
   ```bash
   # Development mode (runs both client and server)
   npm run dev
   
   # Run client only
   npm run client
   
   # Run server only
   npm run server
   ```

5. **Access the application**
   - Frontend: http://localhost:5173
   - Backend API: http://localhost:5000

---

## Deployment

### Deploying to Render

EduFlow is optimized for deployment to [Render](https://render.com) as a single Web Service.

#### Step 1: Set Up MongoDB Atlas

1. Create a free account at [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. Create a new cluster
3. Configure database access with username and password
4. Whitelist IP addresses (use `0.0.0.0/0` for Render)
5. Obtain your connection string

#### Step 2: Prepare Repository

```bash
git add .
git commit -m "Prepare for deployment"
git push origin main
```

#### Step 3: Configure Render

1. Sign up at [Render](https://render.com)
2. Click "New" → "Web Service"
3. Connect your GitHub repository
4. Configure the service:
   - **Name**: `eduflow` (or your preferred name)
   - **Environment**: `Node`
   - **Build Command**: `bash ./render-build.sh`
   - **Start Command**: `NODE_ENV=production npm start`
   - **Auto-Deploy**: Enable

#### Step 4: Set Environment Variables

Add the following environment variables in Render:

```
NODE_ENV=production
MONGODB_URI=your_mongodb_atlas_connection_string
JWT_SECRET=your_secure_jwt_secret
RENDER=true
FIREBASE_PROJECT_ID=your_firebase_project_id
FIREBASE_PRIVATE_KEY=your_firebase_private_key
FIREBASE_CLIENT_EMAIL=your_firebase_client_email
```

#### Step 5: Deploy

Render will automatically build and deploy your application. Access it at the provided URL once deployment completes.

---

## Troubleshooting

### Connection Issues

#### Error: `ERR_CONNECTION_REFUSED` or `Error fetching courses`

**Solution 1: Clear Browser State**
```javascript
// Run in browser console (F12)
localStorage.clear();
sessionStorage.clear();
location.reload(true);
```

**Solution 2: Verify API Configuration**
- Check that `client/src/lib/api.ts` uses the correct API URL
- Production builds should use relative paths (`/api`)
- Verify environment variables are properly set

**Solution 3: Run Diagnostics**
```bash
node diagnose-connection.js
```

### Production Deployment Issues

#### API Connection Errors on Render

1. **Check Render Logs**: Review server logs in the Render dashboard
2. **Inspect Network Requests**: Use browser DevTools to verify API endpoints
3. **Force Clean Deployment**:
   ```bash
   git add .
   git commit -m "Fix API connection issues"
   git push origin main
   ```
4. **Verify Environment Variables**: Ensure all required variables are set in Render

---

## Project Structure

```
eduflow/
├── client/                 # React frontend
│   ├── public/            # Static assets
│   ├── src/
│   │   ├── components/    # React components
│   │   ├── lib/          # Utility functions
│   │   ├── pages/        # Page components
│   │   └── types/        # TypeScript types
│   └── package.json
├── server/                # Express backend
│   ├── controllers/       # Route controllers
│   ├── models/           # Mongoose models
│   ├── routes/           # API routes
│   ├── middleware/       # Custom middleware
│   └── package.json
├── render-build.sh       # Render build script
└── package.json          # Root package.json
```

---

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## License

This project is licensed under the MIT License. See the LICENSE file for details.

---

## Support

For issues, questions, or suggestions:
- Open an issue on GitHub
- Contact the development team
- Check the documentation

---

<div align="center">
  <p>Built with passion using</p>
  
  ![Tech Stack](https://skillicons.dev/icons?i=react,ts,nodejs,mongodb,express,tailwind)
  
  <p><strong>Made by the EduFlow Team</strong></p>
</div>
