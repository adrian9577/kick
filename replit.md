# Overview

This is a real-time Kick.com multi-account detection application built with React and Express.js. The system monitors live chat streams from Kick.com channels and automatically detects when multiple user accounts share identical links in their channel descriptions, indicating potential multi-account violations. The application provides a dashboard with live chat feeds, user statistics, and instant alerts when duplicate accounts are detected.

## Recent Changes (Latest) - January 3, 2025
- **DEMO MODE COMPLETELY REMOVED** - All demo functionality removed, system only works with real data
- **ENHANCED POPUP NOTIFICATIONS** - Browser notifications with click-to-focus functionality  
- **IMPROVED AUDIO SYSTEM** - Polish voice "Wykryto multikonto" with enhanced debug logging
- **CRITICAL BLACK SCREEN BUG FIXED** - System properly displays duplicate tables without crashing
- **SINGLE DUPLICATE TABLES** - Each unique link shows only one table with all users grouped together
- **CLICKABLE USER LINKS** - User names link directly to /about pages with proper formatting
- **COMPLETE RESET AFTER REFRESH** - Single page refresh fully stops all monitoring and scraping
- **OAUTH AUTHENTICATION** - System uses Kick.com API credentials for authorized access
- **403 FORBIDDEN FIXED** - OAuth tokens resolve API access blocking issues  
- **ULTRA-FAST REAL-TIME** - 200ms polling for instant duplicate detection
- **INSTANT RESPONSE** - System processes every user immediately as they write in chat
- **CLEAN INTERFACE** - Removed all test modes, warnings fixed, only authentic data

# User Preferences

Preferred communication style: Simple, everyday language.

# System Architecture

## Frontend Architecture
- **Framework**: React 18 with TypeScript and Vite for development
- **UI Components**: Shadcn/ui component library built on Radix UI primitives
- **Styling**: Tailwind CSS with dark theme as default
- **State Management**: TanStack Query for server state management and caching
- **Routing**: Wouter for lightweight client-side routing
- **Real-time Communication**: WebSocket connection for live updates and alerts

## Backend Architecture
- **Runtime**: Node.js with Express.js server
- **WebSocket Server**: Built-in WebSocket server for real-time client communication
- **Data Storage**: In-memory storage with interface abstraction for future database integration
- **API Design**: REST endpoints for session management, chat messages, users, and duplicates
- **External API Integration**: Direct HTTP requests to Kick.com public API and WebSocket connections to chat servers

## Real-time Detection System
- **Chat Monitoring**: WebSocket connections to Kick.com chat servers for live message capture
- **Duplicate Detection**: Automatic analysis of user channel descriptions to find shared links
- **Alert System**: Instant notifications via WebSocket and audio alerts when duplicates are detected
- **Session Management**: Single active session support with automatic deactivation of previous sessions

## Data Models
- **Sessions**: Track active monitoring sessions with stream URLs and configuration
- **Chat Messages**: Store live chat messages with timestamps and user information
- **Kick Users**: Maintain user profiles with channel descriptions and extracted links
- **Duplicate Groups**: Group users sharing identical links for multi-account detection

## Build and Deployment
- **Development**: Vite dev server with HMR and Express API proxy
- **Production Build**: Vite builds React frontend, esbuild bundles Express server
- **Static Serving**: Express serves built React app in production mode

# External Dependencies

## Core Technologies
- **Neon Database**: PostgreSQL database service (configured but not actively used)
- **Drizzle ORM**: Database schema definition and query builder
- **WebSocket**: Real-time bidirectional communication between client and server

## Third-party Services
- **Kick.com API**: Public REST API for channel information and chat room details
- **Kick.com WebSocket**: Live chat message streaming from Kick.com chat servers

## UI and Development Tools
- **Radix UI**: Accessible component primitives for complex UI components
- **Lucide React**: Icon library for consistent iconography
- **TanStack Query**: Server state management with automatic caching and refetching
- **React Hook Form**: Form handling with validation support
- **Zod**: Runtime type validation for API requests and responses

## Audio and Notifications
- **Web Speech API**: Text-to-speech notifications for duplicate detection alerts
- **Web Audio API**: Fallback audio notifications using generated tones
- **Browser Notifications**: Desktop notification support (configurable)