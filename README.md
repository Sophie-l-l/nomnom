# NomNom — AI Therapy Chatbot

[![React](https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react&logoColor=white)](https://reactjs.org/)
[![Node.js](https://img.shields.io/badge/Node.js-Express-339933?style=for-the-badge&logo=node.js&logoColor=white)](https://nodejs.org/)
[![OpenAI](https://img.shields.io/badge/OpenAI-GPT--4o--mini-412991?style=for-the-badge&logo=openai&logoColor=white)](https://openai.com/)
[![LangChain](https://img.shields.io/badge/LangChain-0.3-1C3C3C?style=for-the-badge)](https://js.langchain.com/)
[![MongoDB](https://img.shields.io/badge/MongoDB-6.13-47A248?style=for-the-badge&logo=mongodb&logoColor=white)](https://www.mongodb.com/)

**NomNom** is an AI-powered therapy chatbot that provides compassionate, memory-aware conversational support through multi-turn dialogue. Built with LangChain + GPT-4o-mini for context-aware therapeutic responses and Clerk for user authentication.

**Demo Video:** [Watch on YouTube](https://youtu.be/ppIAHSyNp_8)

**Team:** Khatira Kazemi, Sophie Lin, Yanlin Wu, Phuc Nguyen

---

## Key Achievements

- **Situation**: Mental health support remains inaccessible for many — therapy sessions are expensive ($100–200/hr), waitlists are long, and stigma prevents help-seeking
- **Task**: Build an AI companion that provides empathetic, context-aware conversational support with persistent memory across sessions
- **Action**:
  - Integrated **LangChain's ConversationChain with BufferMemory** for multi-turn context retention — the bot remembers prior conversation context within each session
  - Designed a custom **therapeutic system prompt** emphasizing empathy, active listening, and non-judgmental support
  - Built a **React + Vite frontend** with real-time messaging UI, typewriter animation effects, and responsive design
  - Implemented **Clerk authentication** for secure user sessions with persistent login
  - Connected to **MongoDB** for data persistence and **Express** backend with CORS-enabled API
  - Developing a separate **AI Voice Agent prototype** ([voice-agent](https://github.com/PhucNguyen-rsc/voice-agent)) for future merge
- **Result**: Working prototype with real-time AI responses, conversation memory, and user authentication; demo video showcasing full functionality

---

## Features

### AI & Conversation
- **GPT-4o-mini powered** — Cost-optimized model for empathetic, concise responses
- **Memory-aware dialogue** — LangChain ConversationChain retains conversation context
- **Custom therapeutic prompt** — Emphasizes compassion, validation, and safe space creation
- **Real-time streaming** — Instant AI responses with loading indicators

### User Experience
- **Typewriter animation** — Messages appear with typing effect for natural feel
- **Auto-scroll** — Conversation view automatically follows latest messages
- **Responsive design** — Mobile-friendly chat interface with Tailwind CSS
- **User authentication** — Clerk-powered login/signup with persistent sessions

### Architecture
- **Client-server separation** — React frontend communicates with Express API
- **RESTful API** — POST `/answer` endpoint processes messages and returns AI responses
- **Environment-based config** — Separate `.env` files for client and backend secrets

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| **Frontend** | React 18, Vite 6.0, React Router DOM 7.1 |
| **Styling** | Tailwind CSS 4.0, react-simple-typewriter |
| **Auth** | Clerk (React SDK 5.22) |
| **Backend** | Node.js, Express 4.21 |
| **AI/LLM** | LangChain 0.3.15, OpenAI GPT-4o-mini |
| **Database** | MongoDB 6.13 |
| **Linting** | ESLint 9.19 |

---

## Architecture

```
nomnom/
├── client/                     # React frontend
│   ├── src/
│   │   ├── components/
│   │   │   └── chatPage/
│   │   │       └── chatPage.jsx        # Chat interface with message handling
│   │   ├── layouts/
│   │   │   ├── dashboardLayout.jsx     # Authenticated layout (Clerk)
│   │   │   └── root_layout/
│   │   │       └── rootLayout.jsx      # App shell with ClerkProvider
│   │   ├── routes/
│   │   │   ├── Homepage.jsx            # Landing page with typewriter
│   │   │   ├── dashboardPage.jsx       # User dashboard
│   │   │   ├── signinPage.jsx          # Clerk sign-in
│   │   │   └── signupPage.jsx          # Clerk sign-up
│   │   └── main.jsx                    # Router + entry point
│   ├── .env                            # VITE_CLERK_PUBLISHABLE_KEY, VITE_BACKEND_URL
│   └── package.json
├── backend/                    # Express API server
│   ├── index.mjs               # Express server + /answer endpoint
│   ├── openai.mjs              # LangChain + GPT-4o-mini conversation chain
│   ├── .env                    # OPENAI_API_KEY
│   └── package.json
└── README.md
```

---

## Getting Started

### Prerequisites
- Node.js 18+
- npm 8+
- [OpenAI API key](https://platform.openai.com/api-keys)
- [Clerk account](https://clerk.com/) (free tier available)

### Environment Setup

**Backend** (`backend/.env`):
```env
OPENAI_API_KEY=sk-your-openai-api-key
```

**Client** (`client/.env`):
```env
VITE_CLERK_PUBLISHABLE_KEY=pk_test_your-clerk-key
VITE_BACKEND_URL=http://localhost:3000
```

### Installation & Run

```bash
# Clone the repository
git clone https://github.com/Sophie-l-l/nomnom.git
cd nomnom

# Terminal 1 — Start backend
cd backend
npm install
node index.mjs

# Terminal 2 — Start frontend
cd client
npm install
npm run dev
```

The frontend will be available at `http://localhost:5173` and the backend API at `http://localhost:3000`.

---

## API Reference

### POST `/answer`

Sends a user message and receives an AI-generated therapeutic response.

**Request:**
```json
{
  "message": "I've been feeling anxious lately about work deadlines."
}
```

**Response:**
```json
{
  "response": "I hear you, and it makes complete sense that approaching deadlines would bring up feelings of anxiety..."
}
```

---

## Future Plans

- Merge with [AI Voice Agent](https://github.com/PhucNguyen-rsc/voice-agent) for voice-based interaction
- Add persistent conversation history across sessions via MongoDB
- Implement mood tracking and progress visualization

---

## Skills Demonstrated

LLM integration (LangChain + OpenAI), prompt engineering for therapeutic AI, full-stack development (React + Express), user authentication (Clerk), NoSQL databases (MongoDB), real-time messaging UI, team collaboration (4-person team)

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
