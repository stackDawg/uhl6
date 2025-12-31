# replit.md

## Overview

This is an interactive love letter web application built with React and Express. The app displays an animated, typewriter-style letter with background music and visual effects (confetti). It features a multi-stage experience: initial view, letter opening animation, reading phase with typewriter effect, and a final celebration screen with a heart icon.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Routing**: Wouter (lightweight React router)
- **State Management**: TanStack React Query for server state
- **Styling**: Tailwind CSS with shadcn/ui component library (New York style)
- **Animations**: Framer Motion for page transitions and animations
- **Audio**: use-sound hook for background music playback
- **Effects**: canvas-confetti for celebration effects
- **Build Tool**: Vite with React plugin

### Backend Architecture
- **Framework**: Express.js with TypeScript
- **Runtime**: Node.js with tsx for TypeScript execution
- **API Pattern**: REST endpoints defined in shared route definitions
- **Database ORM**: Drizzle ORM with PostgreSQL dialect
- **Schema Validation**: Zod with drizzle-zod integration

### Project Structure
```
├── client/           # React frontend
│   └── src/
│       ├── components/ui/  # shadcn/ui components
│       ├── pages/          # Page components
│       ├── hooks/          # Custom React hooks
│       └── lib/            # Utilities and query client
├── server/           # Express backend
│   ├── routes.ts     # API route definitions
│   ├── storage.ts    # Database operations
│   └── db.ts         # Database connection
├── shared/           # Shared types and schemas
│   ├── schema.ts     # Drizzle database schema
│   └── routes.ts     # API route type definitions
└── api/              # Vercel serverless function entry
```

### Data Flow
1. Frontend makes API calls via TanStack Query
2. Express routes validate input with Zod schemas
3. Storage layer handles database operations via Drizzle ORM
4. Shared schema ensures type safety across client and server

### Key Design Decisions
- **Monorepo structure**: Client, server, and shared code in single repository for easier type sharing
- **Type-safe API**: Route definitions in shared folder ensure frontend/backend type consistency
- **Component library**: shadcn/ui provides accessible, customizable components
- **Path aliases**: `@/` for client, `@shared/` for shared, `@assets/` for static assets

## External Dependencies

### Database
- **PostgreSQL**: Primary database via `DATABASE_URL` environment variable
- **Drizzle ORM**: Type-safe database queries and migrations
- **connect-pg-simple**: PostgreSQL session store (available but may not be active)

### Build & Deployment
- **Vite**: Frontend bundling with HMR support
- **esbuild**: Server bundling for production
- **Vercel**: Deployment target with serverless functions support

### UI & Animation Libraries
- **Radix UI**: Headless UI primitives (accordion, dialog, dropdown, etc.)
- **Framer Motion**: Animation library for React
- **Lucide React**: Icon library
- **canvas-confetti**: Confetti celebration effects

### Development Tools
- **TypeScript**: Full type safety across the stack
- **Tailwind CSS**: Utility-first CSS framework
- **PostCSS/Autoprefixer**: CSS processing

### Environment Variables Required
- `DATABASE_URL`: PostgreSQL connection string (required for database operations)