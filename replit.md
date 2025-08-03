# Overview

This is a word search puzzle game application built with a modern full-stack architecture. The game features Indonesian words displayed in a grid format where players must find hidden words by clicking and dragging to select them. The application supports multiple difficulty levels (easy, medium, hard) with varying grid sizes and word counts, includes player progress tracking, game statistics, and a complete scoring system with timer functionality.

# User Preferences

Preferred communication style: Simple, everyday language.

# System Architecture

## Frontend Architecture

The client-side is built as a React SPA using Vite as the build tool and bundler. The application follows a component-based architecture with:

- **UI Framework**: React with TypeScript for type safety
- **Styling**: Tailwind CSS with shadcn/ui component library for consistent design system
- **State Management**: React hooks with custom game state management via `useGameState` hook
- **Routing**: Wouter for lightweight client-side routing
- **Data Fetching**: TanStack Query (React Query) for server state management and caching
- **Form Handling**: React Hook Form with Zod validation schemas
- **Toast Notifications**: Radix UI toast system for user feedback

The game logic is encapsulated in custom hooks (`useGameState`, `useTimer`) and utility functions that handle word search grid generation, word placement algorithms, and game mechanics.

## Backend Architecture

The server is built with Express.js following a RESTful API pattern:

- **Framework**: Express.js with TypeScript
- **Development**: Uses tsx for TypeScript execution in development
- **API Structure**: RESTful endpoints under `/api` prefix for player progress and game statistics
- **Error Handling**: Centralized error middleware with proper HTTP status codes
- **Logging**: Custom request/response logging middleware for API endpoints

The backend provides endpoints for player progress management and game statistics tracking, with in-memory storage as the default implementation.

## Data Storage Architecture

The application uses a flexible storage abstraction pattern:

- **ORM**: Drizzle ORM with PostgreSQL dialect for type-safe database operations
- **Database**: Configured for PostgreSQL via Neon serverless
- **Schema Management**: Drizzle migrations with shared schema definitions
- **Fallback Storage**: In-memory storage implementation for development/testing
- **Data Models**: Player progress tracking, game statistics, and session management

The storage layer is abstracted through an interface (`IStorage`) allowing for easy switching between different storage implementations.

## Authentication & Session Management

The application includes session management infrastructure:

- **Session Storage**: PostgreSQL-based session store using `connect-pg-simple`
- **Player Identification**: Player-based progress tracking without traditional authentication
- **Progress Persistence**: Automatic save/load of player progress and game state

## Build & Deployment Architecture

- **Development**: Vite dev server with HMR for frontend, tsx for backend development
- **Production Build**: Vite builds the client, esbuild bundles the server
- **Asset Management**: Static file serving through Express in production
- **Environment Configuration**: Environment variable-based configuration for database and deployment settings

# External Dependencies

## Core Frameworks
- **React 18**: Frontend UI library
- **Express.js**: Backend web framework
- **Vite**: Frontend build tool and development server
- **TypeScript**: Type safety across the entire stack

## Database & ORM
- **@neondatabase/serverless**: Neon PostgreSQL serverless driver
- **drizzle-orm**: Type-safe ORM for database operations
- **drizzle-kit**: Database migrations and schema management
- **connect-pg-simple**: PostgreSQL session store for Express sessions

## UI Components & Styling
- **@radix-ui/***: Comprehensive set of accessible UI primitives (dialogs, dropdowns, forms, etc.)
- **tailwindcss**: Utility-first CSS framework
- **class-variance-authority**: Component variant management
- **clsx**: Conditional className utility

## State Management & Data Fetching
- **@tanstack/react-query**: Server state management and caching
- **wouter**: Lightweight React router
- **react-hook-form**: Form state management and validation
- **@hookform/resolvers**: Form validation resolvers

## Game-Specific Libraries
- **date-fns**: Date manipulation for timers and scoring
- **nanoid**: Unique ID generation for game sessions
- **zod**: Runtime type validation and schema definition

## Development Tools
- **@replit/vite-plugin-runtime-error-modal**: Development error overlay
- **@replit/vite-plugin-cartographer**: Replit-specific development tools
- **embla-carousel-react**: Carousel component for UI

The application is designed to be deployed on Replit with specific optimizations for that environment, including development banners and error handling.