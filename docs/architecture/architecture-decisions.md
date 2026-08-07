# Architecture Decision Records (ADR)

This document records the most important architectural decisions made during the development of ResolveHub.

The purpose of these records is to explain why a decision was made, allowing future contributors to understand the reasoning behind the architecture.

---

# ADR-001

## Title

ResolveHub is an Internal Support Operations Platform

### Status

Accepted

### Context

Many support platforms require customers to create and manage tickets directly.

However, in many software companies, customer communication occurs through external channels such as WhatsApp, Microsoft Teams, phone calls, or email.

Customers rarely interact with an internal support platform.

### Decision

ResolveHub will be designed as an internal platform.

Only company employees will authenticate into the application.

Customer requests will be captured by support engineers and transformed into Work Items.

### Consequences

- Simpler authentication model.
- Faster request capture.
- Better adaptation to real-world support workflows.
- Easier future integration with communication platforms.

---

# ADR-002

## Title

Work Item is the Core Domain Entity

### Status

Accepted

### Context

Different companies use different terminology.

Examples include:

- Ticket
- Incident
- Service Request
- Support Case

Using one specific term could limit the platform.

### Decision

ResolveHub will use Work Item as the central business entity.

Every customer request will become a Work Item regardless of its origin.

### Consequences

- Flexible domain model.
- Easier future expansion.
- Generic workflow capable of handling multiple request types.

---

# ADR-003

## Title

Timeline replaces multiple history tables

### Status

Accepted

### Context

Traditional ticketing systems separate:

- Comments
- Assignment History
- Status History
- Activity Log

This often forces users to navigate multiple screens.

### Decision

ResolveHub will maintain a single Timeline for every Work Item.

Every important event will be recorded chronologically.

Examples include:

- Work Item created
- Assignment changed
- Status updated
- Internal note added
- Attachment uploaded
- Resolution completed

### Consequences

- Simpler user experience.
- Complete chronological history.
- Easier auditing.
- Better understanding of technical work.

---

# ADR-004

## Title

Modular Monolith Architecture

### Status

Accepted

### Context

ResolveHub is intended for a single company during its initial versions.

Microservices would introduce unnecessary operational complexity.

### Decision

The platform will be built as a Modular Monolith.

Business capabilities will be separated into modules while remaining inside a single deployable application.

### Consequences

- Easier development.
- Simpler deployment.
- Lower infrastructure costs.
- Clear separation between business modules.
- Future migration to microservices remains possible.

---

# ADR-005

## Title

Business before Technology

### Status

Accepted

### Context

Many software projects start by designing the database or choosing frameworks.

This frequently results in technical decisions driving the business model.

### Decision

ResolveHub follows a Domain-Driven Design mindset.

The development order will always be:

1. Understand the business problem.
2. Model the domain.
3. Design the application.
4. Design the infrastructure.
5. Implement the solution.

### Consequences

- Stronger business model.
- Better maintainability.
- Clear separation of responsibilities.
- Technology becomes an implementation detail.

---

# ADR-006

## Title

Documentation is part of the product

### Status

Accepted

### Context

Documentation is often created at the end of a project and quickly becomes outdated.

### Decision

Documentation will evolve together with the source code.

Every important architectural decision must be documented.

### Consequences

- Easier onboarding.
- Better collaboration.
- Clear project evolution.
- Professional open-source repository.

---

# ADR-007

## Title

External integrations are outside Version 1

### Status

Accepted

### Context

Platforms such as WhatsApp Business, Microsoft Teams, and Outlook require external integrations and additional operational complexity.

### Decision

Version 1 will support manual request capture only.

The architecture will remain open for future integrations.

### Consequences

- Faster delivery.
- Lower implementation complexity.
- Stable business model before external integrations.