# Instant Win - Backend Specifications

**Feature**: Instant Win
**Phase**: 4 (Advanced Features)
**Document Version**: 1.0
**Last Updated**: 2025-12-24

---

## 1. Overview

Instant Win enables users to create games where participants find out immediately if they've won a prize, with configurable odds and prize pools.

---

## 2. Requirements

### 2.1 Instant Win Configuration

#### REQ-IW-BE-001: Instant Win Creation
**Statement**: The system SHALL allow creating instant win games.

**Phase**: 4

**Acceptance Criteria**:
- AC1: Game created with name and duration
- AC2: InstantWinCreated event published
- AC3: Linked to parent campaign
- AC4: Play mechanics configurable

---

#### REQ-IW-BE-002: Prize Pool Configuration
**Statement**: The system SHALL support configuring prize pools.

**Phase**: 4

**Acceptance Criteria**:
- AC1: Multiple prizes with quantities
- AC2: InstantWinPrizePoolConfigured event
- AC3: TotalPrizesAllocated event
- AC4: Prize tiers supported

---

#### REQ-IW-BE-003: Winning Odds Configuration
**Statement**: The system SHALL support configuring winning odds.

**Phase**: 4

**Acceptance Criteria**:
- AC1: Overall odds configurable
- AC2: WinningOddsSet event published
- AC3: Per-prize odds (optional)
- AC4: Odds validation (not > 100%)

---

#### REQ-IW-BE-004: Win Distribution Scheduling
**Statement**: The system SHALL distribute wins over time.

**Phase**: 4

**Acceptance Criteria**:
- AC1: Spread wins across campaign duration
- AC2: PrizeDistributionScheduled event
- AC3: Daily win limits configurable
- AC4: DailyWinLimitSet event

---

### 2.2 Instant Win Play

#### REQ-IW-BE-005: Play Attempt Processing
**Statement**: The system SHALL process instant win play attempts.

**Phase**: 4

**Acceptance Criteria**:
- AC1: Validate eligibility to play
- AC2: InstantWinAttempted event published
- AC3: InstantWinPlayed event on valid play
- AC4: Check against daily/total limits

---

#### REQ-IW-BE-006: Win Determination
**Statement**: The system SHALL determine instant win results.

**Phase**: 4

**Acceptance Criteria**:
- AC1: Random determination based on odds
- AC2: Check prize availability
- AC3: WinningMomentTriggered event on win
- AC4: NonWinningAttemptRecorded on loss
- AC5: PrizeInventoryUpdated on win

---

### 2.3 Prize Distribution

#### REQ-IW-BE-007: Instant Prize Award
**Statement**: The system SHALL award prizes to winners.

**Phase**: 4

**Acceptance Criteria**:
- AC1: InstantWinPrizeAwarded event
- AC2: Prize details captured
- AC3: WinnerDataCollected for fulfillment
- AC4: PrizeClaimInitiated/Completed events

---

#### REQ-IW-BE-008: Prize Inventory Tracking
**Statement**: The system SHALL track prize inventory.

**Phase**: 4

**Acceptance Criteria**:
- AC1: Real-time inventory updates
- AC2: PrizeAllocationDepleted when exhausted
- AC3: Inventory alerts for low stock
- AC4: Automatic game pause on depletion

---

---

## 3. Domain Model

```
Aggregate: InstantWinAggregate
Location: MarketingPlatform.Core/Model/InstantWinAggregate/

Entities:
- InstantWinGame (Aggregate Root)
- InstantWinPrize
- InstantWinPlay
- WinningMoment

Value Objects:
- PlayAttemptId
- WinOdds
- PrizeInventory

Enums:
- GameStatus (Draft, Active, Paused, Completed)
- PlayResult (Win, Loss)
```

---

## 4. API Endpoints

| Method | Endpoint | Description | Phase |
|--------|----------|-------------|-------|
| POST | /api/instant-win | Create game | 4 |
| GET | /api/instant-win/{id} | Get game | 4 |
| PUT | /api/instant-win/{id} | Update game | 4 |
| POST | /api/instant-win/{id}/prizes | Add prize | 4 |
| PUT | /api/instant-win/{id}/odds | Set odds | 4 |
| POST | /api/instant-win/{id}/play | Submit play | 4 |
| GET | /api/instant-win/{id}/winners | List winners | 4 |
| GET | /api/instant-win/{id}/inventory | Check inventory | 4 |

---

## 5. Domain Events

| Event | Trigger | Phase |
|-------|---------|-------|
| InstantWinCreated | Game creation | 4 |
| InstantWinPrizePoolConfigured | Prize setup | 4 |
| WinningOddsSet | Odds config | 4 |
| TotalPrizesAllocated | Prizes set | 4 |
| DailyWinLimitSet | Limit config | 4 |
| PrizeDistributionScheduled | Schedule set | 4 |
| InstantWinAttempted | Play attempt | 4 |
| InstantWinPlayed | Valid play | 4 |
| PrizeWonInstantly | Win result | 4 |
| NonWinningAttemptRecorded | Loss result | 4 |
| WinningMomentTriggered | Win triggered | 4 |
| InstantWinPrizeAwarded | Prize given | 4 |
| PrizeInventoryUpdated | Stock change | 4 |
| PrizeAllocationDepleted | Out of prizes | 4 |
| WinnerDataCollected | Winner info | 4 |
| PrizeClaimCompleted | Claim done | 4 |

---

*End of Instant Win Backend Specifications*
