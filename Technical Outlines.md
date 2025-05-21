Technical Outlines (Based on PRD)

I. Database Schema (MS SQL - complyarkDB)
1. Industry Table:
IndustryID (PK, INT, IDENTITY)
IndustryName (NVARCHAR(255), NOT NULL, UNIQUE)
IsActive (BIT, DEFAULT 1)
CreatedAt (DATETIME, DEFAULT GETDATE())
UpdatedAt (DATETIME, DEFAULT GETDATE())
PRD Link: REQ-ADM-015 to 018
2. Organisation Table:
OrganisationID (PK, INT, IDENTITY)
BusinessName (NVARCHAR(255), NOT NULL)
BusinessAddress (NVARCHAR(MAX), NOT NULL)
IndustryID (FK, INT, NOT NULL, REFERENCES Industry)
ContactPersonName (NVARCHAR(255), NOT NULL)
ContactEmailAddress (NVARCHAR(255), NOT NULL)
ContactPhoneNumber (NVARCHAR(50), NOT NULL)
NoOfUsers (INT, NOT NULL)
Remarks (NVARCHAR(MAX), NULL)
RequestPageURL (NVARCHAR(MAX), NULL) - Stores the unique URL (e.g., with UUID)
IsActive (BIT, DEFAULT 1)
CreatedAt (DATETIME, DEFAULT GETDATE())
UpdatedAt (DATETIME, DEFAULT GETDATE())
PRD Link: REQ-ADM-004 to 010
3. Users Table:
UserID (PK, INT, IDENTITY)
FirstName (NVARCHAR(100), NOT NULL)
LastName (NVARCHAR(100), NOT NULL)
Email (NVARCHAR(255), NOT NULL, UNIQUE)
PhoneNumber (NVARCHAR(50), NULL)
PasswordHash (NVARCHAR(MAX), NOT NULL)
Role (NVARCHAR(50), NOT NULL, CHECK IN ('SystemAdmin', 'OrgAdmin', 'OrgUser'))
OrganisationID (FK, INT, NULL, REFERENCES Organisation) - NULL for SystemAdmin
IsActive (BIT, DEFAULT 1)
CanEdit (BIT, DEFAULT 0) - Permission flag for OrgUser, managed by OrgAdmin
CanDelete (BIT, DEFAULT 0) - Permission flag for OrgUser, managed by OrgAdmin
LastLoginAt (DATETIME, NULL) - For tracking, desirable
PasswordResetToken (NVARCHAR(255), NULL) - For forgot password flow
PasswordResetExpires (DATETIME, NULL) - For forgot password flow
CreatedAt (DATETIME, DEFAULT GETDATE())
UpdatedAt (DATETIME, DEFAULT GETDATE())
PRD Link: REQ-ADM-002, REQ-ADM-006, REQ-ADM-011 to 014, REQ-APP-001 to 005, REQ-APP-012 to 018
4. Template Table (Notice Templates):
TemplateID (PK, INT, IDENTITY)
TemplateName (NVARCHAR(255), NOT NULL)
TemplateBody (NVARCHAR(MAX), NULL) - Text content of the template
IndustryID (FK, INT, NOT NULL, REFERENCES Industry)
TemplatePath (NVARCHAR(MAX), NULL) - Path to uploaded PDF/DOCX in TemplateRepo/
IsActive (BIT, DEFAULT 1)
CreatedAt (DATETIME, DEFAULT GETDATE())
UpdatedAt (DATETIME, DEFAULT GETDATE())
PRD Link: REQ-ADM-019 to 022, REQ-APP-062
5. RequestStatus Table (For DPR & Grievances):
RequestStatusID (PK, INT, IDENTITY)
RequestStatusName (NVARCHAR(100), NOT NULL, UNIQUE)
SLA_Days (INT, NOT NULL) - SLA associated with this status or for resolution from this status
IsActive (BIT, DEFAULT 1)
CreatedAt (DATETIME, DEFAULT GETDATE())
UpdatedAt (DATETIME, DEFAULT GETDATE())
PRD Link: REQ-ADM-023 to 026
6. Notice Table:
NoticeID (PK, INT, IDENTITY)
OrganisationID (FK, INT, NOT NULL, REFERENCES Organisation)
NoticeName (NVARCHAR(255), NOT NULL) - e.g., "Website Privacy Policy_Org123_V1"
NoticeBody (NVARCHAR(MAX), NOT NULL) - Content from text editor (REQ-APP-069)
NoticeType (NVARCHAR(255), NULL) - Name of selected template or uploaded custom format file
Version (NVARCHAR(10), NOT NULL, DEFAULT 'V1')
FolderLocation (NVARCHAR(MAX), NULL) - Path to generated file in GeneratedNotices/[OrgID]/
PrimaryLanguage (NVARCHAR(20), DEFAULT 'eng_Latn') - Language of this original notice (REQ-APP-067)
QuestionnaireDataSnapshot (NVARCHAR(MAX), NULL) - Snapshot of formatted questionnaire data used for this notice for audit/reference (REQ-APP-065)
CreatedByUserID (FK, INT, NOT NULL, REFERENCES Users)
CreatedAt (DATETIME, DEFAULT GETDATE())
UpdatedAt (DATETIME, DEFAULT GETDATE())
PRD Link: REQ-APP-069, REQ-APP-071
(Translated notices are files in NoticesTranslated/, not separate DB rows for MVP)
7. DPRequests Table:
DPRequestID (PK, INT, IDENTITY)
OrganisationID (FK, INT, NOT NULL, REFERENCES Organisation)
FirstName (NVARCHAR(100), NOT NULL)
LastName (NVARCHAR(100), NOT NULL)
Email (NVARCHAR(255), NOT NULL)
PhoneNumber (NVARCHAR(50), NULL)
RequestType (NVARCHAR(100), NOT NULL) - 'Access', 'CorrectionErasure', 'Nomination'
RequestComment (NVARCHAR(MAX), NOT NULL)
ExternalUserIdentifier (NVARCHAR(255), NULL) - Email used at dummy login on external page
CurrentStatusID (FK, INT, NOT NULL, REFERENCES RequestStatus)
AssignedToUserID (FK, INT, NULL, REFERENCES Users)
ExpectedCompletionDate (DATETIME, NULL)
CompletedOnTime (BIT, NULL)
ClosureComment (NVARCHAR(MAX), NULL)
ClosedAt (DATETIME, NULL)
CreatedAt (DATETIME, DEFAULT GETDATE())
LastUpdatedAt (DATETIME, DEFAULT GETDATE())
PRD Link: REQ-EXT-009, REQ-EXT-012, REQ-APP-076 to 091
8. DPRequestHistory Table:
HistoryID (PK, INT, IDENTITY)
DPRequestID (FK, INT, NOT NULL, REFERENCES DPRequests)
ChangedAt (DATETIME, DEFAULT GETDATE())
ChangedByUserID (FK, INT, NULL, REFERENCES Users) - NULL if system/external initial
OrganisationID (FK, INT, NOT NULL, REFERENCES Organisation)
PreviousStatusID (FK, INT, NULL, REFERENCES RequestStatus)
NewStatusID (FK, INT, NULL, REFERENCES RequestStatus)
PreviousAssignedToUserID (FK, INT, NULL, REFERENCES Users)
NewAssignedToUserID (FK, INT, NULL, REFERENCES Users)
Comment (NVARCHAR(MAX), NOT NULL) - e.g., "Status changed to InProgress", "Assigned to John Doe", "Closure: Case resolved."
PRD Link: REQ-EXT-012, REQ-APP-087 to 090a
9. Grievances Table: (Mirrors DPRequests structure without RequestType)
GrievanceID (PK, INT, IDENTITY)
OrganisationID (FK, INT, NOT NULL, REFERENCES Organisation)
FirstName (NVARCHAR(100), NOT NULL)
LastName (NVARCHAR(100), NOT NULL)
Email (NVARCHAR(255), NOT NULL)
PhoneNumber (NVARCHAR(50), NULL)
GrievanceComment (NVARCHAR(MAX), NOT NULL)
ExternalUserIdentifier (NVARCHAR(255), NULL)
CurrentStatusID (FK, INT, NOT NULL, REFERENCES RequestStatus)
AssignedToUserID (FK, INT, NULL, REFERENCES Users)
ExpectedCompletionDate (DATETIME, NULL)
CompletedOnTime (BIT, NULL)
ClosureComment (NVARCHAR(MAX), NULL)
ClosedAt (DATETIME, NULL)
CreatedAt (DATETIME, DEFAULT GETDATE())
LastUpdatedAt (DATETIME, DEFAULT GETDATE())
PRD Link: REQ-EXT-014, REQ-EXT-016, REQ-APP-092 to 107
10. GrievanceHistory Table: (Mirrors DPRequestHistory)
HistoryID (PK, INT, IDENTITY)
GrievanceID (FK, INT, NOT NULL, REFERENCES Grievances)
ChangedAt (DATETIME, DEFAULT GETDATE())
ChangedByUserID (FK, INT, NULL, REFERENCES Users)
OrganisationID (FK, INT, NOT NULL, REFERENCES Organisation)
PreviousStatusID (FK, INT, NULL, REFERENCES RequestStatus)
NewStatusID (FK, INT, NULL, REFERENCES RequestStatus)
PreviousAssignedToUserID (FK, INT, NULL, REFERENCES Users)
NewAssignedToUserID (FK, INT, NULL, REFERENCES Users)
Comment (NVARCHAR(MAX), NOT NULL)
PRD Link: REQ-EXT-016, REQ-APP-104 to 107a
11. OrganisationDocuments Table (Compliance Documentation Module):
DocumentID (PK, INT, IDENTITY)
OrganisationID (FK, INT, NOT NULL, REFERENCES Organisation)
FileName (NVARCHAR(255), NOT NULL)
FilePath (NVARCHAR(MAX), NOT NULL) - Relative path within OrganisationSpecificDocs/[OrgID]/
FileType (NVARCHAR(100), NULL) - e.g., 'application/pdf', 'text/plain'
FileSize (BIGINT, NULL) - In bytes
Description (NVARCHAR(MAX), NULL)
UploadedByUserID (FK, INT, NOT NULL, REFERENCES Users)
UploadedAt (DATETIME, DEFAULT GETDATE())
LastModifiedAt (DATETIME, DEFAULT GETDATE()) - Can be file system's last modified or db record update
PRD Link: REQ-APP-123 to 142
12. RoPAEntries Table (Record of Processing Activities):
RoPAEntryID (PK, INT, IDENTITY)
OrganisationID (FK, INT, NOT NULL, REFERENCES Organisation)
ProcessingActivityName (NVARCHAR(500), NOT NULL)
ProcessingPurpose (NVARCHAR(MAX), NOT NULL)
CategoriesDataPrincipals (NVARCHAR(MAX), NULL) - Could be JSON array or comma-separated
CategoriesPersonalData (NVARCHAR(MAX), NULL) - Could be JSON array or comma-separated
LawfulBasis (NVARCHAR(MAX), NULL) - e.g., "Consent", "Legitimate Use: Contract Performance"
ChildDisabilityDataDetails (NVARCHAR(MAX), NULL) - Text describing measures
SensitiveDataDetails (NVARCHAR(MAX), NULL)
DataFiduciaryContact (NVARCHAR(MAX), NULL) - Could be prefilled, or specific to activity
DPOContact (NVARCHAR(MAX), NULL)
DataProcessorsInvolved (NVARCHAR(MAX), NULL) - JSON array of objects: {name, contact, service, dpaReference}
ThirdPartyFiduciaries (NVARCHAR(MAX), NULL) - JSON array of objects: {name, dataShared, purpose, lawfulBasis}
CrossBorderTransfers (NVARCHAR(MAX), NULL) - JSON array of objects: {country, dataCategories, safeguards}
DataRetentionPeriod (NVARCHAR(500), NULL)
SecurityMeasuresDescription (NVARCHAR(MAX), NULL)
AlgorithmicDecisionMakingDetails (NVARCHAR(MAX), NULL)
TokenizationDetails (NVARCHAR(MAX), NULL)
CreatedByUserID (FK, INT, NOT NULL, REFERENCES Users)
CreatedAt (DATETIME, DEFAULT GETDATE())
LastUpdatedAt (DATETIME, DEFAULT GETDATE())
PRD Link: REQ-APP-109 to 122
13. GeneralTasks Table (Basic Task Management):
TaskID (PK, INT, IDENTITY)
OrganisationID (FK, INT, NOT NULL, REFERENCES Organisation)
Title (NVARCHAR(500), NOT NULL)
Description (NVARCHAR(MAX), NULL)
AssignedToUserID (FK, INT, NULL, REFERENCES Users)
DueDate (DATETIME, NULL)
Priority (NVARCHAR(50), NULL, CHECK IN ('High', 'Medium', 'Low'))
Status (NVARCHAR(50), NOT NULL, CHECK IN ('ToDo', 'InProgress', 'Completed', 'OnHold'))
ReferenceLink (NVARCHAR(MAX), NULL) - Free text or link to other module items
CreatedByUserID (FK, INT, NOT NULL, REFERENCES Users)
CreatedAt (DATETIME, DEFAULT GETDATE())
UpdatedAt (DATETIME, DEFAULT GETDATE())
PRD Link: REQ-APP-143 to 157

