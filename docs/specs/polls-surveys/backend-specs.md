# Polls & Surveys - Backend Specifications

**Feature**: Polls & Surveys
**Phase**: 3 (Enhanced Features)
**Document Version**: 1.0
**Last Updated**: 2025-12-24

---

## 1. Overview

Polls & Surveys enables users to create interactive voting experiences to gather opinions and feedback from participants.

---

## 2. Requirements

### 2.1 Poll Lifecycle

#### REQ-PS-BE-001: Poll Creation
**Statement**: The system SHALL allow creating polls with questions and options.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Poll created with question text
- AC2: Multiple options added (min 2, max 10)
- AC3: PollCreated event published
- AC4: Linked to parent campaign

---

#### REQ-PS-BE-002: Poll Publishing
**Statement**: The system SHALL support publishing polls for voting.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Draft polls can be published
- AC2: PollPublished event published
- AC3: Poll accepts responses after publishing
- AC4: URL generated for access

---

#### REQ-PS-BE-003: Poll Closing
**Statement**: The system SHALL support closing polls to voting.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Polls can be manually closed
- AC2: Auto-close at end date
- AC3: PollClosed event published
- AC4: No new responses accepted

---

### 2.2 Poll Configuration

#### REQ-PS-BE-004: Poll Options Management
**Statement**: The system SHALL allow managing poll options.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Add options (PollOptionAdded event)
- AC2: Remove options (PollOptionRemoved event)
- AC3: Update option text (PollOptionUpdated event)
- AC4: Option order configurable

---

#### REQ-PS-BE-005: Voting Mode Configuration
**Statement**: The system SHALL support different voting modes.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Single choice mode (radio buttons)
- AC2: Multiple choice mode (checkboxes)
- AC3: SingleChoiceEnabled/MultipleChoiceEnabled events
- AC4: Max selections configurable for multiple

---

#### REQ-PS-BE-006: Results Display Configuration
**Statement**: The system SHALL allow configuring results visibility.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Show results after vote
- AC2: Hide results until poll closes
- AC3: PollResultsRevealed/PollResultsHidden events
- AC4: Real-time result updates

---

### 2.3 Poll Responses

#### REQ-PS-BE-007: Response Submission
**Statement**: The system SHALL accept and validate poll responses.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Response validated against poll config
- AC2: PollResponseSubmitted event published
- AC3: Duplicate prevention (optional)
- AC4: PollResponseRecorded for storage

---

#### REQ-PS-BE-008: Vote Change
**Statement**: The system SHALL optionally allow vote changes.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Vote change configurable per poll
- AC2: PollVoteChanged event published
- AC3: Original vote archived
- AC4: Change limit configurable

---

---

## 3. Domain Model

```
Aggregate: PollAggregate
Location: MarketingPlatform.Core/Model/PollAggregate/

Entities:
- Poll (Aggregate Root)
- PollOption
- PollResponse

Enums:
- PollStatus (Draft, Published, Closed)
- VotingMode (SingleChoice, MultipleChoice)
```

---

## 4. API Endpoints

| Method | Endpoint | Description | Phase |
|--------|----------|-------------|-------|
| POST | /api/polls | Create poll | 3 |
| GET | /api/polls/{id} | Get poll | 3 |
| PUT | /api/polls/{id} | Update poll | 3 |
| POST | /api/polls/{id}/publish | Publish poll | 3 |
| POST | /api/polls/{id}/close | Close poll | 3 |
| POST | /api/polls/{id}/options | Add option | 3 |
| POST | /api/polls/{id}/responses | Submit vote | 3 |
| GET | /api/polls/{id}/results | Get results | 3 |

---

## 5. Domain Events

| Event | Trigger | Phase |
|-------|---------|-------|
| PollCreated | Poll creation | 3 |
| PollPublished | Publishing | 3 |
| PollClosed | Closing | 3 |
| PollOptionAdded | Option add | 3 |
| PollOptionRemoved | Option remove | 3 |
| PollOptionUpdated | Option update | 3 |
| PollResponseSubmitted | Vote submit | 3 |
| PollResponseRecorded | Vote stored | 3 |
| PollVoteChanged | Vote change | 3 |
| PollResultsRevealed | Show results | 3 |
| PollResultsHidden | Hide results | 3 |

---

*End of Polls & Surveys Backend Specifications*
