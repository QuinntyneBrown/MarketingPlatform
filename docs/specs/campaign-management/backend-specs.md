# Campaign Management - Backend Specifications

**Feature**: Campaign Management
**Phase**: 1 (MVP)
**Document Version**: 1.0
**Last Updated**: 2025-12-24

---

## 1. Overview

Campaign Management is the core feature of the Marketing Platform, enabling users to create, configure, publish, and manage marketing campaigns. This is a Phase 1 (MVP) feature essential for the minimum viable product.

---

## 2. Requirements

### 2.1 Campaign Lifecycle Management

#### REQ-CM-BE-001: Campaign Creation
**Statement**: The system SHALL allow authenticated users to create new marketing campaigns with basic configuration.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Users can create a campaign by providing a name and optional description
- AC2: A unique CampaignId is generated upon creation
- AC3: New campaigns are created in "Draft" status by default
- AC4: CampaignCreated domain event is published upon successful creation
- AC5: The campaign is associated with the user's BusinessId

---

#### REQ-CM-BE-002: Campaign Draft State
**Statement**: The system SHALL support saving campaigns in a draft state for later editing.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Campaigns can be saved without being published
- AC2: Draft campaigns are not visible to end participants
- AC3: CampaignDrafted event is published when explicitly saved as draft
- AC4: All campaign properties can be modified while in draft state

---

#### REQ-CM-BE-003: Campaign Publishing
**Statement**: The system SHALL allow users to publish draft campaigns to make them active.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Only campaigns in "Draft" or "Paused" status can be published
- AC2: Publishing sets the campaign status to "Published"
- AC3: CampaignPublished event is published upon successful publishing
- AC4: Published campaigns are accessible to end participants
- AC5: Campaigns with validation errors cannot be published

---

#### REQ-CM-BE-004: Campaign Pausing
**Statement**: The system SHALL allow users to pause active campaigns temporarily.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Only campaigns in "Published" status can be paused
- AC2: Pausing sets the campaign status to "Paused"
- AC3: CampaignPaused event is published
- AC4: Paused campaigns are not accessible to new participants
- AC5: Existing participant data is preserved

---

#### REQ-CM-BE-005: Campaign Resumption
**Statement**: The system SHALL allow users to resume paused campaigns.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Only campaigns in "Paused" status can be resumed
- AC2: Resuming sets the campaign status to "Published"
- AC3: CampaignResumed event is published
- AC4: Campaign becomes accessible to participants again

---

#### REQ-CM-BE-006: Campaign Completion
**Statement**: The system SHALL allow users to mark campaigns as completed.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Published or Paused campaigns can be completed
- AC2: Completing sets the campaign status to "Completed"
- AC3: CampaignCompleted event is published
- AC4: Completed campaigns cannot accept new entries
- AC5: All campaign data remains accessible for reporting

---

#### REQ-CM-BE-007: Campaign Archival
**Statement**: The system SHALL allow users to archive completed campaigns.

**Phase**: 2

**Acceptance Criteria**:
- AC1: Only campaigns in "Completed" status can be archived
- AC2: CampaignArchived event is published
- AC3: Archived campaigns are hidden from default campaign lists
- AC4: Archived campaigns can be restored if needed

---

#### REQ-CM-BE-008: Campaign Deletion
**Statement**: The system SHALL allow users to delete draft campaigns.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Only campaigns in "Draft" status can be hard deleted
- AC2: Published campaigns can only be soft deleted (archived)
- AC3: CampaignDeleted event is published
- AC4: All associated data is removed upon hard deletion

---

#### REQ-CM-BE-009: Campaign Cloning
**Statement**: The system SHALL allow users to clone existing campaigns as templates.

**Phase**: 2

**Acceptance Criteria**:
- AC1: Any campaign regardless of status can be cloned
- AC2: Cloned campaign is created in "Draft" status
- AC3: CampaignCloned event is published with source campaign reference
- AC4: All configuration is copied except participant data
- AC5: New unique CampaignId is assigned to the clone

---

### 2.2 Campaign Configuration

#### REQ-CM-BE-010: Campaign Basic Configuration
**Statement**: The system SHALL allow users to configure basic campaign properties.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Users can set/update campaign name (max 200 characters)
- AC2: Users can set/update campaign description (max 2000 characters)
- AC3: CampaignNameUpdated and CampaignDescriptionUpdated events are published
- AC4: Changes are persisted immediately

