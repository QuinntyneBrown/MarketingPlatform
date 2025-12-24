# Popup Management - Backend Specifications

**Feature**: Popup Management
**Phase**: 4 (Advanced Features)
**Document Version**: 1.0
**Last Updated**: 2025-12-24

---

## 1. Overview

Popup Management enables creating and managing popup campaigns for website integration.

---

## 2. Requirements

### 2.1 Popup Configuration

#### REQ-PU-BE-001: Popup Creation
**Statement**: The system SHALL support popup creation.

**Phase**: 4

**Acceptance Criteria**:
- AC1: PopupCreated event
- AC2: Popup content configurable
- AC3: Display rules configurable
- AC4: Campaign association

---

#### REQ-PU-BE-002: Trigger Configuration
**Statement**: The system SHALL support popup triggers.

**Phase**: 4

**Acceptance Criteria**:
- AC1: PopupTriggerSet event
- AC2: Exit intent trigger
- AC3: Scroll percentage trigger
- AC4: Time delay trigger
- AC5: PopupDelayConfigured for timing

---

#### REQ-PU-BE-003: Frequency Control
**Statement**: The system SHALL control popup frequency.

**Phase**: 4

**Acceptance Criteria**:
- AC1: PopupFrequencySet event
- AC2: Once per session option
- AC3: Once per visitor option
- AC4: Cool-down period

---

### 2.2 Popup Display

#### REQ-PU-BE-004: Display Tracking
**Statement**: The system SHALL track popup displays.

**Phase**: 4

**Acceptance Criteria**:
- AC1: PopupDisplayed event
- AC2: PopupViewed for impressions
- AC3: PopupClicked for engagement
- AC4: PopupDismissed for closes
- AC5: PopupConverted for conversions

---

### 2.3 Optimization

#### REQ-PU-BE-005: A/B Testing
**Statement**: The system SHALL support popup A/B testing.

**Phase**: 4

**Acceptance Criteria**:
- AC1: PopupTestVariantCreated event
- AC2: Traffic splitting
- AC3: PopupPerformanceAnalyzed metrics
- AC4: PopupOptimizationApplied winner

---

---

## 3. Domain Model

```
Aggregate: PopupAggregate
Location: MarketingPlatform.Core/Model/PopupAggregate/

Entities:
- Popup (Aggregate Root)
- PopupTrigger
- PopupVariant

Enums:
- TriggerType (ExitIntent, Scroll, TimeDelay, Click)
- PopupPosition (Center, TopBar, BottomBar, Corner)
- FrequencyType (Always, OncePerSession, OncePerVisitor)
```

---

## 4. API Endpoints

| Method | Endpoint | Description | Phase |
|--------|----------|-------------|-------|
| POST | /api/popups | Create popup | 4 |
| GET | /api/popups/{id} | Get popup | 4 |
| PUT | /api/popups/{id} | Update popup | 4 |
| PUT | /api/popups/{id}/trigger | Set trigger | 4 |
| POST | /api/popups/{id}/track | Track event | 4 |
| GET | /api/popups/{id}/analytics | Get analytics | 4 |

---

*End of Popup Management Backend Specifications*
