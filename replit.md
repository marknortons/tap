# TapToMoon - Telegram Tap-to-Earn Game

## Overview

TapToMoon is a Telegram Mini App built as a tap-to-earn game inspired by popular crypto games like Hamster Kombat, NOTCOIN, Blum, and Catizen. Players tap to earn points, collect NFTs, invite friends for rewards, and purchase boosts using TON cryptocurrency. The application features a gamified experience with energy systems, daily challenges, NFT drops, and a comprehensive referral program.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Framework**: React 18+ with TypeScript running in a single-page application (SPA) architecture

**Routing**: Wouter for lightweight client-side routing with the following pages:
- Home (main tapping interface)
- Boosts (in-app purchase shop)
- Friends (referral system)
- NFTs (NFT collection and drops)
- Profile (user statistics)
- Daily Combo (daily challenge)

**State Management**: 
- TanStack Query (React Query) for server state management and caching
- React Context for Telegram WebApp integration
- Local component state for UI interactions

**UI Component Library**: Shadcn/ui (Radix UI primitives) with custom theming
- Uses the "new-york" style variant
- Dark mode design system with gaming aesthetics
- Custom CSS variables for theming via HSL color space

**Styling**: 
- TailwindCSS for utility-first styling
- Custom design system following gaming UI patterns (see design_guidelines.md)
- Typography uses Inter for body text and Rajdhani for gaming/accent text
- Dark theme with high-energy visuals and celebratory animations

**Animation Libraries**:
- Canvas Confetti for celebration effects
- Framer Motion integration (implied by design guidelines)

**Key Frontend Patterns**:
- Query invalidation for real-time data updates
- Optimistic updates for tap interactions
- Energy recovery calculated client-side with server reconciliation
- Toast notifications for user feedback

### Backend Architecture

**Runtime**: Node.js with Express.js server

**Development vs Production**:
- Development: Vite dev server with HMR middleware
- Production: Static file serving from pre-built dist directory

**API Structure**: RESTful JSON API with the following endpoints:
- `GET /api/user` - Fetch user data by Telegram ID
- `POST /api/tap` - Register tap action and update points/energy
- `GET /api/referrals` - Get list of referred users
- `GET /api/nfts` - Get user's NFT collection
- `GET /api/daily-combo` - Get daily combo challenge status
- `POST /api/daily-combo` - Submit daily combo completion

**Session Management**: Connect-pg-simple for PostgreSQL-backed sessions

**Storage Layer**: Abstracted through an `IStorage` interface with two implementations:
- `MemStorage`: In-memory storage for development/testing
- Database storage (implied by Drizzle configuration)

**Data Models** (defined in shared/schema.ts):
- Users: Core player data including points, energy, levels, referral info
- Boosts: Purchased power-ups with expiration times
- NFTs: Collected items with rarity tiers (Common, Rare, Epic, Legendary)
- Daily Combos: Daily challenge completion tracking
- NFT Drops: 24-hour cooldown tracking for free NFT drops

**Game Logic**:
- Energy system: 1000 base capacity, 6 energy/second recovery rate
- Multitap multiplier system (upgradeable levels)
- Energy limit scaling based on user level
- NFT drop probability system with rarity tiers
- Referral reward calculation (25% of referrals' earnings)

### Data Storage Solutions

**Database**: PostgreSQL (configured via Neon serverless driver)
- Schema managed by Drizzle ORM
- Migration files stored in `/migrations` directory
- Schema definitions in TypeScript for type safety

**ORM**: Drizzle ORM for type-safe database queries
- PostgreSQL dialect
- Schema-first approach with `drizzle-zod` for validation

**Session Store**: PostgreSQL-backed sessions via connect-pg-simple

### Authentication and Authorization

**Telegram WebApp Authentication**:
- Uses Telegram's WebApp API (`@twa-dev/sdk`)
- Authenticates users via Telegram's initData
- Extracts user information from Telegram WebApp context
- Fallback to mock user for development outside Telegram

**User Identification**: 
- Primary key: UUID
- Telegram ID for lookup and authentication
- Referral codes generated for user acquisition tracking

**No traditional auth required** - relies entirely on Telegram's WebApp security model

### External Dependencies

**Telegram Platform**:
- Telegram WebApp API for mini-app integration
- User authentication and profile data from Telegram
- Deep linking for referral system (`https://t.me/TapToMoonBot?start={code}`)

**TON Blockchain** (planned integration):
- TON Connect v2 for wallet connections
- Tonkeeper/Tonhub wallet compatibility
- TON cryptocurrency payments for boost purchases
- Jetton transfers for instant payments

**Third-Party Services**:
- Google Fonts: Inter and Rajdhani font families
- Neon Database: Serverless PostgreSQL hosting

**Key NPM Dependencies**:
- `@tanstack/react-query`: Server state management
- `@radix-ui/*`: Headless UI component primitives
- `drizzle-orm`: Type-safe database ORM
- `@neondatabase/serverless`: Neon PostgreSQL client
- `canvas-confetti`: Celebration animations
- `wouter`: Lightweight routing
- `class-variance-authority`: Component variant styling
- `tailwindcss`: Utility-first CSS framework

**Development Tools**:
- Vite: Build tool and dev server
- TypeScript: Type safety across the stack
- ESBuild: Production bundling
- Replit plugins: Development experience enhancements

**Monetization Integration Points**:
- Boost shop with TON pricing (0.05 - 10 TON range)
- NFT guaranteed drop tickets
- Energy refills and multiplier boosts
- Referral cashback system (20% of referral purchases)