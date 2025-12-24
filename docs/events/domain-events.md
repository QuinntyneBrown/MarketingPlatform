# Marketing Platform - Domain Events

## Document Information
- **Platform**: Marketing Platform
- **Date**: December 24, 2025
- **Purpose**: Comprehensive domain event catalog for domain-driven design

---

## 1. Campaign Management

### Campaign Lifecycle Events
- `CampaignCreated`
- `CampaignDrafted`
- `CampaignPublished`
- `CampaignPaused`
- `CampaignResumed`
- `CampaignCompleted`
- `CampaignArchived`
- `CampaignDeleted`
- `CampaignCloned`
- `CampaignTemplateSelected`
- `CampaignTypeChanged`

### Campaign Configuration Events
- `CampaignNameUpdated`
- `CampaignDescriptionUpdated`
- `CampaignBrandingApplied`
- `CampaignLogoUploaded`
- `CampaignColorSchemeUpdated`
- `CampaignFontsCustomized`
- `CampaignLayoutModified`
- `CampaignCustomCSSApplied`
- `CampaignCustomHTMLApplied`
- `CampaignCustomJavaScriptApplied`

### Campaign Duration Events
- `CampaignStartDateSet`
- `CampaignEndDateSet`
- `CampaignDurationExtended`
- `CampaignScheduled`
- `CampaignAutoStarted`
- `CampaignAutoEnded`

### Campaign Channel Events
- `CampaignEmbeddedOnWebsite`
- `CampaignEmbeddedOnBlog`
- `CampaignSharedOnSocialMedia`
- `CampaignPopupConfigured`
- `CampaignLandingPageCreated`
- `CampaignMobileOptimizationEnabled`
- `CampaignDedicatedURLGenerated`

---

## 2. Giveaway & Contest Features

### Giveaway Lifecycle Events
- `GiveawayCreated`
- `GiveawayLaunched`
- `GiveawayEnded`
- `GiveawayExtended`
- `GiveawayCancelled`

### Entry Management Events
- `EntrySubmitted`
- `EntryValidated`
- `EntryRejected`
- `EntryApproved`
- `EntryFlagged`
- `EntryDuplicated`
- `EntryDeleted`
- `BonusEntryAwarded`
- `MultipleEntriesRecorded`
- `EntryMethodCompleted`
- `EntryLimitReached`

### Winner Selection Events
- `WinnerPickerInitiated`
- `RandomWinnerSelected`
- `ManualWinnerSelected`
- `MultipleWinnersSelected`
- `WinnerNotified`
- `WinnerConfirmed`
- `WinnerDeclined`
- `AlternateWinnerSelected`
- `WinnerListPublished`
- `WinnerAnnouncementScheduled`

### Prize Management Events
- `PrizeConfigured`
- `PrizeValueSet`
- `PrizeDescriptionUpdated`
- `PrizeImageUploaded`
- `PrizeAwarded`
- `PrizeShipped`
- `PrizeDelivered`

### Fraud Detection Events
- `FraudAttemptDetected`
- `RecaptchaVerificationPassed`
- `RecaptchaVerificationFailed`
- `SuspiciousActivityFlagged`
- `DuplicateIPDetected`
- `BotActivityIdentified`
- `EntryDisqualified`

---

## 3. User Generated Content (UGC)

### Photo/Video Contest Events
- `PhotoContestCreated`
- `VideoContestCreated`
- `MediaSubmitted`
- `MediaUploaded`
- `MediaProcessed`
- `MediaRejected`
- `MediaApproved`
- `MediaModerated`
- `MediaFeatured`
- `MediaRemoved`

### Hashtag Contest Events
- `HashtagContestCreated`
- `HashtagMonitoringStarted`
- `HashtagEntryCaptured`
- `HashtagEntryValidated`
- `HashtagAutoEntriesEnabled`
- `HashtagFilterApplied`
- `HashtagBlacklistUpdated`

### Voting Events
- `VotingEnabled`
- `VoteSubmitted`
- `VoteCounted`
- `VoteRetracted`
- `VotingClosed`
- `VoteLeaderboardUpdated`
- `TieDetected`
- `VotingResultsPublished`

### Gallery Events
- `GalleryCreated`
- `MediaAddedToGallery`
- `MediaRemovedFromGallery`
- `GalleryPublished`
- `GalleryOrganized`
- `GalleryFilterApplied`