II. Project Structure (React Frontend & Node.js Backend)


ComplyArkWebApp/
├── complyark-frontend/    	# React App (using Material UI)
│   ├── public/
│   ├── src/
│   │   ├── admin/         	# Components for System Admin Page (/admin route)
│   │   │   ├── OrganisationTab.js
│   │   │   ├── UsersTab.js     	# System-wide user management
│   │   │   ├── IndustryTab.js
│   │   │   ├── TemplateTab.js  	# Notice Templates
│   │   │   └── RequestStatusTab.js
│   │   ├── app/           	# Components for Main Application (Org Users - /app route)
│   │   │   ├── auth/      	# Login, ForgotPassword, ResetPassword pages for Org Users
│   │   │   ├── dashboard/ 	# DashboardPage.js, chart components, escalated items tables
│   │   │   ├── users/     	# OrgUsersPage.js (for OrgAdmin to manage their users)
│   │   │   ├── profile/   	# MyProfilePage.js (for OrgUser to view profile, change pwd)
│   │   │   ├── notice/    	# NoticeModulePage.js (parent for tabs)
│   │   │   │   ├── QuestionnaireTab.js
│   │   │   │   ├── NoticePreviewTab.js
│   │   │   │   └── TranslationTab.js
│   │   │   ├── dpr/       	# Data Principal Request Module
│   │   │   │   ├── DPRListingPage.js
│   │   │   │   └── DPRDetailPage.js
│   │   │   ├── grievances/	# Grievance Module
│   │   │   │   ├── GrievanceListingPage.js
│   │   │   │   └── GrievanceDetailPage.js
│   │   │   ├── ropa/      	# Record of Processing Activities Module
│   │   │   │   ├── RoPAListingPage.js
│   │   │   │   ├── RoPAForm.js      	# For Create/Edit RoPA entry
│   │   │   │   └── RoPAView.js      	# For detailed view/visualization
│   │   │   ├── complianceDocs/ # Compliance Documentation Module
│   │   │   │   └── ComplianceDocsPage.js # File explorer interface
│   │   │   └── tasks/     	# Basic Task Management Module
│   │   │   	├── TaskListingPage.js
│   │   │   	└── TaskFormModal.js   # For Create/Edit tasks
│   │   ├── external/      	# Components for CreateRequestPage (publicly accessible)
│   │   │   ├── ExternalLoginPage.js  # Dummy login for external requesters
│   │   │   ├── CreateRequestLandingPage.js
│   │   │   ├── ExternalDPRFormPage.js
│   │   │   └── ExternalGrievanceFormPage.js
│   │   ├── components/    	# Shared/Reusable UI Components
│   │   │   ├── DataTableWrapper.js
│   │   │   ├── ConfirmationDialog.js
│   │   │   ├── FormModalWrapper.js
│   │   │   ├── LoadingSpinner.js
│   │   │   └── SnackbarNotification.js
│   │   ├── services/      	# API call service functions (e.g., authService.js, noticeService.js)
│   │   ├── contexts/      	# React Context (e.g., AuthContext, ThemeContext, OrgContext)
│   │   ├── layouts/       	# MainAppLayout.js, AdminLayout.js, ExternalPageLayout.js
│   │   ├── assets/        	# Images, static files
│   │   ├── theme/         	# Material UI theme configuration (lightTheme.js, darkTheme.js)
│   │   ├── utils/         	# Helper functions (date formatters, validators)
│   │   ├── App.js         	# Main router setup
│   │   ├── index.js
│   │   └── ProtectedRoute.js  # HOC for route protection
│   ├── package.json
│   └── ...
├── complyark-backend/     	# Node.js App (Express.js)
│   ├── src/
│   │   ├── controllers/   	# Request handlers (authController, orgController, noticeController, etc.)
│   │   ├── routes/        	# API route definitions (authRoutes, orgRoutes, noticeRoutes, etc.)
│   │   ├── services/      	# Business logic, database interaction (authService, orgService, etc.)
│   │   ├── middleware/    	# Auth (verifyJWT, checkRoles), errorHandling, validationMiddleware
│   │   ├── config/        	# dbConfig.js, envConfig.js (constants, JWT secret)
│   │   ├── models/        	# (Optional for ORM) If using Sequelize/TypeORM, model definitions here
│   │   ├── utils/         	# Helper functions (passwordUtils, fileUtils, emailUtils (dummy))
│   │   └── server.js      	# Express app initialization and server start
│   ├── package.json
│   └── ...
├── TemplateRepo/          	# Local folder for uploaded Admin Notice Template files
├── GeneratedNotices/      	# Root folder for notices generated by Orgs (contains OrgID subfolders)
├── NoticesTranslated/     	# Root folder for translated notices (contains OrgID subfolders)
├── OrganisationSpecificDocs/  # Root folder for Compliance Docs module (contains OrgID subfolders)
└── README.md

