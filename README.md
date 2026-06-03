# World Capital Quiz 🌍🏙️

A simple web quiz game that asks you to type the **capital city** for a randomly selected country. Your score is tracked across questions, and the game ends when you submit an incorrect answer.

Built with **Node.js + Express**, using **EJS** for templating and **PostgreSQL** for storing/loading quiz data.

---

## Features

- Random country → prompt for its capital
- Score counter (total correct answers)
- Case-insensitive answer checking
- Immediate UI feedback (✔ correct / ✖ incorrect)
- “Game over” alert and restart link
- Quiz data loaded from a PostgreSQL table (`capitals`)

---

## Tech Stack

- **Express** (routing + server)
- **EJS** (server-side rendering)
- **body-parser** (handling form submissions)
- **pg** (PostgreSQL client)
- **PostgreSQL** (quiz dataset)
- **HTML/CSS** (UI via `public/`)

---

## Project Layout

- `index.js`  – Express server logic (routes, quiz selection, DB reads)
- `views/index.ejs` – Quiz page (country name, answer input, score display)
- `public/styles/main.css` – Styling + button/input layout + animations
- `capitals.csv` – Dataset used to populate the `capitals` table

---

## How It Works

### 1) Load quiz data
On startup, the server queries PostgreSQL:

- `SELECT * FROM capitals`

The results are stored in memory as the `quiz` array.

### 2) Start / next question
- `GET /` resets `totalCorrect` and selects a random question.
- The current question is rendered into `views/index.ejs`.

### 3) Submit answer
- `POST /submit` compares the submitted answer against `currentQuestion.capital`.
- Comparison is **case-insensitive**.

If correct:
- `totalCorrect++`
- Next question is selected and rendered.

If incorrect:
- the view renders with `wasCorrect: false`
- a small script shows the “Game over” alert and injects a restart link.

---

## Setup & Run

### 1) Install dependencies

```bash
npm install
```

### 2) Configure PostgreSQL
This project expects:

- Database: `World`
- Table: `capitals`
- Columns: at least `country` and `capital`

> ⚠️ Note: DB credentials are currently hard-coded in the server files.

### 3) Populate the database
Use `capitals.csv` to populate the table `capitals`.

The file format looks like:

- `id,country,capital`

Any CSV import method is fine (COPY, pgAdmin import, etc.).

### 4) Start the server

```bash
npm start
```

Then open:

- http://localhost:3000

---

## Usage

1. Type the capital city for the displayed country.
2. Click **SUBMIT**.
3. Continue until you get a wrong answer.
4. Use **Restart** to play again.

---

## Notes / Possible Improvements

- Move DB credentials to environment variables (`.env`) for security
- Add a `start` script in `package.json` if missing
- Replace `alert()` with a styled modal for a smoother UX

---

## License

ISC

