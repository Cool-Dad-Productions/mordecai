# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Build & Development Commands

```bash
pnpm install          # Install dependencies
pnpm dev              # Start development server (Next.js with Turbo)
pnpm build            # Build app + run DB migrations
pnpm lint             # Check code with Ultracite (Biome-based)
pnpm format           # Auto-fix code with Ultracite
pnpm test             # Run Playwright E2E tests
pnpm db:migrate       # Apply database migrations
pnpm db:generate      # Generate new DB migrations from schema changes
pnpm db:studio        # Open Drizzle Studio UI
```

## Architecture Overview

This is the **Chat SDK** - an AI chatbot built with Next.js 16, Vercel AI SDK, and multi-model support via Vercel AI Gateway.

### Key Directories

- `/app` - Next.js App Router (server components by default)
  - `/(auth)` - Authentication routes
  - `/(chat)` - Main chat interface and API routes
- `/lib/ai` - AI integration layer
  - `models.ts` - Model definitions (Claude, GPT, Gemini, Grok)
  - `providers.ts` - AI Gateway provider setup
  - `prompts.ts` - System prompts
  - `tools/` - AI tools (weather, document creation/updates, suggestions)
- `/lib/db` - Database layer (PostgreSQL + Drizzle ORM)
  - `schema.ts` - Database schema
  - `queries.ts` - Database operations
- `/components` - React components
  - `/ui` - shadcn/ui primitives (excluded from linting)
- `/tests` - Playwright E2E tests

### Data Flow

1. User submits message via `MultimodalInput` component
2. `POST /api/chat` handles the request with streaming
3. AI Gateway routes to selected model (default: Gemini 2.5 Flash Lite)
4. AI can use tools: `getWeather`, `createDocument`, `updateDocument`, `requestSuggestions`
5. Messages stored in PostgreSQL, streams can be resumed via Redis

### Database Schema

Core tables: `User`, `Chat`, `Message_v2` (messages with parts/attachments), `Document`, `Suggestion`, `Vote`, `Stream`

## Code Style (Ultracite/Biome)

The project uses Ultracite for formatting/linting. Key rules:

- No `any` type, no non-null assertions (`!`)
- No TypeScript enums (use `as const`)
- Arrow functions over function expressions
- `const` by default, no `var`
- `===` equality checks
- No console usage (except tests)
- Use `import type` and `export type` for types
- For accessibility: meaningful alt text, proper ARIA roles, keyboard handlers

Run `pnpm format` to auto-fix issues before committing.

## Testing

E2E tests use Playwright with test IDs like `[data-testid="multimodal-input"]`, `[data-testid="send-button"]`.

Mock models are used in test environments (detected via `process.env.PLAYWRIGHT`).

## Environment Variables

Required in `.env.local`:
- `AUTH_SECRET` - Session encryption key
- `POSTGRES_URL` - PostgreSQL connection string
- `BLOB_READ_WRITE_TOKEN` - Vercel Blob storage token
- `AI_GATEWAY_API_KEY` - Required for non-Vercel deployments only
- `REDIS_URL` - Optional, for resumable streams
