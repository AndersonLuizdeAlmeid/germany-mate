<div align="center">

# GermanyMate

**Immigration assistant platform for Brazil → Germany — Chancenkarte calculator, visa checklist, and appointment monitoring with real-time alerts.**

[![.NET](https://img.shields.io/badge/.NET-8.0-512BD4?style=flat-square&logo=dotnet&logoColor=white)](https://dotnet.microsoft.com/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-16-4169E1?style=flat-square&logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![React](https://img.shields.io/badge/React-Vite-61DAFB?style=flat-square&logo=react&logoColor=black)](https://react.dev/)
[![Docker](https://img.shields.io/badge/Docker-ready-2496ED?style=flat-square&logo=docker&logoColor=white)](https://www.docker.com/)
[![CI/CD](https://img.shields.io/badge/CI%2FCD-GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)](https://github.com/features/actions)
[![AI](https://img.shields.io/badge/AI-Advisor-FF6B35?style=flat-square&logo=anthropic&logoColor=white)](https://anthropic.com/)

</div>

---

## About

GermanyMate helps Brazilian professionals navigate the German immigration process — from calculating Chancenkarte eligibility and tracking required documents to monitoring visa appointment availability with instant Telegram and email alerts.

Built as a full-stack SaaS with a React frontend, .NET backend, and AI-powered advisory layer. The platform is currently in production and actively used by people planning their relocation to Germany.

> This repository is a public showcase. The source code is proprietary and kept in a private repository.

---

## Key Features

- **Chancenkarte calculator** — scores the user's eligibility for Germany's points-based Chancenkarte visa based on education, work experience, language skills, and other criteria
- **Immigration checklist** — personalized step-by-step checklist of required documents and actions, with per-item status tracking
- **Appointment monitor** — tracks visa appointment slots and notifies users the moment availability opens
- **Real-time alerts** — notifications delivered via Telegram and email so users never miss a window
- **AI Advisor** — AI-powered layer that answers immigration questions and provides personalized guidance
- **Google OAuth + email auth** — sign in with Google or traditional email/password
- **AI rate limiting** — fair-use enforcement on the AI advisory feature per subscription tier

---

## Architecture
GermanyMate
├── GermanyMate.API # REST API — controllers, middleware, DI
├── GermanyMate.Application # Use cases — commands, queries, DTOs, interfaces
├── GermanyMate.Domain # Entities, enums, domain logic
└── GermanyMate.Infrastructure # EF Core, repositories, external services

CQRS-inspired feature structure:
Features/
├── Auth/
│ ├── Commands/ LoginCommand RegisterCommand GoogleLoginCommand
│ └── DTOs/ AuthDtos
├── Chancenkarte/
│ └── Queries/ CalculateChancenkarteQuery
├── Checklist/
│ ├── Commands/ CreateChecklistCommand UpdateChecklistItemCommand
│ └── Queries/ GetUserChecklistQuery
└── Monitor/
├── Commands/ CreateMonitorCommand UpdateMonitorStatusCommand
└── Queries/ GetUserMonitorsQuery

---
## Tech Stack
| Layer | Technology |
|---|---|
| API | ASP.NET Core 8, C# |
| ORM | Entity Framework Core |
| Database | PostgreSQL |
| Frontend | React 18, TypeScript, Vite |
| Auth | JWT + Google OAuth 2.0 |
| Notifications | Telegram Bot API + SMTP Email |
| AI | AI Advisor with per-user rate limiting |
| Containerization | Docker, Docker Compose |
| CI/CD | GitHub Actions → Docker Hub |
---
## Domain Modules
| Module | Responsibilities |
|---|---|
| `Auth` | Email/password registration, login, Google OAuth |
| `Chancenkarte` | Points-based visa eligibility calculator |
| `Checklist` | Personalized immigration document checklist with status tracking |
| `Monitor` | Appointment slot monitoring with status lifecycle |
| `Notifications` | Telegram + email alert delivery |
| `AI Advisor` | AI-powered immigration Q&A with rate limiting |
---
## Chancenkarte Calculator
The Chancenkarte (Opportunity Card) is Germany's points-based immigration visa introduced in 2024. GermanyMate's calculator evaluates:
| Criterion | Points |
|---|---|
| Qualified professional degree | +1 |
| Work experience (years) | up to +3 |
| German language skills (A1–C1) | up to +3 |
| English or other language skills | +1 |
| Age bracket (under 35, under 40) | up to +2 |
| Connection to Germany (prior stay, family) | +1 |
Users get an instant score with a breakdown explaining which criteria they meet and what they can improve.
---
## Monitoring Flow
User creates monitor (visa type + target consulate)
↓
Background checker polls appointment availability
↓
Slot detected → Telegram message + email sent instantly
↓
User updates monitor status (acting / resolved)

---
## API Overview
POST /auth/register
POST /auth/login
POST /auth/google-login

GET /chancenkarte/calculate

GET /checklist
POST /checklist
PUT /checklist/items/{id}

GET /monitor
POST /monitor
PUT /monitor/{id}/status

---
## Contact
**Anderson Luiz de Almeida** — Backend Developer | .NET · PostgreSQL · Docker

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/anderson-luiz-almeida)
[![GitHub](https://img.shields.io/badge/GitHub-Profile-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/AndersonLuizdeAlmeid)