---

## 4. Polls & Surveys

### Poll Lifecycle Events
- `PollCreated`
- `PollPublished`
- `PollClosed`
- `PollResultsRevealed`
- `PollResultsHidden`
- `PollDeleted`

### Poll Configuration Events
- `PollQuestionSet`
- `PollOptionAdded`
- `PollOptionRemoved`
- `PollOptionUpdated`
- `MultipleChoiceEnabled`
- `SingleChoiceEnabled`
- `PollVisualizationConfigured`

### Poll Response Events
- `PollResponseSubmitted`
- `PollResponseRecorded`
- `PollVoteChanged`
- `ResponseLimitReached`
- `DuplicateResponsePrevented`

---

## 5. Quiz Features

### Trivia Quiz Events
- `TriviaQuizCreated`
- `TriviaQuestionAdded`
- `TriviaQuestionRemoved`
- `TriviaQuestionUpdated`
- `CorrectAnswerSet`
- `WrongAnswerAdded`
- `QuizScoreCalculated`
- `QuizCompleted`
- `QuizResultShared`
- `LeaderboardEntryAdded`

### Personality Quiz Events
- `PersonalityQuizCreated`
- `PersonalityQuestionAdded`
- `PersonalityOutcomeConfigured`
- `OutcomeWeightSet`
- `PersonalityResultCalculated`
- `PersonalityResultRevealed`
- `ResultImageSet`
- `ResultDescriptionSet`

### Quiz Engagement Events
- `QuizStarted`
- `QuizAnswerSubmitted`
- `QuizAnswerValidated`
- `QuizProgressSaved`
- `QuizAbandoned`
- `QuizRetaken`
- `QuizTimerStarted`
- `QuizTimerExpired`

---

## 6. Coupon Management

### Coupon Lifecycle Events
- `CouponCampaignCreated`
- `CouponGenerated`
- `CouponActivated`
- `CouponDeactivated`
- `CouponExpired`
- `CouponDeleted`

### Coupon Distribution Events
- `CouponIssued`
- `CouponRedeemed`
- `CouponEmailed`
- `PrintableCouponGenerated`
- `DigitalCouponCreated`
- `UniqueCouponCodeGenerated`
- `OnePerPersonCouponEnforced`

### Coupon Configuration Events
- `CouponValueSet`
- `CouponExpirationDateSet`
- `CouponRedemptionLimitSet`
- `CouponTermsUpdated`
- `CouponBarcodeGenerated`
- `CouponQRCodeGenerated`

### Coupon Tracking Events
- `CouponViewed`
- `CouponDownloaded`
- `CouponPrinted`
- `CouponShared`
- `CouponRedemptionAttempted`
- `CouponRedemptionValidated`
- `CouponRedemptionRejected`

---

## 7. Instant Win

### Instant Win Configuration Events
- `InstantWinCreated`
- `InstantWinPrizePoolConfigured`
- `WinningOddsSet`
- `PrizeDistributionScheduled`
- `DailyWinLimitSet`
- `TotalPrizesAllocated`

### Instant Win Play Events
- `InstantWinAttempted`
- `InstantWinPlayed`
- `PrizeWonInstantly`
- `NonWinningAttemptRecorded`
- `WinningMomentTriggered`
- `PrizeInventoryUpdated`

### Instant Win Prize Events
- `InstantWinPrizeAwarded`
- `AutomatedEmailSent`
- `WinnerDataCollected`
- `PrizeClaimInitiated`
- `PrizeClaimCompleted`
- `PrizeAllocationDepleted`

---

## 8. Forms & Data Collection

### Form Builder Events
- `CustomFormCreated`
- `FormFieldAdded`
- `FormFieldRemoved`
- `FormFieldReordered`
- `FormFieldConfigured`
- `FormValidationRuleAdded`
- `ConditionalLogicApplied`
- `FormLayoutUpdated`

### Form Field Events
- `TextFieldAdded`
- `EmailFieldAdded`
- `PhoneFieldAdded`
- `DateFieldAdded`
- `DropdownFieldAdded`
- `CheckboxFieldAdded`
- `RadioButtonFieldAdded`
- `FileUploadFieldAdded`
- `AddressFieldAdded`
- `CustomFieldCreated`

