# POS SaaS – Weekly SDLC Task Checklist

> Constraints:
>
> - Solo developer
> - Full-time job
> - ~6–10 hours/week
> - Spare-time development
> - Goal: Offline-first, multi-tenant POS SaaS

---

## Phase 0 — Grounding & Direction

### Week 1 — Product Definition

- [ ] Choose first target industry (retail / fashion recommended)
- [ ] Write 1-page product vision
- [ ] Define core problem statements
- [ ] Define MVP must-have features
- [ ] Define explicit non-goals
- [ ] Define offline-first scope for MVP
- [ ] Create monorepo Git repository

**Output:** `docs/vision.md`

---

### Week 2 — Market & Technical Research

- [ ] Analyze Moka POS features
- [ ] Identify Moka POS gaps
- [ ] Research offline POS failures in Indonesia
- [ ] Finalize tech stack
  - [ ] NestJS
  - [ ] Next.js
  - [ ] PostgreSQL
  - [ ] IndexedDB
- [ ] Decide monorepo tooling (Nx)
- [ ] Define MVP success criteria

**Output:** `docs/mvp-definition.md`

---

## Phase 1 — Architecture & Design

### Week 3 — System Architecture

- [ ] Define high-level architecture
- [ ] Define multi-tenant strategy
- [ ] Define subdomain routing strategy
- [ ] Define custom domain support (conceptual)
- [ ] Define authentication approach
- [ ] Define service boundaries
- [ ] Draw C4 Context Diagram
- [ ] Draw C4 Container Diagram

**Output:** `docs/architecture.md`

---

### Week 4 — Database & RBAC Design

- [ ] Design core tables:
  - [ ] Tenant
  - [ ] User
  - [ ] Role
  - [ ] Permission
  - [ ] Outlet
  - [ ] Product
  - [ ] Inventory
  - [ ] Transaction
- [ ] Design tenant isolation rules
- [ ] Design RBAC model
- [ ] Define audit log strategy
- [ ] Write schema (SQL / DBML)

**Output:** `docs/database.md`

---

### Week 5 — Offline-First Design

- [ ] Define offline data model
- [ ] Define sync strategy
- [ ] Define conflict resolution rules
- [ ] Define command/event queue
- [ ] Define online vs offline feature split
- [ ] Write offline sync flow

**Output:** `docs/offline-strategy.md`

---

## Phase 2 — Foundation Implementation

### Week 6 — Monorepo Setup (Nx)

- [ ] Initialize Nx workspace
- [ ] Create `api` app (NestJS)
- [ ] Create `web` app (Next.js)
- [ ] Create shared libs:
  - [ ] auth
  - [ ] types
  - [ ] utils
- [ ] Setup linting & formatting
- [ ] Setup environment configuration

**Output:** Apps run locally

---

### Week 7 — Authentication & Tenant Core

- [ ] User registration
- [ ] Tenant creation
- [ ] Login / logout
- [ ] JWT + refresh tokens
- [ ] Tenant context middleware
- [ ] Subdomain-to-tenant resolution

**Output:** Auth flow works

---

### Week 8 — RBAC Implementation

- [ ] Role CRUD
- [ ] Permission definitions
- [ ] Role-permission mapping
- [ ] Authorization guards
- [ ] Seed default roles
- [ ] Basic admin UI for roles

**Output:** RBAC enforced

---

### Week 9 — Core POS Backend

- [ ] Product CRUD
- [ ] Category management
- [ ] Inventory tracking
- [ ] Outlet support
- [ ] Transaction model
- [ ] API tests for POS flows

**Output:** POS backend usable

---

### Week 10 — Core POS Frontend

- [ ] Login UI
- [ ] Product list UI
- [ ] Cart UI
- [ ] Checkout flow
- [ ] Transaction history
- [ ] Error handling

**Output:** Online POS flow end-to-end

---

## Phase 3 — Offline-First MVP

### Week 11 — Offline Data Layer

- [ ] IndexedDB schema
- [ ] Product local cache
- [ ] Transaction local store
- [ ] Sync status indicator
- [ ] Network detection

---

### Week 12 — Offline Transactions

- [ ] Offline checkout
- [ ] Queue transactions
- [ ] Local receipt handling
- [ ] Idempotent transaction IDs
- [ ] Manual sync trigger

---

### Week 13 — Sync Engine

- [ ] Background sync
- [ ] Retry strategy
- [ ] Conflict resolution handling
- [ ] Idempotency enforcement
- [ ] Sync logging

---

### Week 14 — Offline QA

- [ ] Test network loss scenarios
- [ ] Test conflict scenarios
- [ ] Verify data consistency
- [ ] UX polish for offline mode

**Output:** Reliable offline POS

---

## Phase 4 — Hardening & MVP Release

### Week 15 — Security & Stability

- [ ] Input validation
- [ ] Rate limiting
- [ ] Audit logging
- [ ] Error monitoring
- [ ] Backup strategy

---

### Week 16 — Multi-Tenant Polish

- [ ] Tenant switching
- [ ] Basic custom domain support
- [ ] Tenant branding (logo, name)
- [ ] Subscription flag (mocked)

---

### Week 17 — Deployment

- [ ] CI pipeline
- [ ] Docker setup
- [ ] Staging environment
- [ ] Production environment
- [ ] SSL configuration

---

### Week 18 — MVP Launch

- [ ] Documentation
- [ ] Demo tenant
- [ ] Feedback collection
- [ ] Known issues list
- [ ] Decide next industry module

---

## Development Rules

- One weekly deliverable
- No refactor before MVP
- No new features outside checklist
- Skip weeks if needed — do not quit
