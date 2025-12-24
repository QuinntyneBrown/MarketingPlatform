# Campaign Management - Frontend Specifications

**Feature**: Campaign Management
**Phase**: 1 (MVP)
**Document Version**: 1.0
**Last Updated**: 2025-12-24

---

## 1. Overview

This document specifies the frontend requirements for the Campaign Management feature, covering user interface components, user flows, and integration with the backend API.

---

## 2. Requirements

### 2.1 Campaign List Page

#### REQ-CM-FE-001: Campaign Dashboard Display
**Statement**: The system SHALL display a dashboard showing all user campaigns.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Campaigns displayed in a responsive card or table layout
- AC2: Each campaign shows: name, type, status, dates, entry count
- AC3: Status indicated with color-coded badges
- AC4: Empty state shown when no campaigns exist
- AC5: Loading skeleton shown during data fetch

---

#### REQ-CM-FE-002: Campaign Filtering
**Statement**: The system SHALL allow users to filter the campaign list.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Filter by status (Draft, Published, Paused, Completed, Archived)
- AC2: Filter by campaign type
- AC3: Filter by date range
- AC4: Filters are applied without page reload
- AC5: Active filters displayed as chips with remove option

---

#### REQ-CM-FE-003: Campaign Sorting
**Statement**: The system SHALL allow users to sort the campaign list.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Sort by name (A-Z, Z-A)
- AC2: Sort by creation date (newest, oldest)
- AC3: Sort by status
- AC4: Current sort indicated visually
- AC5: Sort preference persisted in local storage

---

#### REQ-CM-FE-004: Campaign Search
**Statement**: The system SHALL provide search functionality for campaigns.

**Phase**: 2

**Acceptance Criteria**:
- AC1: Search by campaign name
- AC2: Debounced input (300ms delay)
- AC3: Results update in real-time
- AC4: No results state shown when search yields nothing
- AC5: Clear search button available

---

#### REQ-CM-FE-005: Campaign Pagination
**Statement**: The system SHALL implement pagination for campaign lists.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Paginated results with configurable page size
- AC2: Page size options: 10, 20, 50
- AC3: Previous/Next navigation controls
- AC4: Current page indicator
- AC5: Total count displayed

---

### 2.2 Campaign Creation

#### REQ-CM-FE-006: Create Campaign Button
**Statement**: The system SHALL provide a prominent button to create new campaigns.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Floating action button (FAB) on mobile
- AC2: Header button on desktop
- AC3: Uses primary color from Material theme
- AC4: Accessible with keyboard navigation

---

#### REQ-CM-FE-007: Campaign Creation Dialog/Page
**Statement**: The system SHALL provide a form for campaign creation.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Campaign name input (required, max 200 chars)
- AC2: Campaign description textarea (optional, max 2000 chars)
- AC3: Campaign type selector (dropdown/radio)
- AC4: Start date picker (optional)
- AC5: End date picker (optional)
- AC6: Form validation with inline error messages
- AC7: Save as Draft and Create & Publish options

---

#### REQ-CM-FE-008: Campaign Type Selection
**Statement**: The system SHALL provide visual type selection.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Type options displayed as cards with icons
- AC2: Each type shows brief description
- AC3: Selected type highlighted
- AC4: Types: Giveaway, Contest, Poll, Quiz, Form

---

### 2.3 Campaign Editor

#### REQ-CM-FE-009: Campaign Settings Page
**Statement**: The system SHALL provide a comprehensive campaign editor.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Tab-based or stepper navigation for settings sections
- AC2: Sections: Basic Info, Design, Rules, Entries, Settings
- AC3: Auto-save every 30 seconds for draft campaigns
- AC4: Unsaved changes indicator
- AC5: Save button always accessible

---

#### REQ-CM-FE-010: Basic Information Section
**Statement**: The system SHALL allow editing of basic campaign properties.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Editable name field with character counter
- AC2: Editable description with rich text (basic formatting)
- AC3: Campaign type display (read-only after entries exist)
- AC4: Date range configuration with date pickers
- AC5: URL slug preview

---

#### REQ-CM-FE-011: Campaign Preview
**Statement**: The system SHALL provide real-time campaign preview.

**Phase**: 2

**Acceptance Criteria**:
- AC1: Preview panel showing how campaign appears to participants
- AC2: Toggle between desktop and mobile preview
- AC3: Preview updates as changes are made
- AC4: Full-screen preview option

---

#### REQ-CM-FE-012: Campaign Branding Editor
**Statement**: The system SHALL provide branding customization interface.

**Phase**: 2

**Acceptance Criteria**:
- AC1: Logo upload with drag-and-drop support
- AC2: Color picker for primary/secondary colors
- AC3: Font selection from approved list
- AC4: Real-time preview of branding changes
- AC5: Reset to defaults option

---

### 2.4 Campaign Actions

#### REQ-CM-FE-013: Campaign Quick Actions
**Statement**: The system SHALL provide quick action buttons for campaigns.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Edit action opens campaign editor
- AC2: Publish/Pause action with confirmation
- AC3: Delete action with confirmation dialog
- AC4: More actions menu for secondary actions
- AC5: Actions context-aware based on campaign status

---

#### REQ-CM-FE-014: Publish Confirmation
**Statement**: The system SHALL require confirmation before publishing.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Confirmation dialog with campaign summary
- AC2: Checklist of what will happen when published
- AC3: Cancel and Confirm buttons
- AC4: Loading state during publish operation

