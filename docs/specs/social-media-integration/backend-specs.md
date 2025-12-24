# Social Media Integration - Backend Specifications

**Feature**: Social Media Integration
**Phase**: 3 (Enhanced Features)
**Document Version**: 1.0
**Last Updated**: 2025-12-24

---

## 1. Overview

Social Media Integration enables campaigns to leverage social platforms for entry methods, sharing, and engagement tracking.

---

## 2. Requirements

### 2.1 Social Account Connection

#### REQ-SM-BE-001: Social Account Connection
**Statement**: The system SHALL allow connecting social media accounts.

**Phase**: 3

**Acceptance Criteria**:
- AC1: OAuth integration with major platforms
- AC2: FacebookAccountConnected, InstagramAccountConnected, etc. events
- AC3: Token storage and refresh
- AC4: SocialAccountDisconnected event on removal

---

#### REQ-SM-BE-002: Supported Platforms
**Statement**: The system SHALL support major social platforms.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Facebook integration
- AC2: Instagram integration
- AC3: Twitter/X integration
- AC4: LinkedIn integration (Phase 4)
- AC5: TikTok integration (Phase 5)

---

### 2.2 Social Entry Methods

#### REQ-SM-BE-003: Social Entry Actions
**Statement**: The system SHALL support social actions as entry methods.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Like/follow verification
- AC2: Comment tracking
- AC3: Share/retweet verification
- AC4: Hashtag monitoring
- AC5: Events: FacebookLikeEntryRecorded, InstagramFollowEntryRecorded, etc.

---

#### REQ-SM-BE-004: Social Entry Verification
**Statement**: The system SHALL verify social entry completion.

**Phase**: 3

**Acceptance Criteria**:
- AC1: API verification where available
- AC2: Manual verification option
- AC3: Verification status tracking
- AC4: Entry credited on verification

---

### 2.3 Social Sharing

#### REQ-SM-BE-005: Campaign Sharing Tracking
**Statement**: The system SHALL track campaign shares.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Share events per platform
- AC2: CampaignSharedOnFacebook, etc. events
- AC3: ShareCountIncremented tracking
- AC4: ViralShareTriggered for multi-level shares

---

#### REQ-SM-BE-006: Share Incentives
**Statement**: The system SHALL support share incentives.

**Phase**: 3

**Acceptance Criteria**:
- AC1: Bonus entries for sharing
- AC2: ShareIncentiveAwarded event
- AC3: Configurable entry value per platform
- AC4: Max shares per participant

---

### 2.4 Comment Picker

#### REQ-SM-BE-007: Instagram Comment Picker
**Statement**: The system SHALL support picking winners from Instagram comments.

**Phase**: 3

**Acceptance Criteria**:
- AC1: InstagramCommentPickerInitiated event
- AC2: InstagramCommentsRetrieved for post
- AC3: InstagramCommentValidated against rules
- AC4: InstagramCommentWinnerSelected for pick

---

#### REQ-SM-BE-008: Facebook Comment Picker
**Statement**: The system SHALL support picking winners from Facebook comments.

**Phase**: 3

**Acceptance Criteria**:
- AC1: FacebookCommentPickerInitiated event
- AC2: FacebookCommentsRetrieved for post
- AC3: FacebookCommentValidated against rules
- AC4: FacebookCommentWinnerSelected for pick

---

---

## 3. Domain Model

```
Aggregate: SocialIntegrationAggregate
Location: MarketingPlatform.Core/Model/SocialIntegrationAggregate/

Entities:
- SocialConnection
- SocialEntry
- SocialShare
- CommentEntry

Enums:
- SocialPlatform (Facebook, Instagram, Twitter, LinkedIn, TikTok)
- SocialActionType (Like, Follow, Share, Comment, Hashtag)
```

---

## 4. API Endpoints

| Method | Endpoint | Description | Phase |
|--------|----------|-------------|-------|
| GET | /api/social/connect/:platform | OAuth init | 3 |
| POST | /api/social/callback/:platform | OAuth callback | 3 |
| DELETE | /api/social/connections/:id | Disconnect | 3 |
| GET | /api/social/connections | List connections | 3 |
| POST | /api/campaigns/:id/social-entries | Verify entry | 3 |
| POST | /api/campaigns/:id/shares | Track share | 3 |
| POST | /api/comment-picker/instagram | Pick IG winner | 3 |
| POST | /api/comment-picker/facebook | Pick FB winner | 3 |

---

## 5. Domain Events

| Event | Trigger | Phase |
|-------|---------|-------|
| FacebookAccountConnected | FB OAuth | 3 |
| InstagramAccountConnected | IG OAuth | 3 |
| TwitterAccountConnected | Twitter OAuth | 3 |
| SocialAccountDisconnected | Disconnect | 3 |
| FacebookLikeEntryRecorded | FB like entry | 3 |
| InstagramFollowEntryRecorded | IG follow | 3 |
| TwitterRetweetEntryRecorded | Retweet | 3 |
| CampaignSharedOnFacebook | FB share | 3 |
| CampaignSharedOnTwitter | Twitter share | 3 |
| ShareCountIncremented | Share counted | 3 |
| ShareIncentiveAwarded | Bonus for share | 3 |
| InstagramCommentPickerInitiated | Start IG pick | 3 |
| InstagramCommentWinnerSelected | IG winner | 3 |
| FacebookCommentWinnerSelected | FB winner | 3 |

---

*End of Social Media Integration Backend Specifications*
