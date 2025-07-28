# NLW Agents - Backend Server

> Backend server for the NLW Agents project, developed during a Rocketseat event.

## Overview

NLW Agents is an AI-powered application that processes audio content, generates transcriptions, and provides intelligent question-answering capabilities using vector embeddings and semantic search. This repository contains the backend server implementation.

## Tech Stack

### Core Technologies

- **Node.js** - Runtime environment with native TypeScript support
- **Fastify** - High-performance web framework
- **TypeScript** - Type-safe development
- **PostgreSQL** - Primary database with pgvector extension
- **Docker** - Containerization and development environment

### Key Libraries

- **Drizzle ORM** - Type-safe database operations and migrations
- **Zod** - Runtime schema validation and type inference
- **@google/genai** - Google Gemini AI integration for transcription and embeddings
- **@fastify/cors** - Cross-origin resource sharing
- **@fastify/multipart** - File upload handling
- **fastify-type-provider-zod** - Type-safe API validation

## Architecture & Design Patterns

### Modular Route Architecture

- Routes organized in separate modules (`src/http/routes/`)
- Type-safe request/response validation using Zod schemas
- Centralized route registration in main server file

### Service Layer Pattern

- AI operations abstracted into service modules (`src/services/`)
- Separation of concerns between HTTP layer and business logic

### Database Design

- Schema-driven development with Drizzle ORM
- Vector embeddings support with pgvector extension
- Type-safe migrations and seeding

### Environment-Based Configuration

- Centralized environment validation using Zod
- Type-safe environment variable access

## Database Schema

The application uses three main entities:

- **Rooms** - Organize content sessions
- **Questions** - User questions with vector embeddings
- **Audio Chunks** - Processed audio segments with transcriptions

## API Endpoints

- `GET /health` - Health check
- `GET /rooms` - List all rooms
- `POST /rooms` - Create a new room
- `GET /rooms/:roomId/questions` - Get questions for a room
- `POST /rooms/:roomId/questions` - Create a question
- `POST /rooms/:roomId/upload-audio` - Upload and process audio

## Setup Instructions

### Prerequisites

- Node.js 18+
- Docker and Docker Compose
- Google Gemini API key

### 1. Clone and Install Dependencies

```bash
git clone <repository-url>
cd nlw-agents-server
npm install
```

### 2. Environment Configuration

Create a `.env` file in the root directory:

```env
PORT=3333
DATABASE_URL=postgresql://docker:docker@localhost:5432/agents
GEMINI_API_KEY=your_gemini_api_key_here
```

### 3. Start Database

```bash
docker-compose up -d
```

This will start a PostgreSQL database with the pgvector extension enabled.

### 4. Run Database Migrations

```bash
npm run db:generate
npm run db:migrate
```

### 5. Seed Database (Optional)

```bash
npm run db:seed
```

### 6. Start Development Server

```bash
npm run dev
```

The server will start on `http://localhost:3333` with hot-reload enabled.

## Production Deployment

### Build for Production

```bash
npm start
```

### Database Management

- **Generate migrations**: `npm run db:generate`
- **Apply migrations**: `npm run db:migrate`
- **Seed database**: `npm run db:seed`

## AI Features

### Audio Transcription

- Converts audio files to text using Google Gemini AI
- Supports multiple audio formats
- Portuguese (Brazilian) transcription

### Vector Embeddings

- Generates semantic embeddings for questions and content
- Enables intelligent content search and retrieval
- Uses pgvector for efficient similarity search

### Question Answering

- Context-aware responses based on uploaded content
- Retrieval-augmented generation (RAG) pattern
- Maintains conversation context within rooms

## Development

### Code Quality

- **Biome** - Linting and formatting
- **TypeScript** - Static type checking
- **Zod** - Runtime validation

### Database Development

- Schema changes through Drizzle migrations
- Type-safe database operations
- Automatic TypeScript type generation

## License

ISC License - see LICENSE file for details.

---

_Developed during Rocketseat's NLW (Next Level Week) event._
