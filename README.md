# Employee Management System (EMS)

A full-stack Employee Management app — Express.js backend + React (Vite) frontend.

## Project Structure

```
EMS2/
├── EMS-backend/          # Express.js REST API
│   ├── controllers/      # Route handlers
│   ├── routes/           # Express routers
│   ├── middleware/       # Logger middleware
│   ├── data/             # In-memory employee data
│   └── index.js          # Entry point
│
└── ems-frontend/         # React + Vite UI
    └── src/
        ├── App.jsx        # Main component
        └── index.css      # Styles (light + dark mode)
```

---

## Local Development

### 1. Backend

```bash
cd EMS-backend
npm install
cp .env.example .env          # edit if needed
npm run dev                   # starts on http://localhost:5100
```

### 2. Frontend

```bash
cd ems-frontend
npm install
cp .env.example .env          # edit if needed
npm run dev                   # starts on http://localhost:5173
```

---

## Deploying

### Backend → Render

1. Push this repo to GitHub.
2. Go to [render.com](https://render.com) → **New → Web Service**.
3. Connect your GitHub repo and select it.
4. Set these values:
   - **Root Directory:** `EMS-backend`
   - **Build Command:** `npm install`
   - **Start Command:** `npm start`
5. Under **Environment Variables**, add:
   - `FRONTEND_URL` → *(leave blank for now; fill in after Vercel deploy)*
6. Click **Deploy**. Copy the URL Render gives you (e.g. `https://ems-backend.onrender.com`).

> **Note:** Render's free tier spins down after inactivity. First request may take ~30s.

---

### Frontend → Vercel

1. Go to [vercel.com](https://vercel.com) → **Add New → Project**.
2. Import your GitHub repo.
3. Set **Root Directory** to `ems-frontend`.
4. Under **Environment Variables**, add:
   - `VITE_API_URL` → your Render URL (e.g. `https://ems-backend.onrender.com`)
5. Click **Deploy**. Copy the Vercel URL (e.g. `https://ems-frontend.vercel.app`).

---

### Final step — wire CORS on Render

1. Go back to your Render service → **Environment**.
2. Set `FRONTEND_URL` → your Vercel URL (e.g. `https://ems-frontend.vercel.app`).
3. Render will redeploy automatically.

That's it — your app is live! 🚀

---

## API Reference

| Method | Endpoint          | Description          |
|--------|-------------------|----------------------|
| GET    | /employees        | Get all employees    |
| GET    | /employees/:id    | Get employee by ID   |
| POST   | /employees        | Add new employee     |
| PUT    | /employees/:id    | Update employee      |
| DELETE | /employees/:id    | Delete employee      |

### Employee object

```json
{
  "id": 1,
  "name": "Rahul",
  "department": "IT",
  "salary": 50000
}
```
