# Offline-First Sync Strategy

## Goal

Allow uninterrupted POS operation during network outages
without data loss or duplication.

---

## Offline Definition

The application must function correctly when:

- Network is unavailable
- Network is unstable
- Server is temporarily unreachable

---

## Offline Capabilities (MVP)

Available offline:

- Product listing
- Checkout
- Transaction creation
- Receipt generation

Unavailable offline:

- Reporting dashboards
- User management
- Configuration changes

---

## Local Data Storage

### Storage Technology

IndexedDB (browser)

### Local Stores

- products
- transactions
- sync_queue
- metadata

---

## Transaction Flow (Offline)

1. Cashier completes checkout
2. Transaction is saved locally
3. A sync command is created
4. UI reflects offline status

Example sync command:

{
"command_id": "uuid",
"type": "CREATE_TRANSACTION",
"entity_id": "transaction-uuid",
"payload": { ... },
"status": "PENDING",
"created_at": "timestamp"
}

---

## Sync Trigger

Sync occurs when:

- Network connectivity is restored
- User manually triggers sync

---

## Sync Processing Rules

- Commands are processed sequentially
- Commands are retried on failure
- Sync is resumable

---

## Idempotency Strategy

Rule:

- Server must treat all commands as idempotent

Mechanism:

- Each transaction has a globally unique ID
- Server stores processed command IDs
- Duplicate commands are ignored safely

---

## Conflict Handling

### Inventory Conflict Example

- Local stock = 5
- Server stock = 2

Resolution (MVP):

- Allow sale
- Allow negative inventory
- Flag for reconciliation

No automatic rollback.

---

## Failure Handling

- Partial sync is allowed
- Failed commands remain in queue
- User is notified of unresolved sync issues

---

## UX Requirements

- Clear offline indicator
- Pending sync count
- Sync success/failure feedback

---

## Explicit Non-Goals

- Real-time multi-device inventory locking
- Automatic conflict resolution
- Distributed consensus

---

## Success Criteria

- Zero transaction loss
- No duplicate transactions
- Predictable and explainable sync behavior
