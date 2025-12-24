# Participant Management - Backend Specifications

**Feature**: Participant Management
**Phase**: 1 (MVP)
**Document Version**: 1.0
**Last Updated**: 2025-12-24

---

## 1. Overview

Participant Management handles the registration, tracking, and management of users who participate in campaigns. This is a Phase 1 (MVP) feature essential for tracking engagement across all campaign types.

---

## 2. Requirements

### 2.1 Participant Lifecycle

#### REQ-PM-BE-001: Participant Registration
**Statement**: The system SHALL register participants when they first engage with a campaign.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Participant created on first form submission
- AC2: ParticipantRegistered event published
- AC3: Email used as unique identifier
- AC4: Profile linked to business account

---

#### REQ-PM-BE-002: Participant Profile
**Statement**: The system SHALL maintain participant profiles with collected data.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Profile stores all submitted data
- AC2: ParticipantProfileCreated event published
- AC3: Data merged from multiple campaigns
- AC4: Profile queryable by email

---

#### REQ-PM-BE-003: Participant Data Update
**Statement**: The system SHALL allow updating participant data.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Participants can update their info
- AC2: ParticipantDataUpdated event published
- AC3: Version history maintained
- AC4: Admin can update on behalf

---

#### REQ-PM-BE-004: Participant Verification
**Statement**: The system SHALL support email verification of participants.

**Phase**: 2

**Acceptance Criteria**:
- AC1: Verification email sent on registration
- AC2: ParticipantVerified event on confirmation
- AC3: Verified status stored
- AC4: Campaigns can require verification

---

#### REQ-PM-BE-005: Participant Unsubscribe
**Statement**: The system SHALL allow participants to unsubscribe.

**Phase**: 2

**Acceptance Criteria**:
- AC1: Unsubscribe link in all emails
- AC2: ParticipantUnsubscribed event published
- AC3: Email preferences updated
- AC4: Compliant with CAN-SPAM

---

#### REQ-PM-BE-006: Participant Removal
**Statement**: The system SHALL support participant data removal (GDPR).

**Phase**: 2

**Acceptance Criteria**:
- AC1: Participants can request data deletion
- AC2: ParticipantRemoved event published
- AC3: PII removed, analytics anonymized
- AC4: Deletion logged for compliance

---

### 2.2 Participant Engagement

#### REQ-PM-BE-007: Activity Tracking
**Statement**: The system SHALL track participant activities.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Campaign entries tracked
- AC2: ParticipantActivityRecorded event per action
- AC3: Engagement score calculated
- AC4: Activity history queryable

---

#### REQ-PM-BE-008: Return Visit Tracking
**Statement**: The system SHALL identify returning participants.

**Phase**: 2

**Acceptance Criteria**:
- AC1: Cookie-based identification
- AC2: ParticipantReturnVisit event published
- AC3: Visit count maintained
- AC4: Last visit date tracked

---

#### REQ-PM-BE-009: Referral Tracking
**Statement**: The system SHALL track participant referrals.

**Phase**: 2

**Acceptance Criteria**:
- AC1: Unique referral links generated
- AC2: ParticipantReferralMade event on referral use
- AC3: ReferralCredited event for referrer
- AC4: Referral chain tracked

---

### 2.3 Participant Data Collection

#### REQ-PM-BE-010: Email Collection
**Statement**: The system SHALL collect and store participant emails.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Email validated on collection
- AC2: EmailCollected event published
- AC3: Duplicate prevention
- AC4: Consent recorded

---

#### REQ-PM-BE-011: Consent Management
**Statement**: The system SHALL track participant consent.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Consent recorded at collection
- AC2: ConsentRecorded event published
- AC3: OptInConfirmed for marketing consent
- AC4: Consent version tracked

---

---

## 3. Domain Model

### 3.1 Participant Aggregate

```
Aggregate: ParticipantAggregate
Location: MarketingPlatform.Core/Model/ParticipantAggregate/

Entities:
- Participant (Aggregate Root)
- ParticipantActivity
- ParticipantConsent

Value Objects:
- ParticipantId
- EmailAddress
- EngagementScore

Enums:
- ParticipantStatus (Active, Unsubscribed, Removed)
- ConsentType (Marketing, DataProcessing, ThirdParty)
- ActivityType (FormSubmission, ContestEntry, Vote, Share)
```

---

## 4. API Endpoints

| Method | Endpoint | Description | Phase |
|--------|----------|-------------|-------|
| GET | /api/participants | List participants | 1 |
| GET | /api/participants/{id} | Get participant | 1 |
| PUT | /api/participants/{id} | Update participant | 1 |
| DELETE | /api/participants/{id} | Remove participant (GDPR) | 2 |
| GET | /api/participants/{id}/activities | Get activities | 1 |
| POST | /api/participants/{id}/verify | Verify email | 2 |
| POST | /api/participants/{id}/unsubscribe | Unsubscribe | 2 |
| GET | /api/participants/{id}/referrals | Get referrals | 2 |
| GET | /api/participants/export | Export participants | 2 |

---

## 5. Domain Events

| Event | Trigger | Phase |
|-------|---------|-------|
| ParticipantRegistered | First engagement | 1 |
| ParticipantProfileCreated | Profile created | 1 |
| ParticipantDataUpdated | Data update | 1 |
| ParticipantVerified | Email verified | 2 |
| ParticipantUnsubscribed | Unsubscribe | 2 |
| ParticipantRemoved | GDPR deletion | 2 |
| ParticipantActivityRecorded | Any activity | 1 |
| ParticipantReturnVisit | Return visit | 2 |
| ParticipantReferralMade | Referral used | 2 |
| ReferralCredited | Referrer credit | 2 |
| EmailCollected | Email captured | 1 |
| ConsentRecorded | Consent given | 1 |
| OptInConfirmed | Marketing opt-in | 1 |

---

*End of Participant Management Backend Specifications*
