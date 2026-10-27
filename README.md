# DevSync

**An AI-assisted platform that matches developers with projects, based on their real GitHub activity.**

DevSync was the capstone project of the Cross-Platform Mobile track at the **Digital Egypt Pioneers Initiative (DEPI, MCIT)**, May – Jul 2026, built by a **5-member team led by [Amr Elsherif](https://github.com/amrelsherif-eng)**.

![Flutter](https://img.shields.io/badge/Flutter-02569B?style=flat-square&logo=flutter&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase-FFCA28?style=flat-square&logo=firebase&logoColor=black)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![GitHub API](https://img.shields.io/badge/GitHub_API-181717?style=flat-square&logo=github&logoColor=white)

![DevSync infographic](Project%20Infographic.png)

## What it does

- **Two roles:** developers find projects; project owners publish projects and find developers.
- **GitHub-based profiles:** a developer's languages and activity are read from the GitHub API to build their skill profile.
- **Match ranking:** owners get developers ranked by how well they fit a project, from "Perfect Match" to "Weak Match".
- **AI assistant:** an in-app chat that helps owners shape an idea into a project proposal and helps developers explore projects. It calls an LLM API (Groq, Llama 3.3 70B, in the current code; Google Gemini in earlier versions).
- **Notifications:** Firebase Cloud Messaging for invitations and project updates.

## Tech stack

| Layer | Tools |
|---|---|
| App | Flutter, Dart, GetX (state, routing, DI), Dio, flutter_animate |
| Firebase | Auth (Google Sign-In), Cloud Firestore, Cloud Messaging, Remote Config, Analytics, Cloud Functions |
| Matching service | Python, FastAPI (`/analyze`, `/matches/calculate`) in `python_backend/` |
| External APIs | GitHub REST API, Groq / Gemini LLM APIs |

## Project structure

```text
lib/
├── app/            # Routes
├── core/           # Theme, constants
├── data/           # Models, Firebase + GitHub providers, services (AI, FCM, analytics, Remote Config)
├── flavors/        # Build flavor config
└── presentation/   # Feature modules (auth, dashboards, matches, projects, AI chat) + shared widgets
python_backend/     # FastAPI matching service
functions/          # Firebase Cloud Functions (GitHub token exchange)
docs/               # Architecture notes
```

Architecture notes are in [`docs/`](docs/).

## Run it locally

```bash
flutter pub get
flutter run

# matching service
cd python_backend
pip install -r requirements.txt
uvicorn main:app --reload --port 8000
```

You need your own Firebase project (`flutterfire configure`), and API keys set in Firebase Remote Config, not in code.

## Team

5-member DEPI team. Team lead: Amr Elsherif.
