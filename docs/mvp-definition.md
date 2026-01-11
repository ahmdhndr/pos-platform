# MVP Definition

## MVP Goal

Deliver a production-ready POS system that proves:

- Offline-first reliability
- Multi-tenant SaaS architecture
- End-to-end POS flow works under real-world constraints

---

## Target Industry (MVP)

Retail / Fashion

Reason:

- Simple transaction model
- SKU-based inventory
- Common use case in Indonesia
- Clear validation of offline reliability

---

## MVP Core Capabilities

### 1. Multi-Tenant SaaS

- Tenant isolation at database and application level
- Each tenant has:
  - Subdomain-based access
  - Multiple outlets
- Basic tenant branding (name, logo)

---

### 2. Authentication & Authorization

- User authentication (email/password)
- JWT-based session handling
- Role-Based Access Control (RBAC)
- Default roles:
  - Owner
  - Manager
  - Cashier

---

### 3. POS Core Features

- Product management
- Category management
- Inventory tracking per outlet
- Simple pricing (no complex promos)
- Transaction processing
- Transaction history

---

### 4. Offline-First Support

- Full checkout flow works offline
- Local storage using IndexedDB
- Offline transaction queue
- Visual offline/online indicator
- Manual and automatic sync

---

### 5. Sync & Consistency

- Idempotent transaction syncing
- Conflict detection and resolution
- Retry mechanism for failed syncs
- Audit trail for synced data

---

## Explicit MVP Exclusions

- Accounting exports
- Tax automation
- QRIS / payment gateway integration
- Purchase orders
- Supplier management
- Multi-currency support

---

## MVP Success Metrics

The MVP is successful if:

- Zero data loss during offline operation
- Transactions sync without duplication
- System remains usable under poor connectivity
- Core POS workflow feels stable and predictable

---

## Technical Constraints

- Monorepo using Nx
- Backend: NestJS
- Frontend: Next.js
- Database: PostgreSQL
- Offline storage: IndexedDB
- Deployment: Cloud-based, containerized

---

## Validation Strategy

- Internal dogfooding
- Simulated network outages
- One pilot tenant (non-paying)
- Feedback focused on reliability, not features