### Form Submission Events
- `FormSubmitted`
- `FormValidationPassed`
- `FormValidationFailed`
- `RequiredFieldMissing`
- `InvalidEmailFormat`
- `InvalidPhoneFormat`
- `SubmissionSaved`
- `SubmissionExported`

---

## 9. Participant Management

### Participant Lifecycle Events
- `ParticipantRegistered`
- `ParticipantProfileCreated`
- `ParticipantDataUpdated`
- `ParticipantVerified`
- `ParticipantUnsubscribed`
- `ParticipantRemoved`
- `ParticipantBanned`

### Participant Engagement Events
- `ParticipantLoggedIn`
- `ParticipantActivityRecorded`
- `ParticipantReturnVisit`
- `ParticipantShareCompleted`
- `ParticipantReferralMade`
- `ReferralCredited`

### Participant Data Events
- `EmailCollected`
- `PhoneNumberCollected`
- `DemographicDataCollected`
- `PreferencesCaptured`
- `ConsentRecorded`
- `OptInConfirmed`
- `OptOutProcessed`

---

## 10. Social Media Integration

### Social Connection Events
- `FacebookAccountConnected`
- `InstagramAccountConnected`
- `TwitterAccountConnected`
- `LinkedInAccountConnected`
- `PinterestAccountConnected`
- `YouTubeAccountConnected`
- `TikTokAccountConnected`
- `SocialAccountDisconnected`

### Social Sharing Events
- `CampaignSharedOnFacebook`
- `CampaignSharedOnInstagram`
- `CampaignSharedOnTwitter`
- `CampaignSharedOnLinkedIn`
- `ViralShareTriggered`
- `ShareIncentiveAwarded`
- `ShareCountIncremented`

### Social Entry Methods Events
- `FacebookLikeEntryRecorded`
- `FacebookCommentEntryRecorded`
- `InstagramFollowEntryRecorded`
- `InstagramCommentEntryRecorded`
- `TwitterFollowEntryRecorded`
- `TwitterRetweetEntryRecorded`
- `TwitterHashtagEntryRecorded`

### Instagram Comment Picker Events
- `InstagramCommentPickerInitiated`
- `InstagramCommentsRetrieved`
- `InstagramCommentValidated`
- `InstagramCommentWinnerSelected`

### Facebook Comment Picker Events
- `FacebookCommentPickerInitiated`
- `FacebookCommentsRetrieved`
- `FacebookCommentValidated`
- `FacebookCommentWinnerSelected`

---

## 11. Bracket Tournaments

### Bracket Configuration Events
- `BracketCreated`
- `BracketTypeSelected`
- `BracketSeeded`
- `ParticipantsAdded`
- `MatchupsGenerated`
- `BracketPublished`

### Bracket Progression Events
- `RoundStarted`
- `MatchStarted`
- `VotingOpenedForMatch`
- `VotingClosedForMatch`
- `MatchWinnerDetermined`
- `ParticipantAdvanced`
- `ParticipantEliminated`
- `RoundCompleted`
- `BracketWinnerDeclared`

### Bracket Voting Events
- `BracketVoteSubmitted`
- `BracketPredictionMade`
- `BracketUpsetOccurred`
- `LeaderboardUpdated`

---

## 12. Code Giveaway

### Code Distribution Events
- `CodeGiveawayCreated`
- `CodeListUploaded`
- `CodePoolConfigured`
- `UniqueCodeGenerated`
- `CodeAssigned`
- `CodeDelivered`
- `CodeRevealed`

### Code Redemption Events
- `CodeRedeemed`
- `CodeValidated`
- `CodeExpired`
- `InvalidCodeAttempted`
- `CodeInventoryDepleted`
- `CodeReplenished`

---

## 13. Analytics & Reporting

### Analytics Events
- `CampaignViewRecorded`
- `PageViewTracked`
- `UniqueVisitorCounted`
- `ParticipationRateCalculated`
- `ConversionTracked`
- `EngagementMetricUpdated`
- `TrafficSourceIdentified`

### Performance Events
- `CampaignPerformanceCalculated`
- `EntryTrendAnalyzed`
- `SocialReachMeasured`
- `ViralityScoreCalculated`
- `ROICalculated`
- `BenchmarkComparisonGenerated`

### Reporting Events
- `ReportGenerated`
- `ReportExported`
- `ReportScheduled`
- `ReportDelivered`
- `DashboardUpdated`
- `RealTimeDataRefreshed`
- `CustomReportCreated`

---

