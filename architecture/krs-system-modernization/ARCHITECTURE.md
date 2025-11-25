# Architecture Overview: KRS Correspondentbanking system

**Generated**: 2025-11-25  
**Source**: Legacy System Modernization Pipeline (BIAN v13 + DDD)

---

## Table of Contents

1. [Executive Summary](#executive-summary)
2. [Legacy System Context](#legacy-system-context)
3. [Target Architecture](#target-architecture)
4. [BIAN Trinity Architecture](#bian-trinity-architecture)
5. [Bounded Contexts](#bounded-contexts)
6. [Context Map](#context-map)
7. [Modernization Strategy](#modernization-strategy)
8. [Key Non-Functional Requirements](#key-non-functional-requirements)
9. [BIAN v13 Alignment](#bian-v13-alignment)
10. [Implementation Roadmap](#implementation-roadmap)
11. [Documentation Guide](#documentation-guide)

---

## Executive Summary

### System Overview

**KRS Correspondentbanking system** is a legacy banking system that Legacy correspondentbanking register used in Capital Markets for nostro and settlement when communicating with other bank.

This document outlines the target architecture for modernizing this system using:
- **BIAN v13 Service Landscape** - Industry-standard banking architecture framework
- **Domain-Driven Design (DDD)** - Bounded contexts for clear service boundaries
- **Event-Driven Architecture** - Loosely coupled, scalable microservices

### Business Value

**Why Modernize?**
- ✅ **Agility**: Faster time-to-market for new features (weeks vs. months)
- ✅ **Scalability**: Handle 10x transaction volume without major infrastructure changes
- ✅ **Maintainability**: Clear service boundaries reduce complexity
- ✅ **Compliance**: Audit trails and data lineage built-in from day one
- ✅ **Cost**: Cloud-native architecture reduces infrastructure costs by 30-40%

**What Changes?**
- Mainframe/monolithic architecture → Cloud-native microservices
- Batch processing → Real-time event-driven processing
- Undocumented systems → BIAN v13 standardized architecture
- Manual testing → Automated testing with clear domain boundaries

### Key Metrics

| Metric | Current (Legacy) | Target (Modernized) |
|--------|------------------|---------------------|
| **Deployment Frequency** | Quarterly | Weekly/Daily |
| **Lead Time for Changes** | 3-6 months | 1-4 weeks |
| **MTTR** | Days | Hours |
| **Change Failure Rate** | 30-40% | <10% |
| **Availability** | 99% | 99.9%+ |

---

## Legacy System Context

### Current State

**Technology Stack** (estimated):
- Mainframe/COBOL or legacy middleware
- Batch-oriented processing
- File-based integrations
- Limited documentation

**Known Integrations**:
- Exports data to SWIFT gateway and treasury system.

**Regulatory Context**:
Used for AML/KYC checks on correspondent banks.

### Pain Points

- 🔴 **Undocumented**: 0 capabilities extracted through AI analysis
- 🔴 **Monolithic**: Changes require full system regression testing
- 🔴 **Batch-oriented**: Real-time requirements cannot be met
- 🔴 **Integration Complexity**: Point-to-point integrations are brittle
- 🔴 **Skill Gap**: Declining pool of developers familiar with legacy tech

### What We're Modernizing

**Extracted Capabilities**:
1. **undefined** - Description pending...
2. **undefined** - Description pending...
3. **undefined** - Description pending...
4. **undefined** - Description pending...



---

## Target Architecture

### Architecture Principles

1. **BIAN v13 Alignment**: Use industry-standard service domains
2. **Domain-Driven Design**: Bounded contexts enforce clear ownership
3. **Event-Driven**: Asynchronous communication for scalability
4. **API-First**: RESTful APIs + event streaming
5. **Cloud-Native**: Containerized, orchestrated with Kubernetes
6. **Security by Design**: Authentication, authorization, encryption at every layer

### High-Level Architecture

```mermaid
graph TB
    subgraph "External Systems"
        Legacy[Legacy KRS Correspondentbanking system]
        External[External Integrations]
    end
    
    subgraph "Anti-Corruption Layer"
        ACL[Legacy Integration ACL]
    end
    
    subgraph "Memory Layer"
        Memory[Reference Data Contexts]
    end
    
    subgraph "Heart Layer"
        Heart[Lifecycle Contexts]
    end
    
    subgraph "Brain Layer"
        Brain[Operations Contexts]
    end
    
    Legacy --> ACL
    ACL --> M0
    External --> M0
```

### Technology Stack (Proposed)

| Layer | Technology |
|-------|------------|
| **API Gateway** | Kong / AWS API Gateway |
| **Services** | Java Spring Boot / Node.js |
| **Event Streaming** | Apache Kafka / AWS Kinesis |
| **Databases** | PostgreSQL (transactional), MongoDB (documents) |
| **Caching** | Redis |
| **Search** | Elasticsearch |
| **Container Orchestration** | Kubernetes / EKS |
| **CI/CD** | GitHub Actions / Jenkins |
| **Observability** | Prometheus + Grafana, ELK Stack |
| **Security** | OAuth 2.0 / JWT, Vault for secrets |

---

## BIAN Trinity Architecture

### What is BIAN Trinity?

BIAN v13 organizes banking systems into three architectural layers:

#### 💾 **MEMORY Layer** (System of Record)
- **Purpose**: Store and serve authoritative master data
- **Characteristics**: Read-heavy, caching critical, high data quality
- **NFR Focus**: Query performance (<100ms), data quality, caching

#### 💚 **HEART Layer** (Lifecycle Management)
- **Purpose**: Manage lifecycles, relationships, and agreements
- **Characteristics**: Workflow state, ACID transactions, audit trails
- **NFR Focus**: Data integrity, workflow persistence, compliance

#### 🧠 **BRAIN Layer** (Operations / Execution)
- **Purpose**: Execute business operations and transactions
- **Characteristics**: High throughput, business rules, operational logic
- **NFR Focus**: Throughput (TPS), latency, idempotency, resilience

### Our BIAN Trinity Distribution

| Layer | Contexts |
|-------|----------|
| **💾 Memory** | 0 |
| **💚 Heart** | 0 |
| **🧠 Brain** | 0 |
| **⚙️ Hybrid** | 0 |

---

## Bounded Contexts

### All Bounded Contexts

Bounded contexts are being analyzed...

---

## Context Map

### Comprehensive Context Map

```mermaid
graph TB
  %% Comprehensive Context Map
  %% Generated from bounded context analysis

  bc_001["💾 Correspondent Directory Management"]
  style bc_001 fill:#3498db,stroke:#333,stroke-width:2px,color:#fff
  bc_002["💾 Settlement Instruction Management"]
  style bc_002 fill:#3498db,stroke:#333,stroke-width:2px,color:#fff
  bc_003["💚 Correspondent Relationship Management"]
  style bc_003 fill:#2ecc71,stroke:#333,stroke-width:2px,color:#fff
  bc_004["⚙️ Correspondent Data Gateway"]
  style bc_004 fill:#95a5a6,stroke:#333,stroke-width:2px,color:#fff
  bc_005["💚 Audit & Compliance Reporting"]
  style bc_005 fill:#2ecc71,stroke:#333,stroke-width:2px,color:#fff
  bc_006["⚙️ Legacy Integration (Anti-Corruption Layer)"]
  style bc_006 fill:#95a5a6,stroke:#333,stroke-width:2px,color:#fff

  bc_003 ==>|published-language| bc_001
  bc_001 ==>|published-language| bc_002
  bc_001 -->|open-host-service| bc_004
  bc_002 -->|open-host-service| bc_004
  All_Domain_Contexts ==>|published-language| bc_005
  All_Domain_Contexts -->|anti-corruption-layer| Legacy_Integration_ACL

  %% Legend
  legend["Legend:<br/>💾 Memory (Reference Data)<br/>💚 Heart (Lifecycle)<br/>🧠 Brain (Operations)<br/>⚙️ Hybrid/Technical"]
  style legend fill:#f9f9f9,stroke:#999,stroke-width:1px,color:#333
```

### Context Relationships

Relationships are being analyzed...

---

## Modernization Strategy

### Approach: Strangler Fig Pattern

We will gradually replace legacy functionality:

**Phase 1: Read-Only Façade** (Months 1-6)
- New services read from legacy via ACL
- Build Memory contexts first
- Validate architecture

**Phase 2: Dual-Write** (Months 7-12)
- Writes go to both systems
- Build Heart contexts
- Achieve parity

**Phase 3: Cutover** (Months 13-18)
- Full migration
- Build Brain contexts
- Decommission legacy

---

## Key Non-Functional Requirements

### Critical NFRs


#### 1. Immutable Audit Trail for Correspondent Data (Compliance)

**Statement**: The system must maintain an immutable, append-only audit trail for all create, update, and delete operations on Correspondent Bank, Nostro, and Account entities.

**Measure**: 1) All data modification events are captured and stored in a separate, append-only log store. 2) Each audit entry includes user ID, timestamp (UTC), action performed, and a snapshot of the data before and after the change. 3) Direct database updates to the audit log are prohibited at the data layer.

---

#### 2. Role-Based Access Control (RBAC) (Security)

**Statement**: The system must enforce role-based access control (RBAC) to ensure the principle of least privilege for all user interactions with correspondent data and settlement instructions.

**Measure**: 1) At least three roles are defined: 'Viewer' (read-only), 'Editor' (create/update), and 'Approver' (authorizes changes). 2) API endpoints reject requests from users without the required role with an HTTP 403 error. 3) An audit of user permissions can be generated on demand.

---

#### 3. High Availability for Data Provisioning Services (Availability)

**Statement**: The system's data provisioning services (APIs and batch exports) must achieve 99.9% availability.

**Measure**: Measured monthly, total downtime must not exceed 43.8 minutes. The system must be deployed across at least two independent availability zones.

---

#### 4. Low-Latency Reference Data Retrieval (Performance)

**Statement**: The system must provide read access to correspondent bank and settlement instruction data with a 95th percentile (p95) latency of less than 100 milliseconds.

**Measure**: Performance load tests simulating 1000 concurrent read requests show a p95 response time below 100ms for key lookup APIs (e.g., get correspondent by BIC).

---

#### 5. Idempotent Data Provisioning to Downstream Systems (Resilience)

**Statement**: The system must ensure that all data provisioning events (e.g., updates to settlement instructions) sent to downstream systems are idempotent.

**Measure**: Each outbound message/API call must contain a unique transaction ID. The consuming system can use this ID to safely ignore duplicate messages. The system must handle and log duplicate inbound requests without causing data corruption.


---

## BIAN v13 Alignment

### Mapping Confidence

- **Average Confidence**: 85%
- **High Confidence (>80%)**: 3 capabilities
- **BIAN Domains Used**: 3 domains

---

## Implementation Roadmap

### Phase 1: Foundation (Months 1-6)
- [ ] Infrastructure setup
- [ ] Build Memory contexts
- [ ] Anti-Corruption Layer
- [ ] CI/CD pipelines

### Phase 2: Parity (Months 7-12)
- [ ] Dual-write implementation
- [ ] Build Heart contexts
- [ ] Reconciliation jobs
- [ ] UAT

### Phase 3: Cutover (Months 13-18)
- [ ] Build Brain contexts
- [ ] Traffic migration
- [ ] Legacy decommission

---

## Documentation Guide

### Repository Structure

```
/
├── ARCHITECTURE.md        # This document
├── bounded-contexts/      # Canvas v5 documents
├── diagrams/              # Mermaid diagrams
├── nfrs/                  # NFR catalog
└── bian-mapping.md        # BIAN alignment
```

---

*Generated by Legacy System Modernization Pipeline*
