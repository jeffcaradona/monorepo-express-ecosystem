# Monorepo Setup Instructions

This monorepo contains a local Node.js ecosystem with the following components:

- **Express.js 5 Front End Application**
- **Express.js 5 API** (handles requests for the front end, not direct browser access)
- **Node.js Service** (processes messages from IBM MQ)
- **IBM MQ Queue Manager** (Docker container)
- **MS SQL Server** (Docker container)

## Prerequisites

- [Node.js 22.x](https://nodejs.org/)
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Visual Studio Code](https://code.visualstudio.com/)

## Project Structure

```
/
├── apps/
│   ├── frontend/      # Express.js 5 front end
│   ├── api/           # Express.js 5 API
│   └── mq-service/    # Node.js MQ processor
├── docker/
│   ├── mssql/         # MS SQL Server Docker setup
│   └── ibmmq/         # IBM MQ Docker setup
└── INSTRUCTIONS.md    # This file
```

## Setup Steps

1. **Clone the repository**
   ```sh
   git clone <repo-url>
   cd <repo-folder>
   ```

2. **Install dependencies for each Node.js app**
   ```sh
   cd apps/frontend && npm install
   cd ../api && npm install
   cd ../mq-service && npm install
   ```

3. **Start Docker containers**
   ```sh
   cd docker/mssql && docker compose up -d
   cd ../ibmmq && docker compose up -d
   ```

4. **Run Node.js applications (in separate terminals)**
   ```sh
   # In apps/frontend
   npm start

   # In apps/api
   npm start

   # In apps/mq-service
   npm start
   ```

## Notes

- All Node.js apps use ES modules (modern JavaScript imports).
- Configure environment variables as needed for local development.
- The API is not exposed directly to browsers; only the front end communicates with it.
