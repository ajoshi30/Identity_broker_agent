# AI Identity Broker for Autonomous Agents

> Enterprise-grade Zero Trust identity management platform for autonomous AI agents.

![Python](https://img.shields.io/badge/Python-3.11+-blue)
![React](https://img.shields.io/badge/React-18-61dafb)
![FastAPI](https://img.shields.io/badge/FastAPI-0.115-009688)
![MongoDB](https://img.shields.io/badge/MongoDB-7-47a248)
![Gemini](https://img.shields.io/badge/Gemini-1.5--Flash-4285f4)

## 🏗️ Architecture

```
User → AI Agent → Identity Broker → Policy Engine → Token Service → Protected Resource
                                                                    ↓
                                                         Monitoring + Audit Logs
                                                                    ↓
                                                          Gemini AI Insights
```

## 🚀 Quick Start

### Prerequisites
- Python 3.11+
- Node.js 18+
- MongoDB (local or Docker)

### 1. Start MongoDB

```bash
# Option A: Docker
docker run -d -p 27017:27017 --name mongodb mongo:7

# Option B: Local MongoDB (if already installed)
mongod
```

### 2. Backend Setup

```bash
cd backend

# Create virtual environment
python -m venv venv

# Activate (Windows)
.\venv\Scripts\activate

# Activate (Mac/Linux)
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Start server
uvicorn main:app --reload --port 8000
```

### 3. Frontend Setup

```bash
cd frontend

# Install dependencies
npm install

# Start dev server
npm run dev
```

### 4. Open the App
- **Frontend**: http://localhost:5173
- **Backend API docs**: http://localhost:8000/docs

## ⚙️ Environment Variables

Create a `.env` file in the project root:

```env
MONGO_URI=mongodb://localhost:27017
DB_NAME=identity_broker
GEMINI_API_KEY=your_key_here  # Optional - get from https://aistudio.google.com/
JWT_EXPIRY_MINUTES=30
AGENT_TOKEN_EXPIRY_MINUTES=5
```

## 📋 Features

| Feature | Description |
|---------|-------------|
| **User Auth** | JWT + RSA-256, Role-based access, MFA simulation |
| **Agent Management** | Register agents, assign scopes, track trust scores |
| **Identity Broker** | Central middleware validating all access requests |
| **Policy Engine** | RBAC + ABAC hybrid with deny-by-default |
| **Token Service** | Short-lived scoped JWTs with auto-expiry |
| **Lifecycle Manager** | Task state machine with auto-revocation |
| **Protected Resources** | Simulated banking, healthcare, ecommerce APIs |
| **Audit Logs** | Complete security event trail |
| **AI Insights** | Gemini-powered threat analysis and compliance |
| **Real-time Dashboard** | WebSocket-powered Mission Control |

## 🎯 Demo Flow

1. **Register** a user account
2. **Create** an AI agent with task scopes
3. **Submit** access request via the Broker Monitor
4. **Observe** policy evaluation (allowed/denied)
5. **View** issued token in Token Center
6. **Access** protected resources with the token
7. **Create** a task in Lifecycle Monitor
8. **Complete** the task → tokens auto-revoked
9. **Check** audit logs for full event trail
10. **Generate** AI threat summary in AI Insights

## 🛡️ Security Features

- RSA-256 JWT signing
- Replay attack detection (nonce tracking)
- Rate limiting
- Deny-by-default policy
- Automatic token expiration
- Trust score tracking
- Least privilege enforcement

## 📁 Project Structure

```
├── backend/
│   ├── main.py              # FastAPI entry point
│   ├── config.py            # Settings & RSA keys
│   ├── database.py          # MongoDB connection
│   ├── auth/                # Authentication module
│   ├── agents/              # Agent management
│   ├── broker/              # Identity Broker
│   ├── policy/              # Policy Engine
│   ├── tokens/              # Token Service
│   ├── lifecycle/           # Task Lifecycle
│   ├── monitoring/          # Dashboard metrics
│   ├── resources/           # Protected APIs
│   ├── audit/               # Audit logging
│   ├── ai_insights/         # Gemini integration
│   └── middleware/          # Security middleware
├── frontend/
│   └── src/
│       ├── pages/           # 12 application pages
│       ├── components/      # Reusable UI components
│       ├── api/             # Axios client
│       └── store/           # Zustand state
├── docker-compose.yml
└── .env.example
```

## 🎨 Tech Stack

**Frontend**: React 18, Vite, Tailwind CSS 4, Framer Motion, Recharts, React Three Fiber, Zustand

**Backend**: FastAPI, Motor (async MongoDB), PyJWT + RSA, Google Gemini API

**Security**: JWT RS256, RBAC+ABAC, Replay Detection, Rate Limiting
