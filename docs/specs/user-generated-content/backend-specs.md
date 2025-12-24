# User Generated Content (UGC) - Backend Specifications

**Feature**: User Generated Content
**Phase**: 4 (Advanced Features)
**Document Version**: 1.0
**Last Updated**: 2025-12-24

---

## 1. Overview

User Generated Content enables photo/video contests where participants submit media for voting and judging.

---

## 2. Requirements

### 2.1 Contest Creation

#### REQ-UGC-BE-001: Photo Contest Creation
**Statement**: The system SHALL support photo contest creation.

**Phase**: 4

**Acceptance Criteria**:
- AC1: PhotoContestCreated event published
- AC2: Submission guidelines configurable
- AC3: File type restrictions (jpg, png)
- AC4: Max file size configurable

---

#### REQ-UGC-BE-002: Video Contest Creation
**Statement**: The system SHALL support video contest creation.

**Phase**: 4

**Acceptance Criteria**:
- AC1: VideoContestCreated event published
- AC2: Video format restrictions (mp4, webm)
- AC3: Duration limits configurable
- AC4: Max file size configurable

---

### 2.2 Media Submission

#### REQ-UGC-BE-003: Media Upload
**Statement**: The system SHALL process media uploads.

**Phase**: 4

**Acceptance Criteria**:
- AC1: MediaSubmitted event on upload
- AC2: MediaUploaded for storage
- AC3: MediaProcessed for optimization
- AC4: Thumbnail generation
- AC5: Virus scanning

---

#### REQ-UGC-BE-004: Media Moderation
**Statement**: The system SHALL support media moderation.

**Phase**: 4

**Acceptance Criteria**:
- AC1: MediaModerated event on review
- AC2: MediaApproved for approved content
- AC3: MediaRejected for violations
- AC4: Moderation queue
- AC5: Auto-moderation (AI-based)

---

### 2.3 Hashtag Contests

#### REQ-UGC-BE-005: Hashtag Monitoring
**Statement**: The system SHALL monitor hashtags for entries.

**Phase**: 4

**Acceptance Criteria**:
- AC1: HashtagContestCreated event
- AC2: HashtagMonitoringStarted on launch
- AC3: HashtagEntryCaptured per post
- AC4: HashtagFilterApplied for rules
- AC5: HashtagBlacklistUpdated for exclusions

---

### 2.4 Voting

#### REQ-UGC-BE-006: Voting System
**Statement**: The system SHALL support public voting.

**Phase**: 4

**Acceptance Criteria**:
- AC1: VotingEnabled event on start
- AC2: VoteSubmitted per vote
- AC3: VoteCounted for totals
- AC4: VotingClosed event on end
- AC5: VotingResultsPublished for winners

---

#### REQ-UGC-BE-007: Vote Management
**Statement**: The system SHALL manage vote integrity.

**Phase**: 4

**Acceptance Criteria**:
- AC1: Duplicate vote prevention
- AC2: VoteRetracted for removals
- AC3: Vote limits per participant
- AC4: TieDetected event for ties

---

### 2.5 Gallery

#### REQ-UGC-BE-008: Gallery Management
**Statement**: The system SHALL support media galleries.

**Phase**: 4

**Acceptance Criteria**:
- AC1: GalleryCreated event
- AC2: MediaAddedToGallery for curation
- AC3: GalleryPublished for display
- AC4: GalleryFilterApplied for views

---

---

## 3. Domain Model

```
Aggregate: UGCAggregate
Location: MarketingPlatform.Core/Model/UGCAggregate/

Entities:
- ContentContest (Aggregate Root)
- MediaSubmission
- Vote
- Gallery
- GalleryItem

Enums:
- ContestType (Photo, Video, Hashtag)
- MediaStatus (Pending, Approved, Rejected)
- ModerationStatus (Pending, Approved, Rejected, Flagged)
```

---

## 4. API Endpoints

| Method | Endpoint | Description | Phase |
|--------|----------|-------------|-------|
| POST | /api/ugc-contests | Create contest | 4 |
| GET | /api/ugc-contests/{id} | Get contest | 4 |
| POST | /api/ugc-contests/{id}/submissions | Upload media | 4 |
| GET | /api/ugc-contests/{id}/submissions | List submissions | 4 |
| PUT | /api/ugc-contests/{id}/submissions/{sid}/moderate | Moderate | 4 |
| POST | /api/ugc-contests/{id}/votes | Submit vote | 4 |
| GET | /api/ugc-contests/{id}/results | Get results | 4 |
| POST | /api/ugc-contests/{id}/galleries | Create gallery | 4 |
| GET | /api/ugc-contests/{id}/galleries/{gid} | Get gallery | 4 |

---

## 5. Domain Events

| Event | Trigger | Phase |
|-------|---------|-------|
| PhotoContestCreated | Photo contest creation | 4 |
| VideoContestCreated | Video contest creation | 4 |
| HashtagContestCreated | Hashtag contest | 4 |
| MediaSubmitted | Upload started | 4 |
| MediaUploaded | Upload complete | 4 |
| MediaProcessed | Processing done | 4 |
| MediaApproved | Moderation approved | 4 |
| MediaRejected | Moderation rejected | 4 |
| MediaFeatured | Featured selection | 4 |
| VotingEnabled | Voting started | 4 |
| VoteSubmitted | Vote cast | 4 |
| VotingClosed | Voting ended | 4 |
| VotingResultsPublished | Results revealed | 4 |
| GalleryCreated | Gallery created | 4 |
| GalleryPublished | Gallery published | 4 |

---

*End of User Generated Content Backend Specifications*
