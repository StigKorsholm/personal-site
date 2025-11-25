# Bounded Context Canvas: Correspondent Directory Management

> **Generated from Legacy System Modernization Pipeline**  
> **BIAN Trinity Classification**: MEMORY  
> **Strategic Classification**: SUPPORTING

---

## 1. Name & Description

**Name**: Correspondent Directory Management

**Description**: Manages the master data for correspondent banks, including their legal identifiers (BIC, LEI), addresses, and contact details. It serves as the single, authoritative source of truth for correspondent static data.

**Trinity Role**: System of Record for correspondent bank master data. Provides read-heavy reference data to downstream systems.

---

## 2. Strategic Classification

**Type**: supporting


⚙️ **Supporting Domain** - Necessary but not differentiating


---

## 3. Business Model

**Revenue Impact**: indirect

**Cost Center**: technology-platform

---

## 4. Evolution Stage

**Stage**: product



📦 Product - Standardized, configurable, proven solutions


---

## 5. Domain Roles

**Who interacts with this bounded context:**

- **Data Steward**: Creates, updates, and validates correspondent bank records.
- **Compliance Officer**: Reviews and approves changes to sensitive bank identifiers.

---

## 6. Inbound Communication

**What comes INTO this context:**

- **Correspondent Relationship Management**
  - Message: `RelationshipApproved event`
  - Protocol: async-event-kafka
  - Reason: Triggers the activation of a correspondent bank record in the directory.

- **User Interface / API Client**
  - Message: `CreateCorrespondentBank command`
  - Protocol: sync-rest-api
  - Reason: Direct user action to onboard a new correspondent's static data.

---

## 7. Outbound Communication

**What goes OUT of this context:**

- **Audit & Compliance Reporting**
  - Message: `CorrespondentBankUpdated event`
  - Protocol: async-event-kafka
  - Reason: To record an immutable audit trail of all data changes.

- **Correspondent Data Gateway**
  - Message: `GetCorrespondentByBIC query`
  - Protocol: sync-rest-api
  - Reason: To provide master data for consumption by downstream systems.

---

## 8. Ubiquitous Language

**Domain-specific terminology:**

**correspondent_bank**: A financial institution that provides services on behalf of another financial institution.

**bic**: Bank Identifier Code (ISO 9362), the universal method for identifying financial institutions.

**lei**: Legal Entity Identifier (ISO 17442), a unique global identifier for legal entities participating in financial transactions.

**directory_entry**: A record representing a single correspondent bank's master data.

**validation_status**: The state of a directory entry after being checked against external registries (e.g., Valid, Invalid, Pending).

---

## 9. Responsibilities

**What this context does:**

- Maintain the master data registry for all correspondent banks.
- Enforce data quality rules, including mandatory fields and format validation for BIC and LEI.
- Manage the lifecycle of a directory entry (e.g., Active, Inactive).
- Provide an API for creating, reading, and updating correspondent bank data.
- Publish domain events when correspondent data changes (e.g., CorrespondentBankUpdated).
- Ensure data is versioned to support point-in-time queries.

---

## 10. Aggregates & Entities

**Core domain objects owned by this context:**

### CorrespondentBank

**Entities**: Identifier, Address, ContactPerson

**Value Objects**: BIC, LEI, CountryCode, Status



---

## BIAN v13 Alignment

### Owned BIAN Service Domains


### Correspondent Bank Directory

- **Business Area**: Reference Data
- **Business Domain**: External Agency
- **BIAN URL**: https://bian.org/servicelandscape-13-0-0/object_23.html?object=49491


### BIAN Layer

**Layer**: Reference Data

### Trinity Classification

**Classification**: memory

💾 **MEMORY** - System of Record, Reference Data




---

## Related Capabilities

- CAP-001

---

## Key Non-Functional Requirements

- NFR-007
- NFR-019
- NFR-015
- NFR-002
- NFR-010

---

## Context Relationships

### Upstream Dependencies (This context depends on)

- **Correspondent Relationship Management** (upstream-downstream) - Relationship Management (Upstream) publishes the business approval event, which Directory Management (Downstream) consumes to activate a record.

### Downstream Consumers (This context provides to)

- **Settlement Instruction Management** (upstream-downstream) - The Directory (Upstream) must confirm a bank is active before Settlement Instructions (Downstream) can be created for it.
- **Correspondent Data Gateway** (customer-supplier) - The Directory (Supplier) provides data via a well-defined API to the Gateway (Customer), which serves external clients.

---

## Legacy System Integration

### Modernization Strategy

**Strategy**: strangler-fig

🌿 **Strangler Fig** - Gradually replace legacy functions over time




### Legacy Artifacts Covered

- file=CORR_MASTER (partial)

### Integration Points

No integration points defined yet.

---

## Notes

This is a classic 'Memory' context. The design should prioritize data integrity, quality, and versioning. Consider using bitemporal data modeling.

---

## Context Metadata

- **Context ID**: bc-001
- **Generated**: 2025-11-25T22:45:34.772Z
- **Source**: Legacy System Modernization Pipeline (BIAN v13 + DDD)

---

## Quick Reference Card

| Aspect | Value |
|--------|-------|
| **Name** | Correspondent Directory Management |
| **Type** | supporting |
| **Trinity** | memory |
| **BIAN Layer** | Reference Data |
| **Evolution** | product |
| **Aggregates** | 1 |
| **Capabilities** | 1 |
| **NFRs** | 5 |
| **Upstream Deps** | 1 |
| **Downstream Consumers** | 2 |

---

*This Canvas v5 document was auto-generated from the legacy system modernization pipeline. Review and refine as needed with your team.*
