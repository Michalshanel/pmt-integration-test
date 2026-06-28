# Engineering Architecture Guide

## Overview
The Patient Portal v2 is a Next.js 16 application with server-side rendering, deployed on Vercel, backed by a PostgreSQL database via Prisma.

## Tech Stack
- **Frontend**: Next.js 16 (App Router), React 19, Tailwind CSS, shadcn/ui
- **Backend**: Next.js Server Actions, Prisma ORM
- **Auth**: Custom SSO via insurance ID provider federation
- **Video**: Daily.co WebRTC SDK
- **Infra**: Vercel (preview + prod), GitHub Actions CI

## Key Directories
```
app/
  (auth)/          # Login, SSO callback
  dashboard/       # Patient home
  claims/          # Claims list + detail
  benefits/        # Coverage summary
  telehealth/      # Video booking + messaging
  settings/        # Profile, notifications, security
lib/
  actions/         # Server Actions
  db.ts            # Prisma client
components/
  ui/              # shadcn/ui primitives
  layout/          # Shell, sidebar, tabs
  claims/          # Domain components
```

## Data Flow
All data mutations go through Server Actions in `lib/actions/`. Client components call actions directly — no REST API layer for internal data. External APIs (claims, benefits, eligibility) are consumed in Server Components only to prevent token exposure.

## Environments
| Env | URL | Branch |
|-----|-----|--------|
| Production | portal.greenbackhealth.com | main |
| Staging | portal-staging.greenbackhealth.com | staging |
| Preview | auto-generated | any PR |