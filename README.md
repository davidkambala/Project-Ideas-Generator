# Project Ideas Generator

A lightweight Node.js + Express web app that generates project ideas for university students, powered by OpenAI’s GPT-3.5 and a PostgreSQL backing store.


# ✨ Features

Generate tailored project ideas using GPT-3.5 (theme, difficulty, and field aware).

Persist ideas to Postgres for later browsing and filtering.

Simple EJS frontend with static assets in public/.

One-file server entry (index.js) for easy deployment. 
GitHub

# 🧱 Tech Stack

Backend: Node.js + Express

Database: PostgreSQL

Views: EJS templates (views/)

Static assets: public/

AI: OpenAI GPT-3.5
Repo language stats indicate EJS/CSS/JS composition; server runs on port 3000 by default. 
GitHub

# 🗂️ Project Structure (typical)
Project-Ideas-Generator/
├─ public/            # CSS/JS/Images (static files)
├─ views/             # EJS templates
├─ index.js           # Express server (app entry)
├─ ddl.sql            # DB table DDL
├─ package.json       # scripts & deps
└─ .env               # environment variables (not committed)


Folders/files above are present in the repo; ddl.sql, public/, views/, index.js, package.json are listed on GitHub. 
GitHub

# ⚙️ Setup & Installation
# 1) Clone
git clone https://github.com/davidkambala/Project-Ideas-Generator
cd Project-Ideas-Generator

# 2) Install dependencies
npm install

# 3) Configure environment

Create a .env file at the project root:

API_KEY="your OpenAI key"
DB_USER="your postgres username"
DB_HOST="localhost"
DB_NAME="PIG"
DB_PW="your postgres password"
DB_PORT=5432


These variables are documented in the repo’s notes. 
GitHub

# 4) Create database objects

Run the provided DDL (or execute this SQL):

CREATE TABLE Projects(
    Project_ID   SERIAL PRIMARY KEY,
    Title        TEXT,
    Field        TEXT,
    Difficulty   TEXT,
    Description  TEXT,
    Task         TEXT
);


The schema is included in the README/DDL materials. 
GitHub

# 5) Run the app
node index.js
# App listens on http://localhost:3000


Default port is 3000 per the repo README. 


# 🔑 OpenAI Notes

The app expects an OpenAI API Key via API_KEY in .env.

Model referenced: GPT-3.5 (you can switch to GPT-4+ by adjusting API calls & pricing awareness).

# 🧪 Development Scripts (suggested)

Add these to package.json (if not already):

{
  "scripts": {
    "dev": "nodemon index.js",
    "start": "node index.js",
    "lint": "eslint ."
  }
}


Run:

npm run dev

🧭 Typical Request Flow
flowchart LR
    U[User] -->|Prompt/Filters| W[Express Route]
    W --> OAI[OpenAI API (GPT-3.5)]
    OAI --> W
    W --> DB[(PostgreSQL)]
    DB --> W
    W --> V[EJS View]
    V --> U

# 🔒 Environment & Security

Don’t commit .env (contains secrets).

Use a dedicated DB user with least privilege.

Consider rate-limiting routes that call OpenAI.

# 🚀 Deployment

Render/Fly.io/Railway for quick Node + Postgres deployment.

Set env vars in the platform dashboard.

Provision managed Postgres; run ddl.sql once.

Ensure PORT env var is respected (update index.js to use process.env.PORT || 3000 if not already).

# 🛣️ Roadmap

 User accounts + saved idea collections

 Topic/difficulty filters in UI

 Pagination & search

 Export to Markdown/CSV

 Rate limiting & caching for OpenAI calls

 Add tests (Jest) and ESLint/Prettier

# 🤝 Contributing

Fork the repo & create a feature branch

Add/adjust EJS templates under views/ and routes in index.js

Include migration changes in ddl.sql if needed

Open a PR with a concise description & screenshots

# 📄 License

MIT — feel free to use and adapt for your own student-idea generators or internal tools.

# 📝 Appendix

Existing README highlights (source): installation steps, .env keys, DDL, and the default port reference were taken from the repo page. 
GitHub
