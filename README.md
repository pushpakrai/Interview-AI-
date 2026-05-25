# Interview-AI-

Full-stack application that generates AI-powered interview reports and tailored resumes from a candidate's resume/self-description and a target job description.

## Project layout

- `Backend/` - Express API using Google GenAI to generate reports and Puppeteer to render PDFs.
- `Frontend/` - React + Vite single-page app for user interaction.

## Key features

- User auth (register/login/logout) with JWT cookies.
- Upload resume (PDF/DOCX) or provide a self-description.
- AI-generated interview report: match score, technical & behavioral questions, skill gaps, and a day-wise preparation plan.
- Generate a tailored resume PDF via AI and Puppeteer.

## Requirements

- Node.js 18+ and npm
- MongoDB (connection string)
- Google GenAI API key (if using AI features)

## Environment variables

Create a `.env` file in `Backend/` with:

- `MONGODB_URI` - MongoDB connection URI
- `GOOGLE_GENAI_API_KEY` - (optional) Google GenAI API key
- `JWT_SECRET` - secret used to sign JWT tokens

## Backend - run (development)

```
cd Backend
npm install
npm run dev
```

The backend listens on port `3000` by default.

API endpoints (summary):

- `POST /api/auth/register` - register
- `POST /api/auth/login` - login
- `GET /api/auth/get-me` - get current user (requires cookie)
- `POST /api/interview` - generate report (multipart: `resume` file + `jobDescription` + `selfDescription`)
- `GET /api/interview` - list user reports
- `GET /api/interview/report/:interviewId` - get a single report
- `POST /api/interview/resume/pdf/:interviewReportId` - generate resume PDF

## Frontend - run (development)

```
cd Frontend
npm install
npm run dev
```

The frontend expects the backend to be reachable at `http://localhost:3000` and uses CORS with credentials.

## Notes & Security

- Keep your `GOOGLE_GENAI_API_KEY` and `JWT_SECRET` private (do not commit `.env`).
- Uploaded resumes are parsed and stored in the database as text — consider storage and privacy implications for production.
- Puppeteer runs headless to generate PDFs; ensure the runtime environment supports Puppeteer (install required system dependencies on some Linux hosts).

## Deploying / Pushing to GitHub

To push this project to your GitHub repository (replace the remote URL if needed):

```
git init
git add .
git commit -m "chore: initial import"
git branch -M main
git remote add origin https://github.com/pushpakrai/Interview-AI-.git
git push -u origin main
```

If push requires credentials, use a personal access token or set up SSH keys.

## Where to look in code

- Backend entry: `Backend/server.js` and `Backend/src/app.js`.
- AI logic: `Backend/src/services/ai.service.js` (uses `@google/genai`).
- Interview handling: `Backend/src/controllers/interview.controller.js` and `Backend/src/routes/interview.routes.js`.
- Auth: `Backend/src/controllers/auth.controller.js` and `Backend/src/middlewares/auth.middleware.js`.
- Frontend entry: `Frontend/src/main.jsx`, routes in `Frontend/src/app.routes.jsx`, pages under `Frontend/src/features`.

---

If you want, I can also:

- run the git commands to commit and push (you may need to enter credentials), or
- open specific files and explain any function in more detail.
