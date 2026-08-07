# ResolveHub Domain Model

## Overview

ResolveHub is an internal support operations platform designed to help software support teams capture, organize, assign, document, and resolve customer requests received through multiple communication channels.

Unlike traditional ticketing systems, customers do not access the platform directly. Instead, support engineers register customer requests and manage the entire technical lifecycle internally.

The platform centralizes all technical work, allowing support teams, developers, and administrators to collaborate efficiently while maintaining a complete history of every request.

---

# Vision

The goal of ResolveHub is not only to manage tickets.

Its purpose is to become the central workspace where technical teams organize, document, and track customer support activities.

Every customer request becomes a Work Item.

Every important action becomes part of the Work Item history.

Every decision remains documented.

---

# Users

ResolveHub is an internal platform.

The authenticated users are:

- Support
- Developer
- Administrator

Customers are business entities but they never log into the platform.

---

# Request Capture

Customer requests may arrive through different communication channels.

Examples:

- WhatsApp
- Phone Call
- Microsoft Teams
- Email
- On-site Visit

Regardless of how the request is received, every request becomes a Work Item inside ResolveHub.

---

# Core Entity

## Work Item

A Work Item represents a customer request captured by the support team.

It is the central entity of the entire platform.

Everything revolves around the Work Item.

Examples:

- Software Incident
- Bug Report
- Service Request
- Configuration Issue
- Database Issue
- Infrastructure Support

---

# Domain Entities

## Work Item

### Properties

- Id
- Number
- Title
- Description
- Priority
- Status
- Source
- CreatedAt
- CreatedBy
- AssignedTo
- ClosedAt

### Relationships

- Customer
- Contact
- System
- Module
- Timeline
- Attachments

---

## Customer

Represents a company receiving technical support.

Examples

- ABC Company
- Super Market S.A.
- Coffee Export Group

### Relationships

- Contacts
- Work Items

---

## Contact

Represents the person who reported the request.

Examples

- Carlos Lopez
- Maria Hernandez

### Relationships

- Customer
- Work Items

---

## System

Represents a business software system.

Examples

- Electronic Invoicing
- Inventory
- Payroll
- Accounting

### Relationships

- Modules
- Work Items

---

## Module

Represents a functional area inside a system.

Examples

Electronic Invoicing

- Sales
- Purchases
- Monthly Closing
- Reports

Inventory

- Products
- Stock
- Warehouse

### Relationships

- System
- Work Items

---

## Timeline

The Timeline stores the complete history of a Work Item.

Instead of separating comments, assignments and status changes into different sections, ResolveHub centralizes every important event inside the Timeline.

Examples

- Work Item created
- Assigned to another engineer
- Status changed
- Priority updated
- Internal note added
- Customer contacted
- Attachment uploaded
- Request resolved
- Work Item closed

The Timeline becomes the complete story of a Work Item.

---

## Attachment

Represents files associated with a Work Item.

Examples

- Images
- PDF
- SQL Scripts
- Excel Files
- Log Files
- Configuration Files

---

# Work Item Lifecycle

Customer Request

↓

Captured by Support

↓

Assigned

↓

In Progress

↓

Resolved

↓

Customer Confirmation (External)

↓

Closed

---

# Business Rules

## Customer

- Every Customer may have multiple Contacts.
- Every Contact belongs to exactly one Customer.

---

## System

- Every System may contain multiple Modules.
- Every Module belongs to exactly one System.

---

## Work Item

- Every Work Item must belong to one Customer.
- Every Work Item must belong to one Contact.
- Every Work Item must belong to one System.
- Every Work Item must belong to one Module.
- Every Work Item has exactly one active assignee.
- Every Work Item has one current Status.
- Every Work Item has one current Priority.
- Closed Work Items cannot be modified.
- Every important action must be recorded in the Timeline.

---

# Initial Status Flow

Captured

↓

Assigned

↓

In Progress

↓

Resolved

↓

Closed

Future versions may introduce additional states such as:

- Waiting for Customer
- Pending Deployment
- Cancelled
- Reopened

---

# Future Integrations

ResolveHub is designed with extensibility in mind.

Future versions may support automatic request capture through external communication platforms.

Potential integrations include:

- WhatsApp Business API
- Microsoft Teams
- Outlook
- Gmail

These integrations are intentionally outside the scope of version 1.

---

# Design Principles

ResolveHub follows these principles:

- Customer requests are always captured by internal staff.
- Every request becomes a Work Item.
- Every important action becomes part of the Timeline.
- Business rules belong to the Domain.
- Technology should not dictate business decisions.
- Documentation evolves together with the software.

---

# Version

Document Version

v0.1

Status

Draft