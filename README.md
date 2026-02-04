# Mordecai

A cynical, world-weary AI assistant who just wants to keep you alive.

## What is Mordecai?

Mordecai is an AI chatbot with personality. Inspired by the Dungeon Manager character from the *Dungeon Crawler Carl* LitRPG series, Mordecai acts as a veteran mentor who has seen too many people fail. He's tired of bureaucracy, blunt about your shortcomings, but ultimately wants you to succeed.

Behind the grumbling, Mordecai provides expert assistance on any topic—whether it's coding, writing, or cooking—because "shoddy work gets people killed."

## Features

- **The Mordecai Persona** - No cheerful AI platitudes here. Expect cynical wisdom, colorful language, and genuinely helpful advice delivered with veteran pragmatism.

- **Multi-Model Support** - Switch between Claude, GPT, and Gemini models via Vercel AI Gateway.

- **Document Artifacts** - Create and edit code snippets, text documents, and spreadsheets in a side panel while chatting.

- **Resumable Streams** - Conversations persist and can resume even if interrupted, powered by Redis.

- **Real-time Streaming** - Responses stream in as they're generated for a responsive experience.

## Tech Stack

| Layer | Technology |
|-------|------------|
| Framework | Next.js 16 (App Router) |
| AI | Vercel AI SDK + AI Gateway |
| Database | PostgreSQL + Drizzle ORM |
| Auth | Auth.js |
| Streaming | Redis (resumable streams) |
| Storage | Vercel Blob |
| Styling | Tailwind CSS + shadcn/ui |
| Linting | Ultracite (Biome-based) |

## Getting Started

### Prerequisites

- Node.js 18+
- pnpm 9+
- PostgreSQL database
- Redis (optional, for resumable streams)

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/mordecai.git
   cd mordecai
   ```

2. Install dependencies:
   ```bash
   pnpm install
   ```

3. Copy the example environment file and configure it:
   ```bash
   cp .env.example .env.local
   ```

4. Run database migrations:
   ```bash
   pnpm db:migrate
   ```

5. Start the development server:
   ```bash
   pnpm dev
   ```

The app will be running at [localhost:3000](http://localhost:3000).

## Environment Variables

### Required

| Variable | Description |
|----------|-------------|
| `AUTH_SECRET` | Secret key for session encryption |
| `POSTGRES_URL` | PostgreSQL connection string |
| `BLOB_READ_WRITE_TOKEN` | Vercel Blob storage token |

### Optional

| Variable | Description |
|----------|-------------|
| `AI_GATEWAY_API_KEY` | Required only for non-Vercel deployments |
| `REDIS_URL` | Enables resumable streams |

## Available Commands

```bash
pnpm dev              # Start development server (with Turbo)
pnpm build            # Build for production + run migrations
pnpm start            # Start production server
pnpm lint             # Check code with Ultracite
pnpm format           # Auto-fix code style issues
pnpm test             # Run Playwright E2E tests
pnpm db:migrate       # Apply database migrations
pnpm db:generate      # Generate migrations from schema changes
pnpm db:studio        # Open Drizzle Studio UI
```

## Deployment

### Vercel (Recommended)

The easiest way to deploy is with Vercel:

1. Push your code to GitHub
2. Import the project in Vercel
3. Configure environment variables
4. Deploy

Authentication with AI Gateway is handled automatically on Vercel via OIDC tokens.

### Other Platforms

For non-Vercel deployments, you'll need to:

1. Set the `AI_GATEWAY_API_KEY` environment variable
2. Ensure PostgreSQL and Redis (optional) are accessible
3. Run `pnpm build` and `pnpm start`

## Project Structure

```
├── app/
│   ├── (auth)/          # Authentication routes
│   └── (chat)/          # Chat interface and API routes
├── components/
│   └── ui/              # shadcn/ui primitives
├── lib/
│   ├── ai/
│   │   ├── models.ts    # Model definitions
│   │   ├── prompts.ts   # System prompts (Mordecai's personality)
│   │   ├── providers.ts # AI Gateway setup
│   │   └── tools/       # AI tools (weather, documents, suggestions)
│   └── db/
│       ├── schema.ts    # Database schema
│       └── queries.ts   # Database operations
└── tests/               # Playwright E2E tests
```

## License

MIT
