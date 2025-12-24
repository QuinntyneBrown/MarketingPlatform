# Team & Business Management - Frontend Specifications

**Feature**: Team & Business Management
**Phase**: 5 (Full Feature)
**Document Version**: 1.0
**Last Updated**: 2025-12-24

---

## 1. Overview

This document specifies the frontend requirements for Team & Business Management.

---

## 2. Requirements

### 2.1 Team Settings

#### REQ-TM-FE-001: Team Member List
**Statement**: The system SHALL display team members.

**Phase**: 5

**Acceptance Criteria**:
- AC1: Member table with role
- AC2: Invite button
- AC3: Role dropdown for admin
- AC4: Remove member action

---

#### REQ-TM-FE-002: Invitation Dialog
**Statement**: The system SHALL provide invitation interface.

**Phase**: 5

**Acceptance Criteria**:
- AC1: Email input
- AC2: Role selection
- AC3: Personal message (optional)
- AC4: Send invitation button

---

### 2.2 Business Switcher

#### REQ-TM-FE-003: Business Selector
**Statement**: The system SHALL support switching businesses.

**Phase**: 5

**Acceptance Criteria**:
- AC1: Dropdown in header
- AC2: Business list display
- AC3: Create new business option
- AC4: Context switch on selection

---

---

## 3. Component Structure

### 3.1 Pages

| Component | Route | Description | Phase |
|-----------|-------|-------------|-------|
| TeamSettings | /settings/team | Team management | 5 |
| BusinessSettings | /settings/business | Business config | 5 |

### 3.2 Components

| Component | Description | Phase |
|-----------|-------------|-------|
| TeamMemberTable | Member list | 5 |
| InviteDialog | Invitation form | 5 |
| RoleSelector | Role dropdown | 5 |
| BusinessSwitcher | Business selector | 5 |

---

*End of Team & Business Management Frontend Specifications*
