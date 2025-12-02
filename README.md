# WarungAI: AI-Powered Micro-Retail Management System

[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Project Type](https://img.shields.io/badge/Project-Hackathon%20%26%20OpenSource-red.svg)]()
[![Backend](https://img.shields.io/badge/Backend-NestJS%20%7C%20Bun%20%7C%20Prisma%20%7C%20PostgreSQL-D2691E)]()
[![Frontend](https://img.shields.io/badge/Frontend-Nuxt3%20%7C%20Vue%20%7C%20Tailwind-20B2AA)]()

## Project Overview

WarungAI is an open-source integrated system designed to empower Micro, Small, and Medium Enterprises (MSMEs), especially traditional Indonesian shops (warung). It provides intelligent, AI-supported business tools such as OCR-based receipt reading, basic analytics, and a modern dashboard. Built during a hackathon, the project demonstrates a scalable, decoupled architecture with clean separation of concerns.

Contributions are welcome from developers who want to build technology that uplifts small businesses.

## Architecture

WarungAI consists of two primary applications stored as separate repositories using Git Submodules. The root repository acts as the main project wrapper for easier development and deployment.

| Component | Technology Stack                | Core Function                 | Repository                                                                                                     | Branch |
| --------- | ------------------------------- | ----------------------------- | -------------------------------------------------------------------------------------------------------------- | ------ |
| Backend   | NestJS, Bun, Prisma, PostgreSQL | Authentication, Data, OCR API | [https://github.com/KanjutGusion/WarungAI-backend.git](https://github.com/KanjutGusion/WarungAI-backend.git)   | main   |
| Frontend  | Nuxt 3, Vue 3, Tailwind CSS     | UI (Login, Dashboard, Pages)  | [https://github.com/KanjutGusion/WarungAI-frontend.git](https://github.com/KanjutGusion/WarungAI-frontend.git) | main   |

## Key Features (MVP)

* User Authentication (Register, Login)
* Role-Based Access Control (Super Admin, Seller)
* OCR Endpoint for parsing receipts via Kolosal AI
* Modern, responsive UI using Nuxt 3 and Tailwind CSS

## Prerequisites

Install the following before running the project:

1. Git
2. Node.js (>=20.9.0) for the frontend
3. Bun (>=1.0) for the backend
4. Docker and Docker Compose (recommended)
5. PostgreSQL database

## Installation and Setup

### 1. Clone the Project (Important)

Use recursive cloning to load submodules:

```bash
git clone --recurse-submodules https://github.com/KanjutGusion/WarungAI.git
cd WarungAI
```

If you forgot the flag:

```bash
git submodule update --init --recursive
```

### 2. Configure Environment

Add `.env` files for each module using the included example files.

| Component | Example File          | Description                                        |
| --------- | --------------------- | -------------------------------------------------- |
| Backend   | backend/.env.example  | Contains DATABASE_URL, JWT_SECRET, KOLOSAL_API_KEY |
| Frontend  | frontend/.env.example | Contains API_BASE_URL and frontend variables       |

Generate a secure JWT secret for backend:

```bash
chmod +x backend/generate-secret.sh
./backend/generate-secret.sh
```

### 3. Install Dependencies & Setup Database

#### Backend Setup (NestJS + Bun)

```bash
cd backend
bun install
```

Run Prisma migrations and seeding:

```bash
bunx prisma migrate dev --name init_database
bun run ts-node prisma/seed.ts
```

Seeder creates a default Super Admin:

* Email: [root@root.root](mailto:root@root.root)
* Password: password

#### Frontend Setup (Nuxt 3)

```bash
cd frontend
npm install
# or pnpm install
```

## Running the Project

Frontend and backend run separately.

### 1. Backend API (Port 3000)

```bash
cd backend
bun run start:dev
```

API runs at:

```
http://localhost:3000/api/v1
```

### 2. Frontend App (Port 3000)

```bash
cd frontend
npm run dev
# or pnpm run dev
```

Frontend runs at:

```
http://localhost:3000
```

## Dockerized Development

Frontend includes a Docker Compose profile for development.

Run:

```bash
docker-compose --profile dev up warungai-frontend-dev
```

## Contributing

We welcome community contributions.

1. Submit issues for bugs or feature suggestions.
2. Contribution steps:

   * Fork the specific submodule (backend or frontend)
   * Create a feature branch
   * Commit changes
   * Open a Pull Request to the `main` branch of that submodule

## License

Licensed under the MIT License. See `LICENSE` for details.