## 14. Email Marketing Integration

### Email Collection Events
- `EmailListCreated`
- `EmailCaptured`
- `EmailValidated`
- `EmailDuplicate Detected`
- `EmailAddedToList`
- `EmailListExported`

### Email Campaign Events
- `AutomatedEmailTriggered`
- `WelcomeEmailSent`
- `ConfirmationEmailSent`
- `WinnerNotificationEmailSent`
- `ReminderEmailSent`
- `FollowUpEmailSent`
- `CouponDeliveryEmailSent`

### Email Integration Events
- `MailchimpIntegrationConnected`
- `MailchimpListSynced`
- `EmailServiceProviderConnected`
- `EmailSyncCompleted`
- `EmailExportTriggered`

---

## 15. Third-Party Integrations

### Integration Connection Events
- `ZapierIntegrationConnected`
- `WordPressPluginInstalled`
- `CRMIntegrationConnected`
- `GoogleAnalyticsConnected`
- `FacebookPixelInstalled`
- `WebhookConfigured`
- `APIKeyGenerated`

### Data Sync Events
- `DataSyncInitiated`
- `DataSyncCompleted`
- `DataSyncFailed`
- `ContactsSynced`
- `LeadsPushedToCRM`
- `WebhookTriggered`
- `APIRequestReceived`

### Integration Events
- `ConstantContactSyncCompleted`
- `HubSpotContactCreated`
- `SalesforceLeadCreated`
- `GoogleSheetUpdated`
- `SlackNotificationSent`

---

## 16. Team & Business Management

### Team Management Events
- `TeamMemberInvited`
- `TeamMemberAdded`
- `TeamMemberRemoved`
- `TeamRoleAssigned`
- `TeamRoleUpdated`
- `TeamPermissionsModified`
- `TeamMemberLimitReached`

### Business Account Events
- `BusinessCreated`
- `BusinessPageAdded`
- `BusinessPageRemoved`
- `MultipleBusinessesManaged`
- `BusinessSwitched`
- `BusinessSettingsUpdated`

### Collaboration Events
- `CampaignSharedWithTeam`
- `CampaignEditPermissionGranted`
- `CampaignCommentAdded`
- `TeamNotificationSent`
- `CollaborationActivityLogged`

---

## 17. Subscription & Billing

### Subscription Events
- `FreeTrialStarted`
- `SubscriptionCreated`
- `SubscriptionUpgraded`
- `SubscriptionDowngraded`
- `SubscriptionRenewed`
- `SubscriptionCancelled`
- `SubscriptionReactivated`
- `SubscriptionExpired`

### Billing Events
- `PaymentProcessed`
- `PaymentFailed`
- `InvoiceGenerated`
- `InvoicePaid`
- `RefundIssued`
- `CreditCardUpdated`
- `BillingCycleChanged`

### Plan Events
- `PlanChanged`
- `ParticipantLimitReached`
- `FeatureUnlocked`
- `FeatureLocked`
- `AnnualBillingSelected`
- `MonthlyBillingSelected`

---

## 18. Branding & Customization

### White-Label Events
- `PlatformBrandingRemoved`
- `CustomBrandingApplied`
- `CustomDomainConnected`
- `CustomDomainVerified`
- `CustomLogoUploaded`
- `BrandColorPaletteSet`

### Theme Events
- `ThemeSelected`
- `ThemeCustomized`
- `CustomCSSApplied`
- `CustomHTMLInjected`
- `ResponsiveDesignAdjusted`
- `MobileViewOptimized`

---

## 19. Targeting & Personalization

### Audience Targeting Events
- `TargetAudienceConfigured`
- `GeographicTargetingSet`
- `DemographicFilterApplied`
- `BehavioralTargetingEnabled`
- `VisitorSegmentCreated`

### Personalization Events
- `PersonalizedContentDisplayed`
- `DynamicContentLoaded`
- `UserPreferenceApplied`
- `LanguagePreferenceSet`
- `LocalizationApplied`

### A/B Testing Events
- `ABTestCreated`
- `VariantCreated`
- `TrafficSplitConfigured`
- `VariantShown`
- `VariantPerformanceTracked`
- `WinningVariantDetermined`

---

## 20. Compliance & Security

### Privacy Events
- `PrivacyPolicyAccepted`
- `TermsOfServiceAccepted`
- `CookieConsentRecorded`
- `DataDeletionRequested`
- `DataExportRequested`
- `GDPRComplianceVerified`