III. Backend API Endpoints (Node.js/Express - Detailed Outline)
Authentication middleware (authSysAdmin, authOrgUser) applied to routes as appropriate. organisationId is often derived from req.user for app routes.
1. Auth Routes (/api/auth)
POST /admin/login: System Admin login (REQ-ADM-002)
POST /login: Organisation User login (REQ-APP-001)
POST /forgot-password: Initiate password reset (REQ-APP-004)
POST /reset-password/:token: Complete password reset (REQ-APP-004)
POST /external/login: Dummy login for external request page (REQ-EXT-004) - may not need a backend call if purely client-side dummy
POST /change-password: Logged-in user changes their own password (REQ-APP-014, M2.4)
2. System Admin Routes (/api/admin) - All require authSysAdmin
Organisations:
POST /organisations: Create Organisation (REQ-ADM-005, includes default OrgAdmin & URL gen)
GET /organisations: List all Organisations (paginated, filter, search) (REQ-ADM-008)
GET /organisations/:id: Get Organisation by ID
PUT /organisations/:id: Update Organisation (REQ-ADM-009)
PUT /organisations/:id/regenerate-url: Regenerate RequestPageURL (REQ-ADM-009a)
DELETE /organisations/:id: Deactivate/Delete Organisation (REQ-ADM-010)
System Users:
POST /users: Create SystemAdmin user (REQ-ADM-012)
GET /users: List SystemAdmin users (or all for overview) (REQ-ADM-013)
GET /users/:id: Get user by ID
PUT /users/:id: Update user (REQ-ADM-014)
DELETE /users/:id: Deactivate/Delete user (REQ-ADM-015)
Industries:
POST /industries: Create Industry (REQ-ADM-017)
GET /industries: List all Industries (REQ-ADM-018) - Also used by main app forms
GET /industries/:id: Get Industry by ID
PUT /industries/:id: Update Industry (REQ-ADM-019)
DELETE /industries/:id: Delete Industry (REQ-ADM-020)
Notice Templates:
POST /templates: Create Template (handles file upload to TemplateRepo) (REQ-ADM-022)
GET /templates: List all Templates (REQ-ADM-023)
GET /templates/:id: Get Template by ID (and serve file info)
GET /templates/:id/download: Download template file
PUT /templates/:id: Update Template (handles file replacement) (REQ-ADM-024)
DELETE /templates/:id: Delete Template (and file) (REQ-ADM-025)
Request Statuses:
POST /request-statuses: Create Request Status (REQ-ADM-027)
GET /request-statuses: List all Request Statuses (REQ-ADM-028) - Also used by main app forms
GET /request-statuses/:id: Get Request Status by ID
PUT /request-statuses/:id: Update Request Status (REQ-ADM-029)
DELETE /request-statuses/:id: Delete Request Status (REQ-ADM-030)
Admin Dashboard:
GET /dashboard/summary: Get system overview stats (REQ-ADM-031)
3. Main Application Routes (/api/app) - All require authOrgUser (or specific role checks)
Dashboard:
GET /dashboard/summary: Get Org-specific dashboard data (REQ-APP-016, REQ-APP-024, REQ-APP-030, REQ-APP-036)
Organisation Users (OrgAdmin only):
POST /users: Create OrgUser within current Org (REQ-APP-042)
GET /users: List users for current Org (REQ-APP-039)
GET /users/:userId: Get specific OrgUser details
PUT /users/:userId: Update OrgUser (REQ-APP-046)
DELETE /users/:userId: Delete/Deactivate OrgUser (REQ-APP-051)
Profile (Current User):
GET /profile/me: Get current logged-in user's profile (REQ-APP-013)
PUT /profile/me/phone: Update current user's phone (if allowed)
Notices:
GET /templates/by-industry: Get notice templates relevant to Org's industry (for Notice Tab 2) (REQ-APP-062)
POST /notices/save-notice: Save/Generate notice (Tab 2 action, saves to DB & file system) (REQ-APP-069)
POST /notices/translate-notice: (Dummy) Translate notice (Tab 3 action) (REQ-APP-073)
GET /notices: List notices for the current Org
GET /notices/:noticeId: Get specific notice details
GET /notices/:noticeId/download-original: Download original generated notice file
GET /notices/download-translated?filePath=...: Download a translated notice file
Data Principal Requests (DPRs):
GET /dpr: List DPRs for Org (with filters, pagination) (REQ-APP-078, REQ-APP-079)
GET /dpr/:dprId: Get DPR details + history (REQ-APP-083, REQ-APP-087)
PUT /dpr/:dprId: Update DPR (status, assignment, closure) (REQ-APP-084)
Grievances:
GET /grievances: List Grievances for Org (with filters, pagination) (REQ-APP-095, REQ-APP-096)
GET /grievances/:grievanceId: Get Grievance details + history (REQ-APP-100, REQ-APP-104)
PUT /grievances/:grievanceId: Update Grievance (REQ-APP-101)
Record of Processing Activities (RoPA):
POST /ropa/activities: Create RoPA entry (REQ-APP-122)
GET /ropa/activities: List RoPA entries for Org (REQ-APP-122)
GET /ropa/activities/:activityId: Get specific RoPA entry (REQ-APP-122)
PUT /ropa/activities/:activityId: Update RoPA entry (REQ-APP-122)
DELETE /ropa/activities/:activityId: Delete RoPA entry (REQ-APP-122)
GET /ropa/export: Export RoPA data (CSV/PDF) (REQ-APP-117)
Compliance Documentation:
GET /documents?path=...: List files/folders in path (REQ-APP-136)
POST /documents/create-folder: Create folder (REQ-APP-125)
POST /documents/upload?path=...: Upload file(s) (REQ-APP-130)
DELETE /documents?itemPath=...&itemType=...: Delete file/folder (REQ-APP-129, REQ-APP-134)
GET /documents/download?filePath=...: Download file (REQ-APP-132)
GET /documents/quicklinks/generated-notices: List generated notices (for quick link) (REQ-APP-140a)
GET /documents/quicklinks/translated-notices: List translated notices (REQ-APP-140b)
GET /documents/quicklinks/templates: List applicable templates (REQ-APP-140c)
Tasks:
POST /tasks: Create a task (REQ-APP-157)
GET /tasks: List tasks for Org (with filters) (REQ-APP-157)
GET /tasks/:taskId: Get specific task details
PUT /tasks/:taskId: Update task (REQ-APP-157)
DELETE /tasks/:taskId: Delete task (REQ-APP-157)
4. External Request Page Routes (/api/external)
GET /organisation-info/:identifier: Get Org name for display on external page (REQ-EXT-003)
POST /dpr/submit: External user submits a DPR (REQ-EXT-011, REQ-EXT-012)
POST /grievances/submit: External user submits a Grievance (REQ-EXT-015, REQ-EXT-016)

