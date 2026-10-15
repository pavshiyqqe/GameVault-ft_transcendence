# GameVault – Real-Time Multiplayer Gaming Platform

> A containerized full-stack web platform featuring a server-authoritative Pong game, real-time matchmaking, live chat, interactive social systems, and detailed player analytics. Built as part of the **42 Paris** curriculum.

---

## 🚀 Key Highlights & Architecture

* **Frontend:** Single-page application built with **React**, **React Router**, and modern component-driven patterns.
* **Backend:** High-concurrency RESTful API and WebSocket hub built with **Go (Gin)**.
* **Real-Time Layer:** Low-latency bidirectional communication via **Gorilla WebSockets** for live gameplay synchronization, online presence, and instant messaging.
* **Database & Persistence:** **PostgreSQL** with structured relational schemas for users, friendships, chat history, and match telemetry.
* **Security & Auth:** Stateless session management with **JWT**, password hashing with **bcrypt**, CORS protection, and secure WebSocket handshakes.
* **DevOps & Infra:** Multi-container orchestration using **Docker Compose** with health checks, isolated networking, and production builds.

---

## 🛠 Tech Stack

| Domain | Technologies |
| :--- | :--- |
| **Frontend** | React, React Router, CRA, JavaScript/TypeScript, CSS Modules |
| **Backend** | Go (Golang), Gin Framework, Gorilla WebSocket |
| **Database** | PostgreSQL |
| **Authentication** | JWT (JSON Web Tokens), bcrypt |
| **DevOps** | Docker, Docker Compose, Linux environment |
| **Accessibility & i18n** | WCAG semantic structure, keyboard navigation, EN/FR/ES translations |

---

## 🎮 Core Features

* **Server-Authoritative Pong:**
  * Physics and ball collision calculated strictly on the backend to eliminate client-side cheating and desync.
  * Real-time remote multiplayer matchmaking over WebSockets.
  * Adaptive AI opponent with reaction latency and human-like movement modeling.
  * Automatic reconnection handling and game-state recovery.
* **Social & Community:**
  * User profiles with avatar uploads and bio management.
  * Real-time online/offline presence tracking.
  * Friend requests, player search, and user blocking.
  * Direct messaging with persistent chat history.
* **Analytics & Progression:**
  * Live match telemetry, win/loss tracking, and score breakdowns.
  * Dynamic leaderboard with performance statistics.
  * Full match history and replay data storage.
* **Accessibility & Usability:**
  * Fully accessible UI with ARIA tags, visible focus indicators, and full keyboard navigation.
  * Multi-language support (English, French, Spanish) with instant switching.

---

## ⚙️ Quick Start

### Prerequisites
* [Docker](https://www.docker.com/) and [Docker Compose](https://docs.docker.com/compose/) installed.

### 1. Clone & Configure
```bash
git clone https://github.com/pavshiyqqe/GameVault.git
cd GameVault
cp .env.example .env
```

### 2. Start Application
```bash
docker compose -f docker/docker-compose.yml up --build
```

### 3. Access the Services
* **Frontend Application:** [http://localhost:3000](http://localhost:3000)
* **Backend API:** [http://localhost:8000](http://localhost:8000)

---

## 👥 Team & Engineering Contributions

This project was built collaboratively by a team of 4 software engineers from **42 Paris**. While each engineer spearheaded specific domains, the team practiced agile cross-review and end-to-end integration across the stack.

### Yevhen Yaniv (`yyaniv`) — Full-Stack & Progression Systems
* **Full-Stack Development:** Designed and built the player progression, leaderboard, and match statistics system end-to-end (PostgreSQL schema, Go/Gin endpoints, and React interface).
* **React UI & State Integration:** Implemented responsive React components and state management for user stats, match records, and dynamic profile analytics.
* **Real-Time Data Flow:** Handled post-match telemetry updates and integrated live WebSocket notifications with the frontend UI.
* **Architecture & Cross-Stack Integration:** Collaborated on API design, client-side routing with React Router, and Dockerized multi-service coordination.

### `lmokhtar` — Frontend & Game Mechanics
* Designed initial application architecture and primary React layout/navigation flows.
* Implemented client-side Pong rendering, input handling, and WebSocket synchronization.
* Integrated core user flows and interactive game lobbies.

### `luctan` — Backend Architecture & Security
* Architected the core Go/Gin service structure, REST routing, and PostgreSQL migrations.
* Implemented secure authentication flows (JWT handling, password hashing, auth middleware).
* Contributed to backend matchmaking queues, Docker networking, and server security.

### `rromanov` — Accessibility & Localization
* Implemented WCAG accessibility standards across all views (keyboard navigation, skip-links, ARIA semantics, accessible game controls).
* Engineered the internationalization (i18n) system with multi-language state persistence (EN, FR, ES).

---

## 🗄 Database Design

Key PostgreSQL data models powering the platform:
* `users` — Authentication credentials, profile metadata, win/loss aggregates, and activity status.
* `friendships` — Bidirectional social graph tracking pending and accepted connections.
* `messages` — Chat communication records with timestamps and sender/recipient relations.
* `matches` — Match telemetry (scores, participants, winner IDs, game mode, timestamps).
* `games` & `game_reviews` — Game library data and community ratings.

---

## 📐 Technical Decisions

* **React (SPA):** Enables a modular, component-driven UI with predictable state rendering, essential for dashboards, chats, and dynamic game screens without full-page reloads.
* **Go + Gin:** Chosen for native concurrency (goroutines), minimal memory footprint, and high-throughput WebSocket handling required for server-authoritative gaming.
* **Server-Authoritative Physics:** Guarantees fair play by calculating ball trajectories and scoring on the server, broadcasting synched states to both clients.
* **PostgreSQL:** Ensures strict relational integrity, transactions, and robust indexing for leaderboards and user statistics.