---

#### REQ-CM-FE-015: Delete Confirmation
**Statement**: The system SHALL require confirmation before deletion.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Warning dialog emphasizing irreversibility
- AC2: Campaign name displayed for verification
- AC3: Type campaign name to confirm (for published campaigns)
- AC4: Cancel and Delete buttons (Delete in error color)

---

#### REQ-CM-FE-016: Clone Campaign
**Statement**: The system SHALL allow cloning campaigns.

**Phase**: 2

**Acceptance Criteria**:
- AC1: Clone action available in more actions menu
- AC2: Dialog to set new campaign name
- AC3: Option to include/exclude certain settings
- AC4: Cloned campaign opens in editor

---

### 2.5 Campaign Status Management

#### REQ-CM-FE-017: Status Badge Display
**Statement**: The system SHALL display campaign status with visual indicators.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Draft: Grey badge
- AC2: Published: Green badge
- AC3: Paused: Yellow/Orange badge
- AC4: Completed: Blue badge
- AC5: Archived: Dark grey badge

---

#### REQ-CM-FE-018: Status Transition Validation
**Statement**: The system SHALL prevent invalid status transitions.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Invalid action buttons disabled with tooltip explanation
- AC2: Only valid actions shown in context menus
- AC3: Error message if transition fails

---

### 2.6 Campaign Sharing & Embedding

#### REQ-CM-FE-019: Share Campaign Dialog
**Statement**: The system SHALL provide sharing options for published campaigns.

**Phase**: 1

**Acceptance Criteria**:
- AC1: Campaign URL displayed with copy button
- AC2: Social sharing buttons (Twitter, Facebook, LinkedIn)
- AC3: QR code generation
- AC4: Success toast on copy

---

#### REQ-CM-FE-020: Embed Code Generator
**Statement**: The system SHALL provide embeddable code snippets.

**Phase**: 2

**Acceptance Criteria**:
- AC1: Iframe embed code with customizable dimensions
- AC2: JavaScript embed snippet
- AC3: WordPress shortcode
- AC4: Copy to clipboard functionality
- AC5: Preview of embed

---

---

## 3. Component Structure

### 3.1 Pages

| Component | Route | Description | Phase |
|-----------|-------|-------------|-------|
| CampaignList | /campaigns | Dashboard listing all campaigns | 1 |
| CampaignCreate | /campaigns/new | Campaign creation form | 1 |
| CampaignEdit | /campaigns/:id/edit | Campaign editor | 1 |
| CampaignDetail | /campaigns/:id | Campaign details and stats | 1 |

### 3.2 Components

| Component | Location | Description | Phase |
|-----------|----------|-------------|-------|
| CampaignCard | components/campaign-card | Card display for campaign | 1 |
| CampaignTable | components/campaign-table | Table display for campaigns | 1 |
| CampaignForm | components/campaign-form | Creation/Edit form | 1 |
| CampaignStatusBadge | components/campaign-status-badge | Status indicator | 1 |
| CampaignTypeIcon | components/campaign-type-icon | Type icon display | 1 |
| CampaignFilters | components/campaign-filters | Filter controls | 1 |
| CampaignActions | components/campaign-actions | Action buttons | 1 |
| ShareDialog | components/share-dialog | Sharing modal | 1 |
| DeleteConfirmDialog | components/delete-confirm-dialog | Delete confirmation | 1 |
| BrandingEditor | components/branding-editor | Branding customization | 2 |
| EmbedCodeGenerator | components/embed-code-generator | Embed codes | 2 |

### 3.3 Services

| Service | Description | Phase |
|---------|-------------|-------|
| CampaignService | HTTP operations for campaigns | 1 |

---

## 4. User Flows

### 4.1 Create Campaign Flow
1. User clicks "Create Campaign" button
2. Type selection dialog appears
3. User selects campaign type
4. Creation form opens with type pre-selected
5. User fills in name, description, dates
6. User clicks "Save as Draft" or "Create & Publish"
7. Redirect to campaign editor or list

### 4.2 Publish Campaign Flow
1. User opens campaign editor or clicks publish from list
2. Validation check runs
3. If errors, validation messages shown
4. If valid, confirmation dialog appears
5. User confirms
6. Campaign status updates to Published
7. Success toast shown

---

## 5. Wireframes Reference

Wireframes should be created for:
- Campaign list page (empty, populated, filtered)
- Campaign creation dialog
- Campaign editor tabs
- Campaign preview
- Share dialog
- Delete confirmation

---

## 6. Accessibility Requirements

- All interactive elements keyboard accessible
- Focus management in dialogs
- ARIA labels for icon-only buttons
- Color contrast ratio minimum 4.5:1
- Screen reader announcements for status changes

---

## 7. Responsive Design

| Breakpoint | Layout Changes |
|------------|----------------|
| < 600px | Single column, FAB for create, cards only |
| 600-960px | Two column cards, sidebar filters |
| > 960px | Table view option, inline filters |

---

## 8. Error Handling

| Scenario | User Feedback |
|----------|---------------|
| Network error | Retry button with error message |
| Validation error | Inline field errors |
| Publish failed | Error dialog with details |
| Not found | 404 page with return link |
| Unauthorized | Redirect to login |

---

*End of Campaign Management Frontend Specifications*
