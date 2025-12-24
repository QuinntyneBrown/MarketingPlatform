# Email Marketing Integration - Backend Specifications

**Feature**: Email Marketing Integration
**Phase**: 2 (Core Expansion)
**Document Version**: 1.0
**Last Updated**: 2025-12-24

---

## 1. Overview

Email Marketing Integration enables email collection, automated email sending, and integration with email service providers.

---

## 2. Requirements

### 2.1 Email Collection

#### REQ-EM-BE-001: Email List Management
**Statement**: The system SHALL support email list creation and management.

**Phase**: 2

**Acceptance Criteria**:
- AC1: EmailListCreated event on creation
- AC2: Lists associated with business account
- AC3: List naming and description
- AC4: Duplicate email prevention

---

#### REQ-EM-BE-002: Email Capture
**Statement**: The system SHALL capture emails from campaigns.

**Phase**: 2

**Acceptance Criteria**:
- AC1: EmailCaptured event on submission
- AC2: EmailValidated for format check
- AC3: EmailAddedToList for storage
- AC4: Consent recorded with capture

---

### 2.2 Automated Emails

#### REQ-EM-BE-003: Welcome Email
**Statement**: The system SHALL send welcome emails.

**Phase**: 2

**Acceptance Criteria**:
- AC1: WelcomeEmailSent event on send
- AC2: Triggered on participant registration
- AC3: Customizable template
- AC4: Delay configurable

---

#### REQ-EM-BE-004: Confirmation Email
**Statement**: The system SHALL send entry confirmation emails.

**Phase**: 2

**Acceptance Criteria**:
- AC1: ConfirmationEmailSent event
- AC2: Triggered on entry submission
- AC3: Entry details included
- AC4: Bonus entry opportunities shown

---

#### REQ-EM-BE-005: Winner Notification Email
**Statement**: The system SHALL send winner notifications.

**Phase**: 2

**Acceptance Criteria**:
- AC1: WinnerNotificationEmailSent event
- AC2: Prize details included
- AC3: Claim instructions provided
- AC4: Deadline for response

---

#### REQ-EM-BE-006: Reminder Emails
**Statement**: The system SHALL send campaign reminder emails.

**Phase**: 3

**Acceptance Criteria**:
- AC1: ReminderEmailSent event
- AC2: Before campaign end trigger
- AC3: Configurable timing
- AC4: Conditional send logic

---

### 2.3 Email Service Provider Integration

#### REQ-EM-BE-007: Mailchimp Integration
**Statement**: The system SHALL integrate with Mailchimp.

**Phase**: 3

**Acceptance Criteria**:
- AC1: MailchimpIntegrationConnected event
- AC2: MailchimpListSynced for list sync
- AC3: Automatic subscriber push
- AC4: Two-way sync support

---

#### REQ-EM-BE-008: Generic ESP Integration
**Statement**: The system SHALL support other ESPs.

**Phase**: 4

**Acceptance Criteria**:
- AC1: EmailServiceProviderConnected event
- AC2: EmailSyncCompleted on sync
- AC3: Webhook-based integration
- AC4: EmailExportTriggered for export

---

---

## 3. Domain Model

```
Aggregate: EmailMarketingAggregate
Location: MarketingPlatform.Core/Model/EmailMarketingAggregate/

Entities:
- EmailList (Aggregate Root)
- EmailSubscriber
- EmailCampaign
- EmailTemplate

Enums:
- EmailType (Welcome, Confirmation, Winner, Reminder, FollowUp)
- SubscriptionStatus (Active, Unsubscribed, Bounced)
- SyncStatus (Pending, Synced, Failed)
```

---

## 4. API Endpoints

| Method | Endpoint | Description | Phase |
|--------|----------|-------------|-------|
| POST | /api/email-lists | Create list | 2 |
| GET | /api/email-lists | List all | 2 |
| GET | /api/email-lists/{id} | Get list | 2 |
| GET | /api/email-lists/{id}/subscribers | List subscribers | 2 |
| POST | /api/email-lists/{id}/export | Export list | 2 |
| GET | /api/email-templates | List templates | 2 |
| PUT | /api/email-templates/{id} | Update template | 2 |
| POST | /api/integrations/mailchimp | Connect Mailchimp | 3 |
| POST | /api/integrations/mailchimp/sync | Sync to Mailchimp | 3 |

---

## 5. Domain Events

| Event | Trigger | Phase |
|-------|---------|-------|
| EmailListCreated | List creation | 2 |
| EmailCaptured | Email submitted | 2 |
| EmailValidated | Format validated | 2 |
| EmailAddedToList | Added to list | 2 |
| EmailListExported | Export complete | 2 |
| AutomatedEmailTriggered | Auto email start | 2 |
| WelcomeEmailSent | Welcome sent | 2 |
| ConfirmationEmailSent | Confirmation sent | 2 |
| WinnerNotificationEmailSent | Winner notified | 2 |
| ReminderEmailSent | Reminder sent | 3 |
| MailchimpIntegrationConnected | Mailchimp OAuth | 3 |
| MailchimpListSynced | Sync complete | 3 |
| EmailServiceProviderConnected | ESP connected | 4 |
| EmailSyncCompleted | Sync done | 4 |

---

*End of Email Marketing Integration Backend Specifications*