---

#### REQ-CM-BE-011: Campaign Type Configuration
**Statement**: The system SHALL support different campaign types.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Supported types: Giveaway, Contest, Poll, Quiz, Form
- AC2: Campaign type is set at creation and can be changed in Draft status
- AC3: CampaignTypeChanged event is published when type changes
- AC4: Type determines available configuration options

---

#### REQ-CM-BE-012: Campaign Duration Configuration
**Statement**: The system SHALL allow users to configure campaign duration.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Users can set optional start date/time
- AC2: Users can set optional end date/time
- AC3: CampaignStartDateSet and CampaignEndDateSet events are published
- AC4: End date must be after start date if both are set
- AC5: All dates are stored in UTC

---

#### REQ-CM-BE-013: Campaign Auto-Start/End
**Statement**: The system SHALL automatically start and end campaigns based on configured dates.

**Phase**: 2

**Acceptance Criteria**:
- AC1: Background service checks for campaigns to auto-start/end
- AC2: CampaignAutoStarted event published when scheduled start occurs
- AC3: CampaignAutoEnded event published when scheduled end occurs
- AC4: Notifications sent to campaign owners on auto-transitions

---

#### REQ-CM-BE-014: Campaign Branding Configuration
**Statement**: The system SHALL allow users to customize campaign branding.

**Phase**: 2

**Acceptance Criteria**:
- AC1: Users can upload a logo (max 5MB, PNG/JPG/SVG)
- AC2: Users can set primary and secondary colors
- AC3: CampaignBrandingApplied, CampaignLogoUploaded events published
- AC4: Branding is validated for accessibility contrast ratios

---

#### REQ-CM-BE-015: Campaign Custom Code
**Statement**: The system SHALL allow advanced users to inject custom CSS/HTML/JavaScript.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Custom CSS can be applied (max 50KB)
- AC2: Custom HTML can be added to header/footer (max 20KB)
- AC3: Custom JavaScript can be injected (max 30KB, sandboxed)
- AC4: CampaignCustomCSSApplied, CampaignCustomHTMLApplied, CampaignCustomJavaScriptApplied events published
- AC5: Content is sanitized for XSS prevention

---

### 2.3 Campaign Access & Distribution

#### REQ-CM-BE-016: Campaign URL Generation
**Statement**: The system SHALL generate unique URLs for each campaign.

**Phase**: 1

**Acceptance Criteria**:
- AC1: A unique slug-based URL is generated for each campaign
- AC2: CampaignDedicatedURLGenerated event is published
- AC3: URLs are human-readable when possible (slugified from name)
- AC4: URL format: {base-domain}/c/{campaign-slug}

---

#### REQ-CM-BE-017: Campaign Embedding
**Statement**: The system SHALL provide embed codes for website integration.

**Phase**: 2

**Acceptance Criteria**:
- AC1: Iframe embed code is generated for each published campaign
- AC2: JavaScript embed snippet is provided for dynamic embedding
- AC3: CampaignEmbeddedOnWebsite event tracked when embed code used
- AC4: Responsive embed options available

---

### 2.4 Campaign Retrieval

#### REQ-CM-BE-018: Campaign List Retrieval
**Statement**: The system SHALL provide paginated campaign listings.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Campaigns are filtered by BusinessId for the authenticated user
- AC2: Pagination with configurable page size (default 20, max 100)
- AC3: Sorting by created date, name, status
- AC4: Filtering by status, type, date range
- AC5: Archived campaigns excluded by default (optional include)

---

#### REQ-CM-BE-019: Campaign Detail Retrieval
**Statement**: The system SHALL provide detailed campaign information.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Full campaign configuration returned by CampaignId
- AC2: Includes status, type, dates, branding, and statistics summary
- AC3: Authorization verified for campaign ownership
- AC4: 404 returned for non-existent campaigns

---

---

## 3. Domain Model

### 3.1 Campaign Aggregate

