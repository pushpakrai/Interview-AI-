# 🚀 Interview-AI

Smart, AI-powered interview prep that turns your resume or self-description and a target job description into a tailored interview plan and resume PDF.

## ✨ Quick Summary
- 🔐 Auth: JWT cookie-based sign in/out
- 📄 Upload: Resume (PDF/DOCX) or paste a self-description
- 🤖 AI output: Match score, technical & behavioral Qs, skill gaps, and a day-by-day preparation plan
- 🖨️ Export: Tailored resume PDF generated via AI + Puppeteer

## ⚙️ Quick Start
Backend
```
cd Backend
npm install
npm run dev
```
Frontend
```
cd Frontend
npm install
npm run dev
```

## 🔑 Env (Backend/.env)
- `MONGODB_URI`
- `GOOGLE_GENAI_API_KEY` (optional)
- `JWT_SECRET`

## 📡 API (summary)
- `POST /api/auth/register` — register
- `POST /api/auth/login` — login
- `POST /api/interview` — generate report (multipart: `resume`, `jobDescription`, `selfDescription`)
- `POST /api/interview/resume/pdf/:interviewReportId` — generate resume PDF

## ⚠️ Notes
- Keep secrets out of source control. Use `.env` and secure storage for API keys.
- Uploaded resumes are parsed and stored as text; consider privacy and retention policies.

---