### Security Events
- `LoginAttempted`
- `LoginSuccessful`
- `LoginFailed`
- `PasswordResetRequested`
- `PasswordChanged`
- `TwoFactorAuthEnabled`
- `SuspiciousActivityDetected`
- `AccountLocked`
- `SecurityAuditLogged`

### Moderation Events
- `ContentReported`
- `ContentReviewed`
- `ContentApproved`
- `ContentRejected`
- `ContentFlagged`
- `ModerationQueueUpdated`
- `AutoModerationTriggered`

---

## 21. Popup Management

### Popup Configuration Events
- `PopupCreated`
- `PopupTriggerSet`
- `PopupDelayConfigured`
- `PopupFrequencySet`
- `ExitIntentConfigured`
- `PopupPositionSet`

### Popup Display Events
- `PopupDisplayed`
- `PopupViewed`
- `PopupClicked`
- `PopupDismissed`
- `PopupConverted`
- `PopupClosed`

### Popup Optimization Events
- `PopupTestVariantCreated`
- `PopupPerformanceAnalyzed`
- `PopupOptimizationApplied`

---

## 22. Landing Page Features

### Landing Page Events
- `LandingPageCreated`
- `LandingPagePublished`
- `LandingPageUnpublished`
- `LandingPageURLGenerated`
- `LandingPageTemplateApplied`
- `LandingPageSEOConfigured`
- `LandingPageMetatagsSet`

### Landing Page Engagement Events
- `LandingPageVisited`
- `LandingPageBounceRecorded`
- `LandingPageConversion`
- `LandingPageFormSubmitted`
- `LandingPageShareClicked`

---

## 23. Leaderboard Features

### Leaderboard Events
- `LeaderboardCreated`
- `LeaderboardEntryAdded`
- `LeaderboardRankCalculated`
- `LeaderboardUpdated`
- `LeaderboardReset`
- `LeaderboardPublished`
- `LeaderboardPrizeAwarded`

### Leaderboard Display Events
- `TopEntriesDisplayed`
- `UserRankDisplayed`
- `LeaderboardFiltered`
- `LeaderboardSorted`
- `RealTimeUpdateEnabled`

---

## Event Naming Conventions

All domain events follow these patterns:
- **Past tense**: Events represent things that have already happened
- **Noun + Verb (Past)**: e.g., `CampaignCreated`, `EntrySubmitted`
- **Business language**: Uses terms familiar to marketing domain experts
- **Granular**: Specific enough to be actionable and traceable
- **Immutable**: Events are facts that cannot be changed

---

## Event Metadata (Common Across All Events)

Each event typically includes:
- `EventId`: Unique identifier for the event
- `EventType`: The name of the event
- `AggregateId`: ID of the entity the event belongs to
- `AggregateType`: Type of the aggregate (Campaign, Entry, etc.)
- `Timestamp`: When the event occurred
- `UserId`: Who triggered the event (if applicable)
- `BusinessId`: Which business/account owns the entity
- `Version`: Event schema version
- `Metadata`: Additional contextual information
- `CorrelationId`: For tracking related events
- `CausationId`: What caused this event

---

## Integration Points

These domain events can be consumed by:
- **Analytics Systems**: For reporting and insights
- **Email Marketing Tools**: Mailchimp, Constant Contact, etc.
- **CRM Systems**: Salesforce, HubSpot, etc.
- **Webhook Endpoints**: For custom integrations
- **Zapier**: For workflow automation
- **Event Streaming Platforms**: Kafka, EventBridge, etc.
- **Data Warehouses**: For historical analysis
- **Notification Services**: Slack, SMS, etc.

---

## Total Event Count

**Total Domain Events Documented**: 450+

**Categories**: 23 major feature categories

---

## Notes for Implementation

1. **Event Sourcing**: This catalog supports event sourcing architecture where state is derived from events
2. **CQRS**: Events facilitate Command Query Responsibility Segregation patterns
3. **Audit Trail**: Every event provides complete audit capability
4. **Analytics**: Events enable real-time and historical analytics
5. **Integration**: Events serve as integration points with external systems
6. **Replay**: Events can be replayed for debugging or state reconstruction
7. **Microservices**: Events enable decoupled microservice communication

---

*This document represents a comprehensive domain event catalog for the marketing platform as of December 2025.*
