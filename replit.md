# replit.md

## Overview

SwapSavvy is a decentralized skill-swapping platform that allows users to exchange knowledge and skills using a token-based economy. Users can earn "SkillCoins" by teaching others and spend them to learn new skills. The platform features AI-powered matching, NFT certificates for achievements, and a comprehensive review system.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

This is a full-stack web application built with modern technologies:

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite for fast development and optimized builds
- **Routing**: Wouter for client-side routing
- **State Management**: React Query (@tanstack/react-query) for server state
- **UI Framework**: Shadcn/ui components built on Radix UI primitives
- **Styling**: Tailwind CSS with CSS variables for theming
- **Form Handling**: React Hook Form with Zod validation

### Backend Architecture
- **Runtime**: Node.js with Express.js server
- **Language**: TypeScript with ES modules
- **Database**: PostgreSQL with Drizzle ORM
- **Database Provider**: Neon Database (@neondatabase/serverless)
- **Authentication**: Replit Auth with OpenID Connect
- **Session Management**: Express sessions with PostgreSQL store

### Build and Development
- **Development**: Single command (`npm run dev`) starts both frontend and backend
- **Production**: Vite builds frontend, esbuild bundles backend
- **Type Safety**: Shared TypeScript schemas between frontend and backend

## Key Components

### Authentication System
- **Provider**: Replit Auth integration with passport.js
- **Session Storage**: PostgreSQL-backed sessions with `connect-pg-simple`
- **Security**: HTTP-only cookies, CSRF protection, secure session management
- **User Management**: Automatic user creation/update on authentication

### Database Schema
The application uses a comprehensive PostgreSQL schema with the following main entities:
- **Users**: Profile information, skill coin balance, ratings
- **Skills**: Categorized skill catalog
- **UserSkills**: User's offered/sought skills with proficiency levels
- **SkillExchanges**: Matching and exchange requests between users
- **SkillCoinTransactions**: Token economy transaction history
- **NFTBadges**: Achievement certificates and credentials
- **Reviews**: User feedback and rating system
- **Notifications**: In-app messaging and alerts

### API Architecture
- **RESTful Design**: Express routes with proper HTTP methods
- **Validation**: Zod schemas for request/response validation
- **Error Handling**: Centralized error middleware
- **Authentication Middleware**: Route-level authentication guards

### Frontend Structure
- **Component Architecture**: Reusable UI components with proper separation
- **Page Routing**: Protected routes with authentication checks
- **State Management**: Server state via React Query, local state via React hooks
- **TypeScript Integration**: Full type safety with shared schemas

## Data Flow

1. **Authentication**: Users authenticate via Replit Auth, sessions stored in PostgreSQL
2. **User Onboarding**: Profile creation and skill registration
3. **Skill Matching**: AI-powered algorithm matches users based on complementary skills
4. **Exchange Process**: Users request skill swaps, negotiate terms, and confirm exchanges
5. **Token Economy**: SkillCoins are earned by teaching and spent on learning
6. **Achievement System**: NFT badges awarded for milestones and completed exchanges
7. **Review System**: Post-exchange feedback maintains quality and trust

## External Dependencies

### Core Dependencies
- **Database**: Neon PostgreSQL (serverless)
- **Authentication**: Replit Auth/OpenID Connect
- **UI Components**: Radix UI primitives
- **Validation**: Zod for schema validation
- **Date Handling**: date-fns for date operations

### Development Tools
- **TypeScript**: Full type safety across the stack
- **Vite**: Fast development server and build tool
- **Tailwind CSS**: Utility-first styling
- **Drizzle**: Type-safe SQL query builder and migrations

### Replit Integration
- **Development Banner**: Replit development environment integration
- **Cartographer**: Replit's code navigation tool (development only)
- **Runtime Error Overlay**: Development error handling

## Deployment Strategy

### Production Build
- **Frontend**: Vite builds optimized static assets to `dist/public`
- **Backend**: esbuild bundles server code to `dist/index.js`
- **Database**: Drizzle migrations handle schema updates

### Environment Configuration
- **Database**: Requires `DATABASE_URL` environment variable
- **Authentication**: Requires Replit Auth configuration (`REPL_ID`, `SESSION_SECRET`)
- **Development**: Uses Vite dev server with Express backend
- **Production**: Serves static files through Express

### Scalability Considerations
- **Database**: Uses connection pooling with Neon serverless PostgreSQL
- **Authentication**: Stateless JWT-like approach with Replit Auth
- **Frontend**: Static asset serving with CDN-friendly builds
- **Backend**: Stateless Express server suitable for horizontal scaling

The architecture prioritizes developer experience with hot reloading, type safety, and modern tooling while maintaining production readiness with proper security, error handling, and scalability patterns.