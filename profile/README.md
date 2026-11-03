<div align="center">
  <br />
  <h1>⚡ Sentirix AI</h1>
  <p><strong>The Open-Source, AI-Native Customer Support & Helpdesk Platform</strong></p>
  <p><em>An intelligent, self-hosted alternative to Zendesk and Intercom — equipped with real-time sentiment triage, Gemini AI copilot, and live WebSockets.</em></p>

  <p>
    <a href="https://nextjs.org"><img src="https://img.shields.io/badge/Frontend-Next.js%2016-black?style=for-the-badge&logo=next.js" alt="Next.js 16" /></a>
    <a href="https://react.dev"><img src="https://img.shields.io/badge/UI-React%2019-61DAFB?style=for-the-badge&logo=react" alt="React 19" /></a>
    <a href="https://nestjs.com"><img src="https://img.shields.io/badge/Backend-NestJS%2012-E0234E?style=for-the-badge&logo=nestjs" alt="NestJS 12" /></a>
    <a href="https://www.prisma.io"><img src="https://img.shields.io/badge/ORM-Prisma%206-2D3748?style=for-the-badge&logo=prisma" alt="Prisma 6" /></a>
    <a href="https://www.postgresql.org"><img src="https://img.shields.io/badge/Database-PostgreSQL%2016-336791?style=for-the-badge&logo=postgresql" alt="PostgreSQL 16" /></a>
    <a href="https://ai.google.dev"><img src="https://img.shields.io/badge/AI-Google%20Gemini-8E75C2?style=for-the-badge&logo=google" alt="Google Gemini" /></a>
  </p>
  <br />
</div>

---

## 🌟 Welcome to Sentirix AI

Traditional customer support platforms like **Zendesk** and **Intercom** charge expensive per-seat pricing ($55 – $115+/agent/month), lock your sensitive data behind proprietary clouds, and tack on rudimentary AI features at high premiums.

**Sentirix** was engineered to solve this:
* 🔒 **100% Self-Hosted & Privacy-First**: Keep customer conversations and internal notes on your own infrastructure.
* 🧠 **AI-Native Sentiment Triage**: Real-time scoring of customer emotional urgency (`FRUSTRATED`, `URGENT`, `NEUTRAL`, `POSITIVE`).
* 🤖 **Gemini AI Copilot**: Instant response drafts and long thread summaries powered by Google Gemini.
* ⚡ **Real-Time Collaboration**: Sub-millisecond agent collision detection, typing indicators, and WebSocket live sync.
* 🏢 **Multi-Pod Enterprise Workspaces**: Dedicated department pods with 1-click ticket transfers and executive SLA analytics.

---

## 📂 Official Repositories

| Repository | Purpose | Tech Stack | Status |
| :--- | :--- | :--- | :--- |
| [**`sentirix-web`**](https://github.com/sentirix-ai/sentirix-web) | Real-time agent dashboard, customer portal, helpdesk queue & executive cockpit | Next.js 16 (App Router), React 19, Tailwind CSS 4, Socket.io | [![CI](https://img.shields.io/github/actions/workflow/status/sentirix-ai/sentirix-web/ci.yml?branch=main&style=flat-square&logo=github-actions&label=CI)](https://github.com/sentirix-ai/sentirix-web/actions) |
| [**`sentirix-core`**](https://github.com/sentirix-ai/sentirix-core) | Core API engine, real-time WebSocket gateway, Gemini AI triage & Prisma ORM | NestJS 12, Prisma 6, PostgreSQL 16, Google Gemini, Docker | [![CI](https://img.shields.io/github/actions/workflow/status/sentirix-ai/sentirix-core/ci.yml?branch=main&style=flat-square&logo=github-actions&label=CI)](https://github.com/sentirix-ai/sentirix-core/actions) |

---

## 🏗️ Platform Architecture

```mermaid
flowchart LR
    subgraph Frontend [User Interface]
        Client[Support Agent / Customer] -->|Next.js 16 + Tailwind| WebApp[sentirix-web: Port 3000]
    end

    subgraph Backend [Core API & Realtime Gateway]
        WebApp -->|REST API / JWT Auth| CoreAPI[sentirix-core: Port 4000]
        WebApp <-->|Live WebSockets| CoreGateway[Socket.io Gateway]
        CoreAPI --> PrismaClient[Prisma ORM Client]
    end

    subgraph Infrastructure [Data & Intelligence]
        PrismaClient --> Postgres[(PostgreSQL 16 in Docker)]
        CoreAPI -->|@google/genai SDK| GeminiAI[Google Gemini 2.0 / 2.5 AI]
    end
```

---

## 📊 Sentirix vs Traditional Platforms

| Feature | Sentirix AI | Zendesk Enterprise | Intercom |
| :--- | :---: | :---: | :---: |
| **Pricing** | **Free & Open Source** | $115+/agent/mo | $99+/seat/mo |
| **Hosting** | **Self-Hosted (Docker)** | Proprietary Cloud | Proprietary Cloud |
| **Data Privacy** | **100% Owned by You** | 3rd Party Cloud | 3rd Party Cloud |
| **AI Sentiment Triage** | **Built-in (Gemini AI)** | Paid Add-on | Paid Add-on |
| **Real-time Collision Avoidance** | **Native WebSockets** | Limited | Native |
| **Multi-Pod Architecture** | **Built-in** | Enterprise Only | Enterprise Only |

---

## 🚀 60-Second Quickstart

```bash
# 1. Clone both repositories
git clone https://github.com/sentirix-ai/sentirix-core.git
git clone https://github.com/sentirix-ai/sentirix-web.git

# 2. Start PostgreSQL via Docker (inside sentirix-core)
cd sentirix-core
docker compose up -d

# 3. Setup and start Backend API
cp .env.example .env
npm install
npx prisma generate
npx prisma db push
npm run start:dev

# 4. In a new terminal, setup and start Frontend
cd ../sentirix-web
cp .env.example .env.local
npm install
npm run dev
```

Visit `http://localhost:3000` to access the Sentirix AI platform!

---

## 📜 License

All Sentirix repositories are proudly open-sourced under the [MIT License](https://github.com/sentirix-ai/sentirix-core/blob/main/LICENSE).
