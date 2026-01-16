# Multi-Tenant Architecture Definition

## Goal

Ensure strict data isolation between tenants while allowing
the system to scale efficiently in a single SaaS deployment.

---

## Tenant Definition

A tenant represents one business entity subscribing to the platform.

A tenant owns:

- Users
- Outlets
- Products
- Inventory
- Transactions
- Configuration and branding

---

## Tenant Identification Strategy

### Primary Identifier

- `tenant_id` (UUID, immutable)

### Request Resolution

Tenant is resolved from subdomain

<!-- 2. Custom domain (optional, paid tier) -->

Example:

- agamdinamo.posapp.com → tenant_id = `uuid-42`
- queeniza.posapp.com -> tenant_id = `uuid-45`

---

## Architecture Choice

### Selected Model

Shared database, tenant-scoped rows

Rationale:

- Lower operational cost
- Easier schema evolution
- Suitable for MVP and early scale

---

## Database Enforcement

### Mandatory Rule

Every business table MUST include `tenant_id`.

Example tables:

tenants

- id (PK)
- name
- subdomain
- custom_domain
- status

users

- id (PK)
- tenant_id (FK)
- email
- password_hash
- role_id

products

- id (PK)
- tenant_id (FK)
- name
- price
- sku

transactions

- id (PK)
- tenant_id (FK)
- outlet_id
- total_amount
- created_at

---

## Application Enforcement

### Tenant Context

- Tenant is resolved once per request
- Tenant context is injected into request lifecycle
- No repository/query may execute without tenant scope

Example rule:

- Any query without tenant filter is invalid

---

## Security Guarantees

- No cross-tenant queries
- No shared identifiers exposed across tenants
- No global admin bypass in MVP

---

## Explicit Non-Goals

- Separate database per tenant
- Cross-tenant reporting
- Tenant-to-tenant data sharing

---

## Success Criteria

- Tenant A cannot access Tenant B data under any circumstance
- Tenant resolution is deterministic and auditable
