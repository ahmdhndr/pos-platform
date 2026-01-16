# 🚀 Solo-Dev POS Roadmap (Lean Edition)

> **Constraints:**
>
> - 1 Developer | Full-time job elsewhere
> - 6–10 hours per week
> - Goal: Functional Multi-tenant POS (Apotek/Retail focused)

---

## Phase 1 — Grounding & Foundation (Weeks 1–3)

**Focus:** Lock in decisions and set up the "Empty Shell."

### Week 1: Product & Repo Setup

- [ ] Finalize **1-page Vision** (Adaptive Strategy Pattern).
- [ ] Initialize Repository: Standard `/api` and `/web` folders.
- [ ] Tech Stack Init: NestJS (Backend), Next.js (Frontend), Tailwind CSS.
- [ ] **Output:** Apps running locally and talking to each other.

### Week 2: Data & Isolation Design

- [ ] Finalize **DBML Schema**: (Core tables: Tenants, Users, Products, Orders).
- [ ] Define **Isolation Strategy**: Implement PostgreSQL Schema-per-tenant logic.
- [ ] Hardcode RBAC: Define `OWNER`, `MANAGER`, `CASHIER` constants.
- [ ] **Output:** Database migrations for the "Public" schema.

### Week 3: Minimalist Offline Strategy

- [ ] Define Offline Scope: Sync only `Products` and `Orders`.
- [ ] Strategy: **Last-Write-Wins** for conflict resolution.
- [ ] Sync UI: Design a simple "Online/Offline" status indicator.
- [ ] **Output:** `docs/sync-logic.md` (A simple 1-page flow).

---

## Phase 2 — The Core Engine (Weeks 4–7)

**Focus:** Building the actual SaaS "Magic."

### Week 4: Auth & Tenant Middleware

- [ ] JWT Login/Logout Flow.
- [ ] **Tenant Middleware**: Subdomain-to-Schema resolution logic.
- [ ] **Output:** `tenant1.app.local` and `tenant2.app.local` show different data.

### Week 5: Core POS API

- [ ] Product CRUD: Support for JSONB (Industry-specific metadata).
- [ ] Basic Inventory: Stock increment/decrement logic.
- [ ] **Output:** Working API for managing a store catalog.

### Week 6: The Cashier UI (Frontend)

- [ ] Product Grid: Search and Filter by category.
- [ ] Cart Logic: Add/Remove/Update quantities (Client-side state).
- [ ] **Output:** A functional "Scanning" experience on the web.

### Week 7: Receipts & Payments

- [ ] **Receipt Engine**: HTML template for ESC/POS printing.
- [ ] Payment Selector: Toggle between Cash and QRIS (Mocked).
- [ ] **Output:** End-to-end "Online" checkout flow.

---

## Phase 3 — The Offline Edge (Weeks 8–11)

**Focus:** Making the app resilient for the Indonesian market.

### Week 8: Local Storage (IndexedDB)

- [ ] Setup **Dexie.js** in the frontend.
- [ ] Data Mirroring: Seed local DB with Product data on login.
- [ ] **Output:** Products visible even when Wi-Fi is toggled off.

### Week 9: Offline Transactions

- [ ] Local Checkout: Save orders to an "Outbox" in IndexedDB.
- [ ] UUID Generation: Ensure order IDs don't collide when syncing.
- [ ] **Output:** Ability to "Complete Sale" while offline.

### Week 10: The Sync Engine

- [ ] Background Sync: Automatic push of "Outbox" orders when online.
- [ ] Basic Conflict handling: Server rejects duplicates based on UUID.
- [ ] **Output:** Data consistency between Browser and Server.

### Week 11: Deployment & CI/CD

- [ ] VPS Setup: Hostinger + Nginx + PM2.
- [ ] **GitHub Actions**: Automated `git push` to deploy.
- [ ] SSL: Setup Let's Encrypt for subdomains.
- [ ] **Output:** Live URL accessible to the world.

---

## 🛠️ Solo-Dev "Survival" Rules

1. **No Over-Engineering**: If you spend more than 2 hours configuring a tool (like Docker or Nx), stop and use the simplest version.
2. **Feature Freeze**: No new "cool ideas" until the Cashier can finish a sale.
3. **Weekly Win**: If you only have 6 hours, finish **one** checkbox completely rather than starting three.
