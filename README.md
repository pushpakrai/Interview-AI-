# Interview-AI

> **🤖 AI-Powered Interview Preparation Tool**
Full-stack application that generates **AI-driven interview reports** and **tailored resumes** from a candidate’s resume/self-description and a target job description.

---

## 📂 Project Structure

- **`Backend/`** – Express.js API leveraging **Google GenAI** for report generation and **Puppeteer** for PDF rendering.
- **`Frontend/`** – React + Vite single-page application for user interaction.

---

## ✨ Core Features

- **🔐 User Authentication** – Secure register/login/logout with JWT cookies.
- **📄 Resume Input** – Upload PDF/DOCX or provide a self-description.
- **📊 AI-Generated Reports** –
  - Match score (ATS compatibility).
  - Technical & behavioral questions.
  - Skill gap analysis.
  - Day-wise preparation plan.
- **📑 Tailored Resume PDF** – AI-optimized and rendered via Puppeteer.

---

## ⚙️ Requirements

- Node.js **18+** and npm/yarn.
- MongoDB (connection string).
- Google GenAI API key *(optional, for AI features)*.

---

## 🔑 Environment Variables

Create a `.env` file in `Backend/` with:

```env
MONGODB_URI=your_mongodb_connection_string
GOOGLE_GENAI_API_KEY=your_google_genai_api_key  # Optional
JWT_SECRET=your_jwt_secret_key
```

> ⚠️ **Do not commit `.env` to version control.**

---

## 🚀 Backend Setup

```bash
cd Backend
npm install
npm run dev
```

- **Default port:** `3000`
- **API Base URL:** `http://localhost:3000`

### 📡 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/auth/register` | Register a new user |
| `POST` | `/api/auth/login` | Login (sets JWT cookie) |
| `GET`  | `/api/auth/get-me` | Get current user *(auth required)* |
| `POST` | `/api/interview` | Generate report *(multipart: `resume`, `jobDescription`, `selfDescription`)* |
| `GET`  | `/api/interview` | List user reports |
| `GET`  | `/api/interview/report/:id` | Fetch a single report |
| `POST` | `/api/interview/resume/pdf/:id` | Generate tailored resume PDF |

---
---
## 🖥️ Frontend Setup

```bash
cd Frontend
npm install
npm run dev
```
- **Backend expected at:** `http://localhost:3000`
- **CORS:** Configured with credentials for local development.

---
---
## 🔒 Security & Notes

- **🔑 API Keys:** Keep `GOOGLE_GENAI_API_KEY` and `JWT_SECRET` **private**.
- **📜 Resume Storage:**
  - Uploaded resumes are parsed and stored as **text** in MongoDB.
  - Consider **privacy/GDPR compliance** for production use.
- **🎭 Puppeteer:**
  - Runs headless for PDF generation.
  - Ensure your environment supports Puppeteer *(e.g., Linux dependencies)*.

---
---
## 🚀 Deployment

To push to GitHub:

```bash
git init
git add .
git commit -m "chore: initial import"
git branch -M main
git remote add origin https://github.com/pushpakrai/Interview-AI-.git
git push -u origin main
```

> 💡 Use a **Personal Access Token (PAT)** or **SSH keys** for authentication.

---
---
## 🔍 Code Navigation

| Component | Location |
|-----------|----------|
| Backend Entry | `Backend/server.js`, `Backend/src/app.js` |
| AI Logic | `Backend/src/services/ai.service.js` *(@google/genai)* |
| Interview Handling | `Backend/src/controllers/interview.controller.js`, `Backend/src/routes/interview.routes.js` |
| Authentication | `Backend/src/controllers/auth.controller.js`, `Backend/src/middlewares/auth.middleware.js` |
| Frontend Entry | `Frontend/src/main.jsx` |
| Frontend Routes | `Frontend/src/app.routes.jsx` |
| Frontend Pages | `Frontend/src/features/` |

---
---
## 🤝 Contributing
Pull requests are welcome! For major changes, please open an issue first.

## 📜 License
[MIT](https://choosealicense.com/licenses/mit/)
