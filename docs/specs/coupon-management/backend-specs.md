# Coupon Management - Backend Specifications

**Feature**: Coupon Management
**Phase**: 3 (Enhanced Features)
**Document Version**: 1.0
**Last Updated**: 2025-12-24

---

## 1. Overview

Coupon Management enables users to create, distribute, and track digital coupons as campaign incentives and prizes.

---

## 2. Requirements

### 2.1 Coupon Lifecycle

#### REQ-CP-BE-001: Coupon Campaign Creation
**Statement**: The system SHALL allow creating coupon distribution campaigns.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Coupon campaign with name and description
- AC2: CouponCampaignCreated event published
- AC3: Linked to parent marketing campaign
- AC4: Distribution rules configurable

---

#### REQ-CP-BE-002: Coupon Code Generation
**Statement**: The system SHALL generate unique coupon codes.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Auto-generate unique alphanumeric codes
- AC2: CouponGenerated event per code
- AC3: UniqueCodeGenerated for each code
- AC4: Bulk generation supported

---

#### REQ-CP-BE-003: Coupon Activation/Deactivation
**Statement**: The system SHALL support activating and deactivating coupons.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Coupons start inactive by default
- AC2: CouponActivated event on activation
- AC3: CouponDeactivated event on deactivation
- AC4: Bulk activation supported

---

### 2.2 Coupon Configuration

#### REQ-CP-BE-004: Coupon Value Configuration
**Statement**: The system SHALL support configuring coupon values.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Percentage discount type
- AC2: Fixed amount discount type
- AC3: CouponValueSet event published
- AC4: Currency configuration for fixed

---

#### REQ-CP-BE-005: Expiration Configuration
**Statement**: The system SHALL support coupon expiration.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Expiration date configurable
- AC2: CouponExpirationDateSet event
- AC3: CouponExpired event on expiry
- AC4: Days from issue option

---

#### REQ-CP-BE-006: Redemption Limits
**Statement**: The system SHALL support redemption limits.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Max total redemptions
- AC2: One per person option
- AC3: CouponRedemptionLimitSet event
- AC4: OnePerPersonCouponEnforced event

---

### 2.3 Coupon Distribution

#### REQ-CP-BE-007: Coupon Issuance
**Statement**: The system SHALL issue coupons to participants.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Issue on form completion
- AC2: CouponIssued event published
- AC3: Unique code assigned to participant
- AC4: Issue on trigger events

---

#### REQ-CP-BE-008: Coupon Delivery
**Statement**: The system SHALL deliver coupons via email.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Email with coupon code
- AC2: CouponEmailed event published
- AC3: Branded email template
- AC4: Delivery tracking

---

### 2.4 Coupon Redemption

#### REQ-CP-BE-009: Redemption Tracking
**Statement**: The system SHALL track coupon redemptions.

**Phase**: 3

**Acceptance Criteria**:
- AC1: CouponRedeemed event on use
- AC2: Redemption timestamp recorded
- AC3: Redemption source tracked
- AC4: One-time use enforcement

---

#### REQ-CP-BE-010: Redemption Validation
**Statement**: The system SHALL validate coupon codes.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Code existence check
- AC2: Expiration check
- AC3: Usage limit check
- AC4: CouponRedemptionValidated/Rejected events

---

---

## 3. Domain Model

```
Aggregate: CouponAggregate
Location: MarketingPlatform.Core/Model/CouponAggregate/

Entities:
- CouponCampaign (Aggregate Root)
- Coupon
- CouponRedemption

Value Objects:
- CouponCode
- CouponValue
- ExpirationPolicy

Enums:
- CouponStatus (Inactive, Active, Redeemed, Expired)
- DiscountType (Percentage, FixedAmount, FreeItem)
```

---

## 4. API Endpoints

| Method | Endpoint | Description | Phase |
|--------|----------|-------------|-------|
| POST | /api/coupon-campaigns | Create campaign | 3 |
| GET | /api/coupon-campaigns/{id} | Get campaign | 3 |
| POST | /api/coupon-campaigns/{id}/generate | Generate codes | 3 |
| POST | /api/coupons/{id}/activate | Activate coupon | 3 |
| POST | /api/coupons/{id}/deactivate | Deactivate | 3 |
| POST | /api/coupons/{id}/issue | Issue to participant | 3 |
| POST | /api/coupons/validate | Validate code | 3 |
| POST | /api/coupons/redeem | Redeem code | 3 |
| GET | /api/coupon-campaigns/{id}/redemptions | List redemptions | 3 |

---

## 5. Domain Events

| Event | Trigger | Phase |
|-------|---------|-------|
| CouponCampaignCreated | Campaign creation | 3 |
| CouponGenerated | Code generation | 3 |
| UniqueCodeGenerated | Each code created | 3 |
| CouponActivated | Activation | 3 |
| CouponDeactivated | Deactivation | 3 |
| CouponValueSet | Value config | 3 |
| CouponExpirationDateSet | Expiry config | 3 |
| CouponRedemptionLimitSet | Limit config | 3 |
| CouponIssued | Issue to participant | 3 |
| CouponEmailed | Email sent | 3 |
| CouponRedeemed | Redemption | 3 |
| CouponRedemptionValidated | Valid code | 3 |
| CouponRedemptionRejected | Invalid code | 3 |
| CouponExpired | Expiration | 3 |

---

*End of Coupon Management Backend Specifications*