IV. Frontend Key Components & Logic Outline (React/Material UI)
This outlines major components and their primary responsibilities/logic.
1. Admin Interface Components (src/admin/)
AdminLayout.js: Wrapper for admin pages; includes header, tab navigation.
OrganisationTab.js: Form for Org CRUD, DataTableWrapper for listing. Logic for API calls, state management for form, edit mode.
UsersTab.js: Form for System User CRUD, DataTableWrapper.
IndustryTab.js: Form for Industry CRUD, DataTableWrapper.
TemplateTab.js: Form for Notice Template CRUD (with file upload input), DataTableWrapper.
RequestStatusTab.js: Form for Request Status CRUD, DataTableWrapper.
2. Main Application Layout & Auth Components (src/layouts/, src/app/auth/)
MainAppLayout.js: Wrapper for authenticated org user pages; header (Org Name, User Menu, Logout), collapsible left navigation Drawer, dark mode toggle.
LoginPage.js (src/app/auth/): Org user login form, handles API call, updates AuthContext.
ForgotPasswordPage.js, ResetPasswordPage.js: Forms and logic for password reset flow.
ProtectedRoute.js (src/): HOC to protect routes based on authentication status and role from AuthContext.
3. Shared/Reusable Components (src/components/)
DataTableWrapper.js: Generic table with sorting, pagination, search, filter slots, edit/delete actions. Uses MUI Table components. Handles delete confirmation via ConfirmationDialog.js.
ConfirmationDialog.js: Reusable MUI Dialog for "Are you sure?" prompts.
FormModalWrapper.js: Reusable MUI Dialog for hosting create/edit forms.
LoadingSpinner.js: Global or local loading indicator.
SnackbarNotification.js: Displays success/error messages using MUI Snackbar.
4. Dashboard (src/app/dashboard/)
DashboardPage.js: Fetches summary data. Renders:
StatusPieChart.js (reusable for DPR & Grievances, takes data and title).
EscalatedItemsTable.js (reusable for DPR & Grievances, takes data, columns, links to detail).
5. Organisation User Management (src/app/users/ - OrgAdmin only)
OrgUsersPage.js: Form for OrgUser CRUD within their org, DataTableWrapper for listing.
6. User Profile (src/app/profile/)
MyProfilePage.js: Displays current user's info, form for password change.
7. Notice Module (src/app/notice/)
NoticeModulePage.js: Main container with MUI Tabs for the 3-tab workflow. Manages shared state between tabs (e.g., questionnaire data, current NoticeID).
QuestionnaireTab.js: Renders accordions for data categories. Manages state of selected fields, reasons, custom fields. Passes data to parent/context.
QuestionnaireCategory.js: Reusable component for each category accordion.
QuestionnaireField.js: Component for each selectable field row.
NoticePreviewTab.js: Dropdowns for templates, file upload for custom format. Text editor (MUI TextField multiline or react-quill). Read-only display of questionnaire data. Preview modal. Save logic.
TranslationTab.js: Displays original notice tile. Language selection checkboxes. "Translate" button logic. Dynamically renders translated notice tiles with download links.
NoticeTile.js: Reusable for displaying original/translated notice info and download buttons.
8. External Request Page (src/external/)
ExternalPageLayout.js: Simple layout for public-facing pages.
ExternalLoginPage.js: Dummy login form.
CreateRequestLandingPage.js: Fetches Org Name. Buttons for DPR/Grievance.
ExternalDPRFormPage.js: Form with DPR fields, validation, submit logic.
ExternalGrievanceFormPage.js: Form with Grievance fields, validation, submit logic.
9. DPR Module (src/app/dpr/)
DPRListingPage.js: Status tiles, filter controls, DataTableWrapper for DPRs. Navigation to detail page.
DPRDetailPage.js: Displays all DPR info. Editable fields (Status, AssignedTo, ClosureComment) based on role. Renders RequestHistoryTrail.js.
RequestHistoryTrail.js: (Reusable for Grievances) Displays history items chronologically.
10. Grievance Module (src/app/grievances/)
GrievanceListingPage.js: Similar to DPRListingPage.js.
GrievanceDetailPage.js: Similar to DPRDetailPage.js, uses RequestHistoryTrail.js.
11. RoPA Module (src/app/ropa/)
RoPAListingPage.js: DataTableWrapper for RoPA entries. "Add New" button. Filters/Search.
RoPAForm.js: Modal or page for creating/editing a RoPA entry. Sections matching RoPA elements (REQ-APP-112).
RoPAView.js: Component or section within listing/detail to display a single RoPA entry in a structured, readable way. Export buttons.
12. Compliance Documentation Module (src/app/complianceDocs/)
ComplianceDocsPage.js: File explorer UI. Breadcrumbs. Buttons for Upload, New Folder. Lists files/folders. Handles navigation, download, delete actions.
FileFolderItem.js: Component to render individual file or folder in the list.
Quick link sections for generated/translated notices and templates.
13. Task Management Module (src/app/tasks/)
TaskListingPage.js: Filters, DataTableWrapper for tasks.
TaskFormModal.js: For creating/editing tasks.
14. Contexts (src/contexts/)
AuthContext.js: Manages user authentication state (token, user object, roles, permissions), login/logout functions.
ThemeContext.js: Manages dark/light mode preference and theme object.
OrgContext.js: (Optional) Stores current Organisation's details if frequently needed across components.
NotificationContext.js: Manages display of global snackbar notifications.
15. Services (src/services/)
Modularized axios instances or fetch wrappers for API calls to different backend resource groups (e.g., authService.js, organisationService.js, noticeService.js, dprService.js, etc.).

