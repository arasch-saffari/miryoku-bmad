---
shard: 1
shard_title: "Project Overview + Technology Stack"
lines: "1-100"
size: "~10KB"
parent_document: "../project-context.md"
---

# Project Context - bmad-miryoku (miryoku.space)

**Purpose:** Comprehensive project context document for AI agents implementing code
**Last Updated:** 2026-01-06
**Shard:** 1 of 4 - Project Overview + Tech Stack

---

## Shard Scope

This shard contains:
- Project Overview (Vision, Goals, Target Users)
- Complete Technology Stack & Versions
  - Core Framework & Language (Next.js, React, TypeScript, Bun)
  - Visualization & Graphics (Three.js, Canvas, WebGL)
  - State Management (Zustand)
  - Data & Storage (IndexedDB, LocalStorage)
  - PWA & Performance, Analytics & Privacy
  - Styling & UI (Tailwind, shadcn/ui, Magic UI, Framer Motion, Lucide Animated)
  - Forms & Validation (React Hook Form + Zod)
  - Internationalization (next-intl)
  - Development Tools (Bun Test, Playwright, ESLint, Prettier)
  - Future Stack (Post-MVP enhancements)

**For other sections, see:** `index.md`

**Note:** This document focuses on **unobvious details that LLMs need to be reminded of** - not generic web development knowledge.

---
---
project_name: 'bmad-miryoku'
user_name: 'Arasch'
date: '2026-01-06'
sections_completed: ['discovery']
existing_patterns_found: 0
project_type: 'greenfield'
workflow: 'generate-project-context'
---

# Project Context for AI Agents

_This file contains critical rules and patterns that AI agents must follow when implementing code in this project. Focus on unobvious details that agents might otherwise miss._

---

## Project Overview

**miryoku.space** ist eine spezialisierte Lernplattform für das Miryoku-Ergonomic-Keyboard-Layout. Die Plattform macht das komplexe Zustandsmaschinen-System (36-Tasten-3x5+3-Matrix, 6 Funktions-Layer, Home-Row-Mods) durch Predictive State Visualization visuell zugänglich.

**Project Type:** Greenfield Web Application (EdTech)
**Mission:** RSI-Prävention und ergonomisches Tippen lernen
**Target Users:** Software-Developers, Content Creators, Gamers mit RSI-Problematik
**Language:** Deutsch/English bilingual
**Business Model:** Non-Profit mit Spenden (keine Paywalls)

---

## Technology Stack & Versions

### Core Framework & Language
- **Next.js 15+ (App Router)** - React Framework mit Server Components
- **React 19+** - UI Framework mit最新 Features
- **TypeScript 5+** - Type-safe development mit strict mode
- **Bun 1+** - Ultra-fast Package Manager, Runtime, and Test Runner

### Visualization & Graphics
- **Three.js (r150+)** - WebGL 3D Keyboard Visualization
- **Canvas API** - 2D Fallback für 60fps Animationen
- **WebHID API** - Direkte Hardware-Kommunikation (Chrome/Edge)
  - Firefox/Safari: Progressive Enhancement Fallback auf Canvas-basierte Visualisierung
- **React Three Fiber (@react-three/fiber)** - React Renderer für Three.js
- **@react-three/drei** - Useful Helpers für R3F

### State Management
- **Zustand 4+** - Lightweight state management mit TypeScript-first approach
- **React Context** - Für globale App-Konfiguration
- **Next.js Server Actions** - Für Server-side Mutationen (Enhanced Phase mit Supabase)

### Data & Storage
- **IndexedDB** - Client-first persistente Speicherung (User Progress, Gamification State, Settings)
- **LocalStorage** - Kleine Settings (Theme, Sound Toggle)
- **Export/Import JSON** - Manuelles Backup (User-kontrolliert, kein Cloud sync für MVP)

### PWA & Performance
- **next-pwa** - Service Worker für Offline-First (Enhanced Phase)
- **Next.js Image Optimization** - Automatische Bild-Optimierung
- **Turbopack** (via Bun) - Blazing-fast bundler für Development

### Analytics & Privacy
- **Plausible Analytics** - Privacy-first Analytics (optional cookie-less)
- **Matomo** - Self-hosted Alternative (GDPR-compliant)

### Styling & UI
- **Tailwind CSS 3+** - Utility-first CSS Framework
- **shadcn/ui** - High-quality React Components (built on Radix UI + Tailwind)
- **Magic UI** - Beeindruckende UI-Components mit Framer Motion (Ergänzung zu shadcn/ui)
  - Animated Buttons, Cards, Effects (Bento Grids, Particles, Marquee)
  - Perfect für "Wow Factor" in Landing Page & Gamification
- **Framer Motion** - Production-ready Motion Library für Smooth Animations
- **Lucide Animated** - Animierte Icons für lebendige UI (Standard lucide icons mit Motion)
  - Beispiele: Animated Heart (Gamification), Animated Star (Achievements)
  - Performance-optimiert via CSS animations (kein JavaScript overhead)
- **Lucide React** - Static Icon Library (Fallback für non-animated contexts)

### Forms & Validation
- **React Hook Form 7+** - Performant Forms mit minimal re-renders
- **Zod 3+** - TypeScript-first Schema Validation
- **@hookform/resolvers** - Zod resolver für React Hook Form

### Internationalization
- **next-intl** - Internationalization für Next.js App Router
  - Deutsch (Primary) - Alle UI Texte
  - English (Secondary) - Optional für internationale Users
  - Locale-aware Routing: `/de/learn`, `/en/learn`

### Development Tools
- **ESLint** - TypeScript/React/Next.js rules (@next/eslint-config)
- **Prettier** - Code formatting
- **Bun Test** - Ultra-fast Unit Testing (built-in, 10x faster than Jest/Vitest)
- **Playwright** - E2E Testing (Browser Automation)
- **TypeScript** - Strict mode configuration für Next.js

### Future Stack (Enhanced Phase, nicht für MVP)
- **Supabase** - Backend für Cloud Sync, User Accounts, Auth
- **PostgreSQL** - Database (Supabase managed)

---

## Critical Implementation Rules

---

**[Continue to Shard 2: Critical Rules 1-13 →](./02-critical-rules-1-13.md)**
