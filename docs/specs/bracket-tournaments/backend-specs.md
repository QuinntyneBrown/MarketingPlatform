# Bracket Tournaments - Backend Specifications

**Feature**: Bracket Tournaments
**Phase**: 5 (Full Feature)
**Document Version**: 1.0
**Last Updated**: 2025-12-24

---

## 1. Overview

Bracket Tournaments enables creating elimination-style voting brackets for products, ideas, or content.

---

## 2. Requirements

### 2.1 Bracket Configuration

#### REQ-BT-BE-001: Bracket Creation
**Statement**: The system SHALL support bracket creation.

**Phase**: 5

**Acceptance Criteria**:
- AC1: BracketCreated event
- AC2: BracketTypeSelected (single/double elimination)
- AC3: Configurable bracket size (8, 16, 32, 64)
- AC4: ParticipantsAdded for entries

---

#### REQ-BT-BE-002: Bracket Seeding
**Statement**: The system SHALL support bracket seeding.

**Phase**: 5

**Acceptance Criteria**:
- AC1: BracketSeeded event
- AC2: Random seeding option
- AC3: Manual seeding option
- AC4: MatchupsGenerated automatically

---

### 2.2 Bracket Progression

#### REQ-BT-BE-003: Round Management
**Statement**: The system SHALL manage bracket rounds.

**Phase**: 5

**Acceptance Criteria**:
- AC1: RoundStarted/RoundCompleted events
- AC2: MatchStarted per match
- AC3: VotingOpenedForMatch for voting
- AC4: VotingClosedForMatch to end
- AC5: MatchWinnerDetermined on result

---

#### REQ-BT-BE-004: Participant Advancement
**Statement**: The system SHALL advance winners.

**Phase**: 5

**Acceptance Criteria**:
- AC1: ParticipantAdvanced to next round
- AC2: ParticipantEliminated on loss
- AC3: BracketWinnerDeclared at end
- AC4: BracketUpsetOccurred tracking

---

### 2.3 Bracket Voting

#### REQ-BT-BE-005: Vote Submission
**Statement**: The system SHALL accept bracket votes.

**Phase**: 5

**Acceptance Criteria**:
- AC1: BracketVoteSubmitted event
- AC2: One vote per match per user
- AC3: BracketPredictionMade for predictions
- AC4: LeaderboardUpdated for prediction games

---

---

## 3. Domain Model

```
Aggregate: BracketAggregate
Location: MarketingPlatform.Core/Model/BracketAggregate/

Entities:
- Bracket (Aggregate Root)
- Round
- Match
- BracketParticipant

Enums:
- BracketType (SingleElimination, DoubleElimination)
- MatchStatus (Upcoming, Voting, Completed)
- BracketSize (Size8, Size16, Size32, Size64)
```

---

## 4. API Endpoints

| Method | Endpoint | Description | Phase |
|--------|----------|-------------|-------|
| POST | /api/brackets | Create bracket | 5 |
| GET | /api/brackets/{id} | Get bracket | 5 |
| POST | /api/brackets/{id}/participants | Add participants | 5 |
| POST | /api/brackets/{id}/seed | Seed bracket | 5 |
| POST | /api/brackets/{id}/publish | Publish | 5 |
| GET | /api/brackets/{id}/rounds | Get rounds | 5 |
| POST | /api/matches/{id}/vote | Submit vote | 5 |
| POST | /api/matches/{id}/close | Close voting | 5 |

---

*End of Bracket Tournaments Backend Specifications*
