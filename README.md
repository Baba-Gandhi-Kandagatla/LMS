# SkillForge (EduGenie)

## Introduction

We built SkillForge around the way our courses were organized. Pick a semester, subject and unit, and you can read the lesson, try a quiz or ask about a passage in the material. You’ll see the name EduGenie in the student interface.

## Tech stack

| Part | What it does |
| --- | --- |
| React and Vite, in `src/` | Renders the course navigation, readings, videos, assessments and chat. The course structure is in `src/data.json`. |
| Express and MongoDB, in `backend/` | Handles registration and sign-in through a Mongoose model. |
| Flask, in `flask/app.py` | Sends documents and questions to ChatPDF and exposes quiz, assessment and feedback routes to the client. |

## Features

- Open a unit’s readings and videos.
- Practice with quizzes, assessments and interview questions.
- Ask a document-based tutor for an explanation tied to the course material.

## The process

After sign-in, the React client uses the course structure in `src/data.json` to navigate from semester to unit. A reading, quiz and tutor conversation share that unit context. For assessments and tutoring, the client calls the Flask service, which works with ChatPDF document sources. The main student routes are in `src/App.jsx`.

We also explored personalized roadmaps and head-to-head quizzes in the wider project.

## How it can be improved

I’d include a short sample course, a test account and a saved tutor response so you could try a lesson, take its quiz and see feedback on your first run.

## How to run

Run each component in its own terminal with development accounts and sample course material.

| Component | Local setup |
| --- | --- |
| Course interface | From the root, run `npm ci` and `npm run dev`. |
| Accounts | Configure a development MongoDB connection in `backend/index.js`. From `backend/`, run `npm ci` and `npm start`. The client expects port 3001. |
| Tutor and assessments | Configure your ChatPDF key and document source IDs in `flask/app.py`. In a Python virtual environment, install Flask, Flask-Cors and Requests, then run `python flask/app.py` from the root. The client expects port 5000. |

## Screenshots

![Reading a React lesson with video, quiz and tutor options alongside it.](docs/images/course-reading.png)