```
Aggregate: CampaignAggregate
Location: MarketingPlatform.Core/Model/CampaignAggregate/

Entities:
- Campaign (Aggregate Root)
- CampaignBranding
- CampaignSettings

Value Objects:
- CampaignId
- CampaignSlug
- CampaignDuration

Enums:
- CampaignStatus (Draft, Published, Paused, Completed, Archived)
- CampaignType (Giveaway, Contest, Poll, Quiz, Form)
```

### 3.2 Properties

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| CampaignId | Guid | Yes | Unique identifier |
| BusinessId | Guid | Yes | Owning business |
| Name | string | Yes | Campaign name (max 200) |
| Description | string | No | Campaign description (max 2000) |
| Slug | string | Yes | URL-friendly identifier |
| Type | CampaignType | Yes | Type of campaign |
| Status | CampaignStatus | Yes | Current lifecycle status |
| StartDate | DateTimeOffset? | No | Scheduled start |
| EndDate | DateTimeOffset? | No | Scheduled end |
| CreatedAt | DateTimeOffset | Yes | Creation timestamp |
| UpdatedAt | DateTimeOffset | Yes | Last update timestamp |
| CreatedBy | Guid | Yes | Creating user ID |

---

## 4. API Endpoints

### 4.1 Campaign Management APIs

| Method | Endpoint | Description | Phase |
|--------|----------|-------------|-------|
| POST | /api/campaigns | Create campaign | 1 |
| GET | /api/campaigns | List campaigns | 1 |
| GET | /api/campaigns/{id} | Get campaign details | 1 |
| PUT | /api/campaigns/{id} | Update campaign | 1 |
| DELETE | /api/campaigns/{id} | Delete campaign | 1 |
| POST | /api/campaigns/{id}/publish | Publish campaign | 1 |
| POST | /api/campaigns/{id}/pause | Pause campaign | 1 |
| POST | /api/campaigns/{id}/resume | Resume campaign | 1 |
| POST | /api/campaigns/{id}/complete | Complete campaign | 1 |
| POST | /api/campaigns/{id}/archive | Archive campaign | 2 |
| POST | /api/campaigns/{id}/clone | Clone campaign | 2 |

---

## 5. Domain Events

| Event | Trigger | Phase |
|-------|---------|-------|
| CampaignCreated | Campaign creation | 1 |
| CampaignDrafted | Saved as draft | 1 |
| CampaignPublished | Publishing | 1 |
| CampaignPaused | Pausing | 1 |
| CampaignResumed | Resuming | 1 |
| CampaignCompleted | Completion | 1 |
| CampaignArchived | Archival | 2 |
| CampaignDeleted | Deletion | 1 |
| CampaignCloned | Cloning | 2 |
| CampaignNameUpdated | Name change | 1 |
| CampaignDescriptionUpdated | Description change | 1 |
| CampaignTypeChanged | Type change | 1 |
| CampaignStartDateSet | Start date set | 1 |
| CampaignEndDateSet | End date set | 1 |
| CampaignAutoStarted | Auto-start trigger | 2 |
| CampaignAutoEnded | Auto-end trigger | 2 |
| CampaignBrandingApplied | Branding update | 2 |
| CampaignLogoUploaded | Logo upload | 2 |
| CampaignDedicatedURLGenerated | URL generation | 1 |

---

## 6. Validation Rules

| Rule | Description | Error Code |
|------|-------------|------------|
| VR-CM-001 | Campaign name is required | CAMPAIGN_NAME_REQUIRED |
| VR-CM-002 | Campaign name max 200 chars | CAMPAIGN_NAME_TOO_LONG |
| VR-CM-003 | Description max 2000 chars | CAMPAIGN_DESC_TOO_LONG |
| VR-CM-004 | End date must be after start date | INVALID_DATE_RANGE |
| VR-CM-005 | Only draft campaigns can be deleted | CANNOT_DELETE_PUBLISHED |
| VR-CM-006 | Only draft/paused can be published | INVALID_STATUS_TRANSITION |
| VR-CM-007 | Campaign type is required | CAMPAIGN_TYPE_REQUIRED |

---

## 7. Security Considerations

- All endpoints require authentication
- Campaign access restricted to owning BusinessId
- Rate limiting: 100 requests per minute per user
- Input sanitization for all text fields
- XSS prevention for custom CSS/HTML/JavaScript

---

*End of Campaign Management Backend Specifications*
