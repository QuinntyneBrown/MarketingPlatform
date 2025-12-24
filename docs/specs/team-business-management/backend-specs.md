# Team & Business Management - Backend Specifications

**Feature**: Team & Business Management
**Phase**: 5 (Full Feature)
**Document Version**: 1.0
**Last Updated**: 2025-12-24

---

## 1. Overview

Team & Business Management handles multi-user access, role-based permissions, and business account management.

---

## 2. Requirements

### 2.1 Team Management

#### REQ-TM-BE-001: Team Member Invitation
**Statement**: The system SHALL support inviting team members.

**Phase**: 5

**Acceptance Criteria**:
- AC1: TeamMemberInvited event on invite
- AC2: TeamMemberAdded on acceptance
- AC3: Email invitation with link
- AC4: Invitation expiration

---

#### REQ-TM-BE-002: Role Assignment
**Statement**: The system SHALL support role-based access.

**Phase**: 5

**Acceptance Criteria**:
- AC1: TeamRoleAssigned/Updated events
- AC2: Predefined roles (Owner, Admin, Member)
- AC3: TeamPermissionsModified for custom
- AC4: Permission enforcement

---

#### REQ-TM-BE-003: Team Member Removal
**Statement**: The system SHALL support removing team members.

**Phase**: 5

**Acceptance Criteria**:
- AC1: TeamMemberRemoved event
- AC2: Access revocation
- AC3: Ownership transfer prevention
- AC4: TeamMemberLimitReached check

---

### 2.2 Business Account

#### REQ-TM-BE-004: Business Management
**Statement**: The system SHALL support business accounts.

**Phase**: 5

**Acceptance Criteria**:
- AC1: BusinessCreated event
- AC2: BusinessSettingsUpdated for changes
- AC3: Multiple businesses per user
- AC4: BusinessSwitched for context

---

---

## 3. Domain Model

```
Aggregate: TeamAggregate
Location: MarketingPlatform.Core/Model/TeamAggregate/

Entities:
- Business (Aggregate Root)
- TeamMember
- TeamInvitation

Enums:
- TeamRole (Owner, Admin, Member, Viewer)
- InvitationStatus (Pending, Accepted, Expired)
```

---

## 4. API Endpoints

| Method | Endpoint | Description | Phase |
|--------|----------|-------------|-------|
| GET | /api/team | List members | 5 |
| POST | /api/team/invite | Invite member | 5 |
| PUT | /api/team/{id}/role | Update role | 5 |
| DELETE | /api/team/{id} | Remove member | 5 |
| GET | /api/businesses | List businesses | 5 |
| POST | /api/businesses | Create business | 5 |
| PUT | /api/businesses/{id} | Update business | 5 |

---

*End of Team & Business Management Backend Specifications*
