# Quiz Features - Backend Specifications

**Feature**: Quiz Features
**Phase**: 3 (Enhanced Features)
**Document Version**: 1.0
**Last Updated**: 2025-12-24

---

## 1. Overview

Quiz Features enables users to create engaging trivia quizzes and personality quizzes to boost participant engagement and collect data.

---

## 2. Requirements

### 2.1 Trivia Quiz

#### REQ-QZ-BE-001: Trivia Quiz Creation
**Statement**: The system SHALL allow creating trivia quizzes with scored questions.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Quiz created with title and description
- AC2: TriviaQuizCreated event published
- AC3: Multiple questions supported
- AC4: Scoring rules configurable

---

#### REQ-QZ-BE-002: Trivia Question Management
**Statement**: The system SHALL support managing trivia questions.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Add questions (TriviaQuestionAdded event)
- AC2: Remove questions (TriviaQuestionRemoved event)
- AC3: Update questions (TriviaQuestionUpdated event)
- AC4: Question order configurable

---

#### REQ-QZ-BE-003: Answer Configuration
**Statement**: The system SHALL support configuring correct and wrong answers.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Multiple choice answers (min 2, max 6)
- AC2: CorrectAnswerSet event for right answer
- AC3: WrongAnswerAdded event for distractors
- AC4: Point value per question configurable

---

#### REQ-QZ-BE-004: Quiz Scoring
**Statement**: The system SHALL calculate quiz scores.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Score calculated based on correct answers
- AC2: QuizScoreCalculated event published
- AC3: Percentage and raw score tracked
- AC4: Time-based bonus scoring (optional)

---

### 2.2 Personality Quiz

#### REQ-QZ-BE-005: Personality Quiz Creation
**Statement**: The system SHALL allow creating personality/outcome quizzes.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Quiz with outcome-based results
- AC2: PersonalityQuizCreated event published
- AC3: Multiple outcomes defined
- AC4: Questions map to outcomes

---

#### REQ-QZ-BE-006: Outcome Configuration
**Statement**: The system SHALL support configuring personality outcomes.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Multiple outcomes with title/description
- AC2: PersonalityOutcomeConfigured event
- AC3: OutcomeWeightSet for answer mapping
- AC4: Outcome image configurable

---

#### REQ-QZ-BE-007: Personality Result Calculation
**Statement**: The system SHALL calculate personality results.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Result based on weighted answers
- AC2: PersonalityResultCalculated event
- AC3: PersonalityResultRevealed to participant
- AC4: Shareable result cards

---

### 2.3 Quiz Engagement

#### REQ-QZ-BE-008: Quiz Session Tracking
**Statement**: The system SHALL track quiz sessions.

**Phase**: 3

**Acceptance Criteria**:
- AC1: QuizStarted event on begin
- AC2: QuizAnswerSubmitted per question
- AC3: QuizCompleted event on finish
- AC4: QuizAbandoned event if not finished

---

#### REQ-QZ-BE-009: Quiz Timer
**Statement**: The system SHALL support timed quizzes.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Overall time limit configurable
- AC2: Per-question time limit (optional)
- AC3: QuizTimerStarted/QuizTimerExpired events
- AC4: Auto-submit on time expiry

---

#### REQ-QZ-BE-010: Quiz Retakes
**Statement**: The system SHALL support quiz retakes.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Retake allowed configurable
- AC2: QuizRetaken event published
- AC3: Max retakes limit
- AC4: Best/latest score option

---

---

## 3. Domain Model

```
Aggregate: QuizAggregate
Location: MarketingPlatform.Core/Model/QuizAggregate/

Entities:
- Quiz (Aggregate Root)
- QuizQuestion
- QuizAnswer
- QuizOutcome (personality)
- QuizSession

Enums:
- QuizType (Trivia, Personality)
- QuizStatus (Draft, Published, Closed)
```

---

## 4. API Endpoints

| Method | Endpoint | Description | Phase |
|--------|----------|-------------|-------|
| POST | /api/quizzes | Create quiz | 3 |
| GET | /api/quizzes/{id} | Get quiz | 3 |
| PUT | /api/quizzes/{id} | Update quiz | 3 |
| POST | /api/quizzes/{id}/questions | Add question | 3 |
| PUT | /api/quizzes/{id}/questions/{qid} | Update question | 3 |
| POST | /api/quizzes/{id}/outcomes | Add outcome | 3 |
| POST | /api/quizzes/{id}/start | Start session | 3 |
| POST | /api/quizzes/{id}/answer | Submit answer | 3 |
| POST | /api/quizzes/{id}/complete | Complete quiz | 3 |
| GET | /api/quizzes/{id}/leaderboard | Get leaderboard | 3 |

---

## 5. Domain Events

| Event | Trigger | Phase |
|-------|---------|-------|
| TriviaQuizCreated | Trivia creation | 3 |
| PersonalityQuizCreated | Personality creation | 3 |
| TriviaQuestionAdded | Question add | 3 |
| CorrectAnswerSet | Answer marked | 3 |
| PersonalityOutcomeConfigured | Outcome setup | 3 |
| QuizStarted | Session start | 3 |
| QuizAnswerSubmitted | Answer submit | 3 |
| QuizScoreCalculated | Score calc | 3 |
| QuizCompleted | Quiz finish | 3 |
| QuizAbandoned | Quiz abandoned | 3 |
| QuizRetaken | Retake | 3 |
| QuizTimerExpired | Time up | 3 |
| LeaderboardEntryAdded | Score recorded | 3 |

---

*End of Quiz Features Backend Specifications*
