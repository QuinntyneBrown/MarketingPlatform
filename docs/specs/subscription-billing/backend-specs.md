# Subscription & Billing - Backend Specifications

**Feature**: Subscription & Billing
**Phase**: 5 (Full Feature)
**Document Version**: 1.0
**Last Updated**: 2025-12-24

---

## 1. Overview

Subscription & Billing manages user subscriptions, payment processing, and plan management for the platform.

---

## 2. Requirements

### 2.1 Subscription Management

#### REQ-SB-BE-001: Free Trial
**Statement**: The system SHALL support free trial periods.

**Phase**: 5

**Acceptance Criteria**:
- AC1: FreeTrialStarted event on signup
- AC2: Configurable trial duration
- AC3: Trial expiration warning
- AC4: Automatic conversion or downgrade

---

#### REQ-SB-BE-002: Subscription Lifecycle
**Statement**: The system SHALL manage subscription lifecycle.

**Phase**: 5

**Acceptance Criteria**:
- AC1: SubscriptionCreated on purchase
- AC2: SubscriptionUpgraded/Downgraded for plan changes
- AC3: SubscriptionRenewed on renewal
- AC4: SubscriptionCancelled on cancellation
- AC5: SubscriptionExpired on expiry

---

### 2.2 Billing

#### REQ-SB-BE-003: Payment Processing
**Statement**: The system SHALL process payments.

**Phase**: 5

**Acceptance Criteria**:
- AC1: PaymentProcessed event on success
- AC2: PaymentFailed event on failure
- AC3: Stripe/payment gateway integration
- AC4: Multiple payment methods

---

#### REQ-SB-BE-004: Invoice Generation
**Statement**: The system SHALL generate invoices.

**Phase**: 5

**Acceptance Criteria**:
- AC1: InvoiceGenerated event
- AC2: InvoicePaid on payment
- AC3: PDF invoice download
- AC4: Invoice history

---

### 2.3 Plan Management

#### REQ-SB-BE-005: Feature Gating
**Statement**: The system SHALL gate features by plan.

**Phase**: 5

**Acceptance Criteria**:
- AC1: FeatureUnlocked/Locked events
- AC2: Plan feature matrix
- AC3: Usage limits per plan
- AC4: ParticipantLimitReached enforcement

---

---

## 3. Domain Model

```
Aggregate: BillingAggregate
Location: MarketingPlatform.Core/Model/BillingAggregate/

Entities:
- Subscription (Aggregate Root)
- Invoice
- Payment
- Plan

Enums:
- SubscriptionStatus (Trial, Active, PastDue, Cancelled, Expired)
- BillingCycle (Monthly, Annual)
- PaymentStatus (Pending, Completed, Failed, Refunded)
```

---

## 4. API Endpoints

| Method | Endpoint | Description | Phase |
|--------|----------|-------------|-------|
| GET | /api/subscription | Get current | 5 |
| POST | /api/subscription | Create | 5 |
| PUT | /api/subscription/plan | Change plan | 5 |
| POST | /api/subscription/cancel | Cancel | 5 |
| GET | /api/invoices | List invoices | 5 |
| GET | /api/invoices/{id}/pdf | Download PDF | 5 |
| POST | /api/payments | Process payment | 5 |

---

*End of Subscription & Billing Backend Specifications*
