# Forms & Data Collection - Backend Specifications

**Feature**: Forms & Data Collection
**Phase**: 1 (MVP)
**Document Version**: 1.0
**Last Updated**: 2025-12-24

---

## 1. Overview

Forms & Data Collection enables users to create custom forms for collecting participant information. This is a Phase 1 (MVP) feature essential for capturing leads and entries across all campaign types.

---

## 2. Requirements

### 2.1 Form Builder

#### REQ-FORM-BE-001: Custom Form Creation
**Statement**: The system SHALL allow users to create custom forms with configurable fields.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Forms can be created with a name and description
- AC2: CustomFormCreated event published
- AC3: Form associated with a campaign
- AC4: Multiple forms per campaign supported

---

#### REQ-FORM-BE-002: Field Management
**Statement**: The system SHALL support adding, removing, and reordering form fields.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Fields can be added to forms
- AC2: FormFieldAdded event published per field
- AC3: Fields can be removed (FormFieldRemoved event)
- AC4: Fields can be reordered (FormFieldReordered event)

---

#### REQ-FORM-BE-003: Field Type Support
**Statement**: The system SHALL support multiple field types.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Text field (single line, multiline)
- AC2: Email field with validation
- AC3: Phone field with formatting
- AC4: Date field with picker
- AC5: Dropdown/select field
- AC6: Checkbox field
- AC7: Radio button field
- AC8: File upload field (Phase 2)
- AC9: Address field (Phase 2)

---

#### REQ-FORM-BE-004: Field Configuration
**Statement**: The system SHALL allow configuring field properties.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Label text configurable
- AC2: Placeholder text configurable
- AC3: Required/optional toggle
- AC4: Default value support
- AC5: FormFieldConfigured event published

---

#### REQ-FORM-BE-005: Field Validation Rules
**Statement**: The system SHALL support field validation rules.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Required field validation
- AC2: Min/max length for text
- AC3: Pattern matching (regex)
- AC4: Email format validation
- AC5: FormValidationRuleAdded event published

---

#### REQ-FORM-BE-006: Conditional Logic
**Statement**: The system SHALL support conditional field visibility.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Show/hide field based on other field values
- AC2: Multiple conditions supported (AND/OR)
- AC3: ConditionalLogicApplied event published
- AC4: Validation skipped for hidden fields

---

### 2.2 Form Submission

#### REQ-FORM-BE-007: Form Submission
**Statement**: The system SHALL process and store form submissions.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Submissions validated against form schema
- AC2: FormSubmitted event published
- AC3: All field values stored
- AC4: Submission timestamp recorded
- AC5: Participant IP and user agent captured

---

#### REQ-FORM-BE-008: Submission Validation
**Statement**: The system SHALL validate submissions server-side.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Required fields checked
- AC2: Field type validation (email format, etc.)
- AC3: FormValidationPassed or FormValidationFailed event
- AC4: Detailed error messages returned
- AC5: RequiredFieldMissing, InvalidEmailFormat events

---

#### REQ-FORM-BE-009: Submission Storage
**Statement**: The system SHALL securely store submission data.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Data encrypted at rest
- AC2: SubmissionSaved event published
- AC3: Queryable by form and date range
- AC4: PII handling compliant with privacy settings

---

#### REQ-FORM-BE-010: Submission Export
**Statement**: The system SHALL allow exporting submission data.

**Phase**: 2

**Acceptance Criteria**:
- AC1: Export to CSV format
- AC2: Export to Excel format
- AC3: SubmissionExported event published
- AC4: Date range filtering for export
- AC5: Field selection for export

---

---

## 3. Domain Model

### 3.1 Form Aggregate

```
Aggregate: FormAggregate
Location: MarketingPlatform.Core/Model/FormAggregate/

Entities:
- Form (Aggregate Root)
- FormField
- FormSubmission
- FieldValue

Value Objects:
- FormId
- FormFieldId
- FormSubmissionId
- FieldType
- ValidationRule

Enums:
- FieldType (Text, Email, Phone, Date, Dropdown, Checkbox, Radio, File, Address)
- ValidationRuleType (Required, MinLength, MaxLength, Pattern, Email, Phone)
```

---

## 4. API Endpoints

| Method | Endpoint | Description | Phase |
|--------|----------|-------------|-------|
| POST | /api/forms | Create form | 1 |
| GET | /api/forms/{id} | Get form | 1 |
| PUT | /api/forms/{id} | Update form | 1 |
| DELETE | /api/forms/{id} | Delete form | 1 |
| POST | /api/forms/{id}/fields | Add field | 1 |
| PUT | /api/forms/{id}/fields/{fieldId} | Update field | 1 |
| DELETE | /api/forms/{id}/fields/{fieldId} | Remove field | 1 |
| POST | /api/forms/{id}/fields/reorder | Reorder fields | 1 |
| POST | /api/forms/{id}/submissions | Submit form | 1 |
| GET | /api/forms/{id}/submissions | List submissions | 1 |
| GET | /api/forms/{id}/submissions/export | Export submissions | 2 |

---

## 5. Domain Events

| Event | Trigger | Phase |
|-------|---------|-------|
| CustomFormCreated | Form creation | 1 |
| FormFieldAdded | Field added | 1 |
| FormFieldRemoved | Field removed | 1 |
| FormFieldReordered | Fields reordered | 1 |
| FormFieldConfigured | Field updated | 1 |
| FormValidationRuleAdded | Rule added | 1 |
| ConditionalLogicApplied | Logic added | 3 |
| FormSubmitted | Submission received | 1 |
| FormValidationPassed | Validation success | 1 |
| FormValidationFailed | Validation failure | 1 |
| SubmissionSaved | Submission stored | 1 |
| SubmissionExported | Export completed | 2 |

---

*End of Forms & Data Collection Backend Specifications*
