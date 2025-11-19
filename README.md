📦 Recipe AI App — Fullstack (Flask + React)

A full-stack Recipe application built with Flask (Python) for the backend API and React for the frontend interface.
This project demonstrates user authentication, CRUD operations, and communication between a REST API and a React client.



🚀 Tech Stack

Frontend

* React (CRA)
* React Router
* Bootstrap / Custom CSS
* Fetch API / Axios (optional)

Backend

* Flask
* Flask-RESTX (API routing + Swagger docs)
* Flask-JWT-Extended (authentication)
* Flask-Migrate + SQLAlchemy (database)
* CORS enabled
* Gunicorn / Render deployment ready



📁 Project Structure


project-root/
│
├── backend/
│   ├── main.py
│   ├── run.py
│   ├── wsgi.py
│   ├── models.py
│   ├── auth.py
│   ├── recipes.py
│   ├── exts.py
│   ├── config.py
│   ├── requirements.txt
│   └── migrations/
│
├── client/
│   ├── package.json
│   ├── src/
│   ├── public/
│   └── README.md (CRA default)
│
└── README.md  ← (THIS FILE)




🛠 Backend Installation (Flask)

Navigate to backend:

```bash
cd backend
```

Create venv:

```bash
python -m venv venv
source venv/Scripts/activate    # Windows
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Run migrations:

```bash
flask db init
flask db migrate
flask db upgrade
```

Run server:

```bash
python run.py
```

Backend will run on:

```
http://localhost:5000
```

---

🛠 Frontend Installation (React)

Navigate to client:

```bash
cd client
npm install
npm start
```

Frontend runs on:

```
http://localhost:3000
```

The client automatically proxies API calls to Flask via:

```json
"proxy": "http://localhost:5000"
```

---

🔑 Environment Variables

Create a `.env` file inside **backend/** with:

```
SECRET_KEY=your_secret_key
JWT_SECRET_KEY=your_jwt_secret
SQLALCHEMY_DATABASE_URI=sqlite:///db.sqlite3
```

Optional for Postgres (Render):

```
SQLALCHEMY_DATABASE_URI=${DATABASE_URL}
```

---

🔌 API Endpoints

## **Auth**

| Method | Endpoint         | Description           |
| ------ | ---------------- | --------------------- |
| POST   | `/auth/register` | Register new user     |
| POST   | `/auth/login`    | Login and receive JWT |

## **Recipes**

| Method | Endpoint              | Description                      |
| ------ | --------------------- | -------------------------------- |
| GET    | `/recipe/hello`       | Test endpoint                    |
| GET    | `/recipe/recipes`     | Get all recipes                  |
| POST   | `/recipe/recipes`     | Create a recipe *(JWT required)* |
| GET    | `/recipe/recipe/<id>` | Get recipe by ID                 |
| PUT    | `/recipe/recipe/<id>` | Update recipe *(JWT required)*   |
| DELETE | `/recipe/recipe/<id>` | Delete recipe *(JWT required)*   |

All endpoints documented automatically via Swagger:

```
http://localhost:5000/docs
```



# 🌐 **Deployment Guide**

## ▶️ Deploy Backend (Flask) — Render

1. Push project to GitHub
2. Go to Render → New Web Service
3. Select your repo
4. Set **Root Directory:** `backend/`
5. Set **Start Command:**

   ```
   gunicorn wsgi:app
   ```
6. Add environment variables
7. Deploy

---

## ▶️ Deploy Frontend (React) — Vercel

1. Go to Vercel → New Project
2. Select same repo
3. Set **Root Directory:** `client/`
4. Build command:

   ```
   npm run build
   ```
5. Output directory:

   ```
   build
   ```
6. Deploy

---

# 🔗 **Connecting Frontend & Backend (Production)**

After Render deploys your Flask API, update your React API URL:

Inside `client/src/...` wherever you call the API:

```javascript
const API_URL = "https://your-render-api.onrender.com";
```

Remove the `"proxy"` line from package.json when deploying.

---

# 🧪 **Testing the API**

Use Swagger:

```
http://localhost:5000/docs
```

Or Postman / Thunder Client.

---

# 👨🏽‍💻 **Author**

Built by **Blessing Chukwuemeka**
Full-stack Developer | Web3 Enthusiast | React + Python Engineer

---

# ⭐ **Support**

If this project helped you, hit ⭐ on GitHub!


