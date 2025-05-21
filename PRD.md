Product Requirements Document: ComplyArkWebApp MVP
1. Introduction
1.1. Purpose of this Document
This Product Requirements Document (PRD) specifies the functional and non-functional requirements for the Minimum Viable Product (MVP) of ComplyArkWebApp. It serves as the primary guide for the design, development, and testing of the MVP, ensuring alignment with business objectives and user needs for compliance with The Digital Personal Data Protection Act, 2023 (DPDPA).
1.2. Product Name:
ComplyArkWebApp
1.3. Product Goal (MVP)
The primary goal of the ComplyArkWebApp MVP is to provide Indian businesses (Data Fiduciaries) with an essential, user-friendly toolkit to initiate and manage their compliance with the DPDPA. This includes features for understanding data processing activities, generating DPDPA-compliant notices, managing Data Principal requests and grievances, and maintaining foundational compliance documentation. The MVP aims to deliver demonstrable value, simplify complex legal requirements, and gather critical feedback from early adopters for future iterations.
1.4. Product Vision (Long-term)
To be the premier, AI-enhanced, comprehensive cloud solution that empowers Indian businesses of all sizes to confidently and efficiently navigate, manage, and sustain compliance with data protection regulations, beginning with the DPDPA and evolving to address a broader spectrum of data governance needs.
1.5. Scope of MVP
1.5.1. Inclusions (Key Modules & High-Level Features):
System Administration Interface: For ComplyArk internal admins to manage organisations, users, industries, notice templates, and request statuses.
Core Main Application (for Data Fiduciaries):
Secure Organisation User Authentication & Role-Based Access (OrgAdmin, OrgUser).
Dashboard providing an overview of compliance status (DPRs, Grievances).
Organisation User Management (by OrgAdmins).
Notice Module: Guided questionnaire for data collection, AI-assisted (placeholder) notice generation from templates (pre-set or uploaded), (dummy) translation into 22 official Indian languages, and notice storage.
External Request Page: Publicly accessible, organisation-specific portal for Data Principals to submit Data Principal Requests (DPRs) and Grievances.
Data Principal Request (DPR) Module: Internal tracking, assignment, status updates, and history logging for received DPRs.
Grievances Module: Similar to DPR module for tracking and managing grievances.
Record of Processing Activities (RoPA) & DPA Management Support: Manual input for RoPA elements (leveraging Notice Questionnaire data), visualization/viewing of RoPA, and support for storing/managing DPAs within the documentation module.
Compliance Documentation Module: Secure storage and management of compliance-related documents (policies, notices, DPAs, etc.) with folder structures.
Basic Task Management Module: For creating and tracking compliance-related tasks.
The application UI language for the MVP will be English.
1.5.2. Exclusions (Features explicitly deferred Post-MVP):
Direct platform features or portal for Data Processors.
Dedicated Data Principal consent management dashboard (consent withdrawal via DPR module).
Automated notice delivery mechanisms (email, SMS, etc.).
Automated/Integrated RoPA generation from client systems (MVP relies on manual input).
Dedicated Data Protection Impact Assessment (DPIA) module or advanced scheduling features beyond manual task management.
Specific verifiable consent intake mechanisms for child/disability data directly via the platform (questionnaire will focus on documenting the Fiduciary's process).
Tailored modules or "modes" for Significant Data Fiduciaries (SDFs) beyond using generic tools.
Platform-performed tokenization or direct manipulation of Fiduciary's raw data.
Advanced security features (MFA, granular RBAC beyond OrgAdmin/OrgUser, advanced encryption options, formal security audits/certifications).
NLP-based auto-classification or discovery of personal data.
Automated data mapping & visualization tools beyond RoPA viewing.
Automated workflows for Data Principal Requests (e.g., auto-assignment, automated responses).
Dedicated Breach Reporting Aid module.
Vendor Management / Third-Party Risk assessment module.
Configurable Consent Form builder.
Employee Training & Awareness module.
Advanced Risk Assessment modules.
AI-powered simplified language summaries of legal text.
Advanced AI agentic workflows for compliance tasks.
Scalable in-app automated user onboarding wizards and comprehensive help documentation.
Full-fledged audit logging and reporting for compliance verification (MVP has basic logging).
Integration with external identity providers (e.g., full Google/Microsoft login for main app).
1.6. Target Audience
1.6.1. Primary Users (Data Fiduciary Personnel):
Compliance Officers / Legal Personnel: Responsible for overall DPDPA compliance strategy, policy creation, and oversight. Will use the platform for notice generation, RoPA management, DPR oversight, and documentation.
IT Managers / Operations Personnel: May be involved in providing information for the Notice Questionnaire/RoPA, managing user access within the platform for their organisation, and handling technical aspects of data processing documentation.
Business Owners (especially in SMEs): May directly use the platform to manage compliance if dedicated roles do not exist.
Designated Individuals: Any employee assigned responsibility for specific DPDPA tasks.
Assumption: Users may have varying levels of prior DPDPA knowledge.
1.6.2. System Administrator (ComplyArk Internal):
Internal ComplyArk team members responsible for platform setup, master data management (industries, templates), onboarding new client organisations, and initial System Admin user provisioning.
1.6.3. External Requesters (Data Principals):
Individuals (customers, employees, website visitors, etc.) whose personal data is processed by an organisation (Data Fiduciary) using ComplyArkWebApp.
Will use the organisation-specific "Create Request Page" to submit Data Principal Requests (e.g., access, correction, erasure, nomination) or log grievances.
1.7. Definitions, Acronyms, and Abbreviations
ComplyArkWebApp: The name of the SaaS platform being developed.
DPDPA: The Digital Personal Data Protection Act, 2023 (India).
DPDP Rules: Rules to be made under the DPDPA by the Central Government.
MVP: Minimum Viable Product.
DF / Data Fiduciary: As defined in DPDPA Section 2(i) - any person who alone or in conjunction with other persons determines the purpose and means of processing of personal data. (The organisations using ComplyArkWebApp).
DP / Data Principal: As defined in DPDPA Section 2(j) - the individual to whom the personal data relates.
Data Processor: As defined in DPDPA Section 2(k) - any person who processes personal data on behalf of a Data Fiduciary.
RoPA: Record of Processing Activities (an obligation implied under DPDPA Section 8 accountability).
DPR: Data Principal Request (requests made by DPs to exercise their rights).
DPA: Data Processing Agreement.
SLA: Service Level Agreement (for request processing timelines).
CRUD: Create, Read, Update, Delete.
RBAC: Role-Based Access Control.
UI: User Interface.
UX: User Experience.
JWT: JSON Web Token.
API: Application Programming Interface.
SDF: Significant Data Fiduciary (as may be notified under DPDPA Section 10).
DPIA: Data Protection Impact Assessment.
LLM: Large Language Model.
1.8. Document Conventions
Requirements are prefixed (e.g., REQ-ADM-XXX, REQ-APP-XXX, REQ-EXT-XXX, NFR-XXX).
Priority for MVP is assumed high for all listed requirements unless otherwise specified.
"Shall" indicates a mandatory requirement. "Should" indicates a strong recommendation. "May" indicates an optional feature or possibility.
1.9. References
The Digital Personal Data Protection Act, 2023 (No. 22 of 2023).
"Compliance Obligations under DPDPA" PDF document (provided by user).
All previous interactive discussion logs and clarifications related to this project.
IndicTrans2 Documentation (for future translation integration reference).
Material UI Documentation.

2. User Stories & Scenarios (Illustrative)
This section provides illustrative user stories and scenarios to help understand how different users will interact with the ComplyArkWebApp MVP and achieve their goals. These are not exhaustive but represent key use cases.
2.1. Persona: Priya Sharma – System Administrator (ComplyArk Admin)
Background: Priya is part of the ComplyArk operations team. Her responsibilities include setting up new client organisations on the platform and maintaining master data that the platform uses.
Goals:
Efficiently onboard new Data Fiduciary organisations.
Ensure the platform has up-to-date industry classifications and notice templates.
Manage system-level user accounts.
Scenario 2.1.1: Onboarding a New Organisation
Priya receives a request to onboard "Innovatech Solutions," a new e-commerce client.
She logs into the ComplyArkWebApp System Admin interface using her complyarkadmin credentials.
She navigates to the "Organisations" tab.
Priya clicks "Add New Organisation."
She fills in the form with Innovatech Solutions' details:
Business Name: "Innovatech Solutions"
Business Address: "123 Tech Park, Bangalore, KA, 560078"
Industry: Selects "E-commerce" from the dropdown.
Contact Person Name: "Arjun Mehta"
Contact Email Address: "arjun.mehta@innovatech.com"
Contact Phone Number: "98XXXXXX01"
No. of Users: "10"
Remarks: "Pilot e-commerce client for DPDPA compliance."
She clicks "Create." The system confirms creation.
The system automatically generates:
A default OrgAdmin user for Innovatech Solutions (e.g., admin@innovatechsolutions.com with password admin<OrgID>).
A unique RequestPageURL for Innovatech Solutions.
Priya sees Innovatech Solutions listed in the Organisations table with its new OrgID and RequestPageURL.
She communicates the OrgAdmin credentials and the RequestPageURL to Arjun Mehta at Innovatech Solutions.
Scenario 2.1.2: Adding a New Notice Template for the Healthcare Industry
Priya is informed that a new standard "Patient Data Consent Notice" template is needed for healthcare clients.
She logs into the System Admin interface.
She navigates to the "Templates" tab.
Priya clicks "Add New Template."
She fills in the form:
Template Name: "Patient Data Consent Notice V1"
Template Body: (Pastes the generic text content of the notice)
Industry: Selects "Healthcare" from the dropdown.
Template File: Uploads the corresponding Patient_Data_Consent_Notice_V1.docx file.
She clicks "Create."
The new template is now available for selection by Healthcare organisations within the Notice Module.
2.2. Persona: Arjun Mehta – Organisation Administrator (Data Fiduciary at Innovatech Solutions)
Background: Arjun is the Head of Operations at Innovatech Solutions, an e-commerce company. He has been assigned responsibility for DPDPA compliance.
Goals:
Set up his company's users on ComplyArkWebApp.
Generate a DPDPA-compliant privacy notice for their website.
Oversee the handling of Data Principal Requests.
Maintain compliance documentation.
Scenario 2.2.1: Setting up an Internal User for DPR Handling
Arjun logs into ComplyArkWebApp using the OrgAdmin credentials provided by Priya.
He navigates to the "Users" module (visible to him as OrgAdmin).
He clicks "Add New User."
He creates an account for Kavita, from their customer support team, who will handle DPRs:
FirstName: "Kavita"
LastName: "Rao"
Email: "kavita.rao@innovatech.com"
Phone: "97XXXXXX02"
Role: (Defaults to 'OrgUser')
IsActive: Checked
CanEdit (for DPRs/Grievances): Checked
CanDelete (for DPRs/Grievances): Unchecked (for now)
Password: Sets an initial password.
He clicks "Create User."
Arjun informs Kavita of her new credentials.
Scenario 2.2.2: Generating a Website Privacy Notice
Arjun logs into ComplyArkWebApp.
He navigates to the "Notice Module."
Tab 1 (Questionnaire):
He meticulously goes through each category (Contact Details, Financial Info for payments, etc.), selecting the data Innovatech collects (e.g., Name, Email, Address, Phone, Payment Info for orders, IP Address for analytics).
For each, he provides the "Reason for Collection" (e.g., "To process and deliver orders," "For customer communication," "To prevent fraud").
He indicates they share data with "Logistics Partner X" and "Payment Gateway Y" for order fulfillment and payment processing.
He confirms Innovatech does not knowingly process children's data and has relevant checks (he notes this for their internal policy, prompted by the questionnaire section).
He clicks "Next."
Tab 2 (Notice Type & Preview):
He sees "Innovatech Solutions" is an "E-commerce" company.
He selects an existing "E-commerce Privacy Notice Template V1.2" from the dropdown.
The text editor populates with the template's body.
The "Data from Questionnaire" box shows a formatted summary of his Tab 1 selections.
He inputs "Innovatech Website Privacy Policy" as the "Notice Title Prefix."
He reviews the template and the questionnaire data. He copies some specific phrasing about payment data from the questionnaire box and pastes it into a relevant section of the main editor.
He clicks "Preview" to see how it looks (basic text preview).
Satisfied, he clicks "Save & Next." The system saves this as "Innovatech Website Privacy Policy_InnovatechOrgID_V1" and creates a corresponding file.
Tab 3 (Translation):
He sees the "Original Document (English)" tile with download options.
He selects "Hindi" and "Tamil" from the language list.
He clicks "Translate." The system (dummy) processes this.
Tiles for "Innovatech Website Privacy Policy_InnovatechOrgID_V1_hin_Deva" and "..._tam_Taml" appear with download options.
Arjun downloads the English, Hindi, and Tamil versions to provide to their web development team.
Scenario 2.2.3: Receiving and Assigning a Data Access Request
An email notification (simulated for MVP, Arjun checks dashboard) indicates a new Data Principal Request.
Arjun logs into ComplyArkWebApp and navigates to the "Data Principal Requests" module.
He sees a new request from "Rina Das" with Request Type "Access" and status "Submitted."
He clicks on the request to view details. Rina wants to know what personal data Innovatech holds about her.
Arjun decides to assign this to Kavita Rao. In the detail view, he selects "Kavita Rao" from the "Assigned To" dropdown and changes the status to "InProgress."
He adds an internal comment: "Kavita, please collate data for Rina Das as per her access request. Due by [date]."
He clicks "Update." The request history is updated. Kavita would (in a future version) get a notification.
Scenario 2.2.4: Managing Documents for an Internal Audit
Innovatech is preparing for an internal DPDPA readiness review.
Arjun navigates to the "Compliance Documentation" module.
He creates a new folder named "Internal Audit Prep Q1-2024."
Inside this folder, he uploads:
Their internal Data Retention Policy (DOCX).
A Data Processing Agreement they signed with "Payment Gateway Y" (PDF).
The generated "Innovatech Website Privacy Policy_InnovatechOrgID_V1.pdf".
He also navigates to the "Generated Notices" quick link within the module to confirm all versions of their notices are accessible.
2.3. Persona: Kavita Rao – Organisation User (Data Fiduciary Staff at Innovatech Solutions)
Background: Kavita is in customer support at Innovatech and has been assigned to handle incoming DPRs. Arjun has given her "CanEdit" permissions for DPRs.
Goals:
Process assigned DPRs according to company policy and DPDPA timelines.
Keep the status of requests updated in ComplyArkWebApp.
Scenario 2.3.1: Processing an Assigned Data Access Request
Kavita logs into ComplyArkWebApp. Her dashboard shows a task/item assigned to her (the DPR from Rina Das).
She navigates to the "Data Principal Requests" module and filters by "Assigned To: Kavita Rao."
She opens Rina Das's request (Status: "InProgress").
Internally (outside ComplyArkWebApp), Kavita queries Innovatech's CRM and order systems to gather Rina's data (name, contact, order history, support interactions).
Once data is collated into a document, she needs to provide it to Rina (manual process for MVP).
She returns to ComplyArkWebApp, opens Rina's DPR detail page.
She changes the status to "AwaitingInfo" (if she needs clarification from Rina) or directly to "Closed" if she has provided the information. Let's assume she provided it.
She selects "Closed" status. The "Closure Comment" box appears.
She enters: "Data access report provided to Rina Das via email on [Date]. Report attached to internal case #XYZ."
She clicks "Update." The request is now closed, and the history log reflects this.
2.4. Persona: Rina Das – External Requester (Data Principal, Customer of Innovatech Solutions)
Background: Rina is a customer of Innovatech Solutions and wants to know what data they have about her.
Goals:
Easily submit a data access request to Innovatech Solutions.
(Future goal, not MVP) Receive timely information.
Scenario 2.4.1: Submitting a Request for Data Access
Rina finds a link on Innovatech Solutions' website: "Exercise Your Data Rights." This link leads to Innovatech's RequestPageURL for ComplyArkWebApp (e.g., http://localhost:3000/request/innovatech-uuid).
She lands on the external request page. It shows "Innovatech Solutions" name.
She performs the dummy login (e.g., enters email/password, clicks "Login").
She is presented with options: "Raise Data Principal Request" / "Log a Grievance." She clicks "Raise Data Principal Request."
She fills out the DPR form:
FirstName: "Rina"
LastName: "Das"
Email: "rina.das@email.com"
PhoneNumber: "99XXXXXX03"
Request Type: Selects "Access" from the dropdown.
RequestComment: "I would like to request a copy of all personal data that Innovatech Solutions holds about me."
She clicks "Submit Request."
The form disables, and she sees a message: "Your request has been successfully submitted. Innovatech Solutions will process it and respond to you. Your Request ID is DPR-XXXX." (Request ID not explicitly part of MVP form, but good for user feedback).
3. Product Features & Functional Requirements (Detailed by Module)
This section details the functional requirements for ComplyArkWebApp MVP, broken down by module and user interface.
3.1. Core Platform & System Administration (complyarkadmin Interface)
This module is exclusively for ComplyArk System Administrators to manage the platform's foundational data and client organisations.
3.1.1. System Admin Authentication
REQ-ADM-001: The system shall provide a dedicated login page for System Administrators at a specific URL (e.g., /admin/login).
REQ-ADM-002: System Admin shall authenticate using a predefined, unique username (complyarkadmin) and a strong password. This credential shall be stored securely (hashed) in the Users table with Role = 'SystemAdmin'.
REQ-ADM-003: Upon successful authentication, the system shall generate a JSON Web Token (JWT) containing userId and role: 'SystemAdmin', which shall be used to authorize subsequent API requests. The JWT shall have a defined expiration period.
REQ-ADM-003a: Unsuccessful login attempts (e.g., incorrect password) shall display a generic error message without revealing whether the username or password was incorrect. Account lockout after multiple failed attempts is desirable but deferred post-MVP.
3.1.2. Organisation Management (DPDPA: Data Fiduciary Onboarding)
REQ-ADM-004: System Admin shall be able to access an "Organisations" tab/section.
REQ-ADM-005 (Create): System Admin shall be able to create a new Organisation profile by providing the following mandatory details:
Business Name (Text Input)
Business Address (Multiline Text Input: street, city, state, postal code)
Industry (Dropdown, populated from Industry master data - REQ-ADM-016)
Contact Person Name (Text Input)
Contact Email Address (Email Input, validated format)
Contact Phone Number (Number/Text Input, basic validation)
No. of Users (Number Input, representing expected users for the org)
And the following optional detail:
Remarks (Multiline Text Input)
REQ-ADM-006 (Default OrgAdmin): Upon successful Organisation creation, the system shall automatically create a default Organisation Administrator (OrgAdmin) user in the Users table associated with the newly created OrganisationID.
Default OrgAdmin credentials:
FirstName: "Admin" (or derived from Business Name)
LastName: Business Name (or "User")
Email: A unique email (e.g., admin@<SanitizedBusinessName>.com or org<OrgID>_admin@complyark.com)
Password: Programmatically generated (e.g., admin<OrganisationID>), securely hashed, and communicated to System Admin for manual sharing with the client.
Role: 'OrgAdmin'
CanEdit: true, CanDelete: true (for users within their org)
IsActive: true
REQ-ADM-007 (RequestPageURL): Upon successful Organisation creation, the system shall generate a unique, persistent identifier (e.g., UUID) and construct a RequestPageURL (e.g., http://localhost:3000/request/{uuid}). This URL shall be stored in the Organisation table.
REQ-ADM-008 (Read/List): System Admin shall be able to view a list of all onboarded Organisations in a paginated, searchable (by Business Name, Email), and filterable (by Industry, IsActive status) data table. Columns: OrgID, Business Name, Industry, Contact Person, Contact Email, NoOfUsers, RequestPageURL, IsActive, Actions (Edit, Delete).
REQ-ADM-009 (Update): System Admin shall be able to select an Organisation from the list and edit all its details (as in REQ-ADM-005).
REQ-ADM-009a: System Admin shall have an option to regenerate the RequestPageURL for an existing Organisation (updates the stored UUID/URL).
REQ-ADM-010 (Delete/Deactivate): System Admin shall be able to (de)activate an Organisation.
Deactivating an Organisation should prevent its users from logging in and make its RequestPageURL inactive.
Actual deletion of an Organisation (and its associated data) is a complex operation deferred post-MVP. For MVP, "delete" may function as deactivation. A confirmation dialog ("Are you sure?") shall be displayed.
3.1.3. System-Wide User Management (Primarily for System Admins themselves)
REQ-ADM-011: System Admin shall be able to access a "System Users" tab/section.
REQ-ADM-012 (Create): System Admin shall be able to create new user accounts with the Role = 'SystemAdmin'. Fields: FirstName, LastName, Email, Phone, Password.
REQ-ADM-013 (Read/List): System Admin shall be able to view a list of all users with Role = 'SystemAdmin' (and potentially OrgAdmins if a global user view is needed, though OrgAdmins are primarily managed under their Organisation). Data table with search/filter.
REQ-ADM-014 (Update): System Admin shall be able to edit details of other SystemAdmins (except their own password directly; offer a password reset mechanism if needed).
REQ-ADM-015 (Delete/Deactivate): System Admin shall be able to (de)activate or delete other SystemAdmin accounts (except their own, with confirmation).
3.1.4. Industry Master Data Management
REQ-ADM-016: System Admin shall be able to access an "Industries" tab/section.
REQ-ADM-017 (Create): System Admin shall be able to add a new Industry by providing IndustryName. Name must be unique.
REQ-ADM-018 (Read/List): System Admin shall be able to view a list of all Industries in a paginated, searchable data table. Columns: IndustryID, IndustryName, IsActive, Actions.
REQ-ADM-019 (Update): System Admin shall be able to edit an existing IndustryName and its IsActive status.
REQ-ADM-020 (Delete): System Admin shall be able to delete an Industry (with confirmation). Impact: If an industry is in use by Organisations, deletion should be prevented or handled by reassigning Orgs. For MVP, prevent deletion if in use, or allow soft delete (mark inactive).
3.1.5. Notice Template Management
REQ-ADM-021: System Admin shall be able to access a "Templates" tab/section.
REQ-ADM-022 (Create): System Admin shall be able to create a new Notice Template by providing:
Template Name (Text Input, e.g., "E-commerce Privacy Policy v1")
Template Body (Multiline Textbox for the generic notice content)
Industry (Dropdown, selecting an Industry this template is primarily for)
Template File (File Upload: PDF/DOCX). The file shall be saved to the TemplateRepo/ folder on the server, and its path stored in Template.TemplatePath.
REQ-ADM-023 (Read/List): System Admin shall be able to view a list of all Notice Templates in a paginated, searchable data table. Columns: TemplateID, Template Name, Industry, TemplatePath (display filename, perhaps a download link), Actions.
REQ-ADM-024 (Update): System Admin shall be able to edit an existing Template's Name, Body, and associated Industry. They shall also be able to replace the uploaded Template File (old file should be deleted from server if replaced).
REQ-ADM-025 (Delete): System Admin shall be able to delete a Template (with confirmation). This should also delete the associated file from TemplateRepo/.
3.1.6. Request Status & SLA Management
REQ-ADM-026: System Admin shall be able to access a "Request Statuses" tab/section.
REQ-ADM-027 (Create): System Admin shall be able to define new statuses for DPRs and Grievances by providing:
Request Status Name (Text Input, e.g., "Submitted", "Awaiting Clarification", "Resolved") - must be unique.
SLA (Number Input, in days - representing the typical time to remain in/resolve from this status, used for ExpectedCompletionDate calculation).
IsActive (Checkbox).
REQ-ADM-028 (Read/List): System Admin shall be able to view a list of all defined Request Statuses in a paginated, searchable data table. Columns: RequestStatusID, RequestStatusName, SLA (days), IsActive, Actions.
Initial seed data: 'Submitted', 'InProgress', 'AwaitingInfo', 'Reassigned', 'Escalated', 'Closed'.
REQ-ADM-029 (Update): System Admin shall be able to edit an existing Request Status Name, its SLA, and IsActive status.
REQ-ADM-030 (Delete): System Admin shall be able to delete a Request Status (with confirmation). Prevent deletion if the status is currently in use by any active DPRs or Grievances.
3.1.7. System Admin Dashboard
REQ-ADM-031: A simple dashboard for the System Admin displaying high-level platform statistics. For MVP, this can include:
Total number of onboarded Organisations.
Total number of Notice Templates.
Total number of Industries.
(Future: Active users, system health indicators).
3.2. Main Application - Core Functionality (Organisation User Interface)
This section details the core functionalities accessible to logged-in Organisation Users (OrgAdmins and OrgUsers). All features here are scoped to the user's specific Organisation.
3.2.1. Organisation User Authentication
REQ-APP-001: Users associated with an Organisation (OrgAdmins, OrgUsers) shall be able to log in to the main application (e.g., at /login) using their registered email address and password.
REQ-APP-002: Backend authentication shall verify credentials against the Users table, ensuring the user belongs to an active Organisation (Organisation.IsActive = true) and the user account itself is active (Users.IsActive = true).
REQ-APP-003: Upon successful authentication, the system shall generate a JSON Web Token (JWT) containing userId, organisationId, role (e.g., 'OrgAdmin', 'OrgUser'), firstName, lastName, and permissions flags like canEdit, canDelete. This JWT shall be used for authorizing subsequent API requests.
REQ-APP-004: The system shall provide a "Forgot Password" mechanism:
User enters their registered email address.
System (dummy for MVP) simulates sending a password reset link/token (e.g., logs to console).
User clicks a (simulated) link with a token to a "Reset Password" page.
User enters and confirms a new password.
Backend validates the token and updates the user's hashed password.
REQ-APP-005: Authenticated users shall be able to log out of the application, which shall invalidate their current session/JWT on the client-side.
REQ-APP-005a: Unsuccessful login attempts shall display a generic error message. Account lockout after multiple failed attempts is deferred post-MVP.
3.2.2. Main Application Layout & Navigation
REQ-APP-006: After successful login, the application shall present a consistent layout comprising a main content area, a persistent header, and a persistent left navigation panel (sidebar).
REQ-APP-007 (Header):
Shall display the Business Name of the logged-in user's Organisation (fetched from Organisation table via organisationId in JWT).
Shall display the logged-in user's name or initials.
Shall provide a "Logout" button/link.
REQ-APP-008 (Left Navigation Panel):
Shall be collapsible/expandable (icon-only when collapsed).
Shall provide clear, clickable links to the main modules accessible to the user based on their role:
Dashboard
Users (Visible to OrgAdmin only)
Notice Module
Data Principal Requests (DPR)
Grievances
Compliance Documentation
My Profile (Primarily for OrgUser, OrgAdmin may also have a profile link)
The currently active module/page shall be visually highlighted in the navigation panel.
REQ-APP-009 (Dark Mode):
A toggle switch (e.g., in the footer of the navigation panel or header) shall allow users to switch between a light theme and a dark theme for the application UI.
The user's theme preference should ideally be persisted (e.g., in localStorage).
3.2.3. Role-Based Access Control (RBAC) - Basic for MVP
REQ-APP-010: The visibility of navigation links and access to certain functionalities within modules shall be controlled based on the user's role (OrgAdmin or OrgUser) and their canEdit/canDelete permissions (stored in JWT and Users table).
Example: "Users" module link visible only to OrgAdmin.
Example: Delete buttons in DPR/Grievance modules enabled only if user role permits or canDelete is true.
REQ-APP-011: Backend APIs shall rigorously enforce these permissions, not relying solely on frontend UI restrictions. Attempts to access unauthorized resources or perform unauthorized actions shall result in an appropriate error response (e.g., 403 Forbidden).
3.2.4. User Profile Management (for the logged-in Organisation User)
REQ-APP-012: Logged-in Organisation Users (both OrgAdmin and OrgUser) shall be able to access a "My Profile" page.
REQ-APP-013 (View Profile): The profile page shall display the user's own details in a read-only format:
FirstName, LastName
Email (cannot be changed via this interface)
Phone Number (may be editable if design allows)
Role within the Organisation
REQ-APP-014 (Change Password): The profile page shall provide an option for the user to change their own password.
Requires current password, new password, and confirm new password fields.
Backend API validates the current password before updating to the new hashed password.
3.3. Main Application - Dashboard Module (Organisation View)
This module serves as the landing page for Organisation Users after login, providing a high-level overview of key compliance metrics and activities relevant to their Organisation.
3.3.1. Organisation-Specific Summary & Welcome
REQ-APP-015: The Dashboard shall prominently display a welcome message including the logged-in user's name and their Organisation's Business Name.
REQ-APP-016: The data presented on the Dashboard shall be dynamically fetched and reflect real-time (or near real-time) statistics for the user's Organisation only.
3.3.2. Data Principal Request (DPR) Status Overview
REQ-APP-017: The Dashboard shall display a visual representation (e.g., a Pie Chart using a library like Recharts or MUI's data display components) showing the distribution of all active (non-Closed) Data Principal Requests by their current status (e.g., 'Submitted', 'InProgress', 'AwaitingInfo', 'Reassigned', 'Escalated').
REQ-APP-018: Each segment of the chart should display the count of requests in that status.
REQ-APP-019: Chart segments or an accompanying legend should be clickable, navigating the user to the DPR Listing Page, pre-filtered by the selected status.
3.3.3. Grievance Status Overview
REQ-APP-020: Similar to DPRs, the Dashboard shall display a visual representation (e.g., a separate Pie Chart) showing the distribution of all active (non-Closed) Grievances by their current status.
REQ-APP-021: Each segment of the chart should display the count of requests in that status.
REQ-APP-022: Chart segments or an accompanying legend should be clickable, navigating the user to the Grievance Listing Page, pre-filtered by the selected status.
3.3.4. Escalated Data Principal Requests Table
REQ-APP-023: The Dashboard shall feature a data table listing Data Principal Requests that are considered "Escalated."
REQ-APP-024 (Escalation Criteria): A DPR is considered escalated if its ExpectedCompletionDate has passed (is less than the current date) AND its CurrentStatusID is not 'Closed'.
REQ-APP-025 (Table Columns): The table shall display, at a minimum:
DPR ID
Requester Name (FirstName LastName)
Request Type
Expected Completion Date (highlighted if overdue)
Assigned To (Name of the assigned Org User/Admin)
Current Status
REQ-APP-026: The table shall be sortable by Expected Completion Date (oldest overdue first).
REQ-APP-027: Each row in the escalated DPRs table shall be clickable, navigating the user directly to the Detail Page for that specific DPR.
REQ-APP-028: If there are no escalated DPRs, a message indicating this (e.g., "No escalated Data Principal Requests") shall be displayed instead of an empty table.
3.3.5. Escalated Grievances Table
REQ-APP-029: The Dashboard shall feature a data table listing Grievances that are considered "Escalated."
REQ-APP-030 (Escalation Criteria): A Grievance is considered escalated if its ExpectedCompletionDate has passed (is less than the current date) AND its CurrentStatusID is not 'Closed'.
REQ-APP-031 (Table Columns): The table shall display, at a minimum:
Grievance ID
Requester Name (FirstName LastName)
Expected Completion Date (highlighted if overdue)
Assigned To (Name of the assigned Org User/Admin)
Current Status
REQ-APP-032: The table shall be sortable by Expected Completion Date (oldest overdue first).
REQ-APP-033: Each row in the escalated Grievances table shall be clickable, navigating the user directly to the Detail Page for that specific Grievance.
REQ-APP-034: If there are no escalated Grievances, a message indicating this (e.g., "No escalated Grievances") shall be displayed.
3.3.6. Role-Specific Dashboard Views (MVP Consideration)
REQ-APP-035: While the overall dashboard structure is similar for OrgAdmin and OrgUser, the data displayed in the "Escalated" tables or any "My Tasks" (future) section should consider the logged-in user.
OrgAdmin sees all escalated items for the entire Organisation.
OrgUser (for MVP, primarily) sees escalated items that are assigned to them. If an OrgUser has broader visibility permissions, this might be adjusted, but assignment-based visibility is the default for specific action items.
This requires backend API for escalated items to optionally accept an assignedToUserId filter.
3.3.7. Data Fetching
REQ-APP-036: All data for the dashboard components shall be fetched via a dedicated backend API endpoint (e.g., GET /api/app/dashboard/summary) which aggregates the necessary counts and lists. This API will be called when the Dashboard component mounts or is refreshed.
3.4. Main Application - Organisation User Management Module (OrgAdmin Role)
This module is accessible only to users with the OrgAdmin role within their specific Organisation. It allows them to manage user accounts (primarily OrgUser roles) for their Organisation on the ComplyArkWebApp platform.
3.4.1. Access Control
REQ-APP-037: The "Users" link in the main application's left navigation panel shall only be visible and accessible to users logged in with the OrgAdmin role.
REQ-APP-038: All backend APIs for this module shall validate that the requesting user has the OrgAdmin role and that operations are scoped to their organisationId.
3.4.2. User Listing and Viewing
REQ-APP-039: Upon accessing the module, the OrgAdmin shall be presented with a paginated, searchable (by Name, Email), and filterable (by Role - e.g., 'OrgUser', 'OrgAdmin'; by Status - 'Active'/'Inactive') data table listing all users belonging to their Organisation.
REQ-APP-040 (Table Columns): The user list data table shall display, at a minimum:
User ID (internal identifier)
First Name
Last Name
Email
Phone Number
Role (e.g., 'OrgUser', 'OrgAdmin')
IsActive (e.g., Yes/No, or a status badge)
CanEdit (for DPR/Grievances - Yes/No, applicable to OrgUsers)
CanDelete (for DPR/Grievances - Yes/No, applicable to OrgUsers)
Last Login Date (Desirable, may be post-MVP if audit logging for login is not in MVP)
Actions (Edit, Delete/Deactivate)
3.4.3. Creating New Organisation Users
REQ-APP-041: An "Add New User" button shall be available on the user listing page.
REQ-APP-042: Clicking "Add New User" shall open a form (e.g., in a modal or a separate view) with the following fields for creating a new user within the OrgAdmin's Organisation:
First Name (Text Input, mandatory)
Last Name (Text Input, mandatory)
Email (Email Input, mandatory, must be unique within the platform)
Phone Number (Text Input, optional)
Password (Password Input, mandatory, with confirmation field. Backend hashes it.)
Role (Dropdown: For MVP, OrgAdmin can only create users with the 'OrgUser' role via this interface to maintain simplicity. Creating other OrgAdmins is a System Admin function or a more advanced feature).
IsActive (Checkbox, defaults to true/checked)
Permissions (visible if 'OrgUser' role is selected):
Can Edit (DPRs/Grievances assigned to them or generally) (Checkbox, defaults to false/unchecked)
Can Delete (DPRs/Grievances assigned to them or generally) (Checkbox, defaults to false/unchecked)
REQ-APP-043: The OrganisationID for the new user will be automatically set to the OrgAdmin's organisationId on the backend.
REQ-APP-044: Upon successful creation, the new user shall be added to the user list, and a success notification displayed.
3.4.4. Editing Existing Organisation Users
REQ-APP-045: The OrgAdmin shall be able to click an "Edit" action/icon next to a user in the list.
REQ-APP-046: Editing shall open a form pre-filled with the selected user's current details. The OrgAdmin can modify:
First Name
Last Name
Phone Number
Role (If an OrgAdmin is editing another OrgAdmin within their org - for MVP, OrgAdmins primarily edit OrgUsers. Changing an OrgUser to an OrgAdmin might be restricted or require higher privilege not in MVP).
IsActive status
CanEdit and CanDelete permissions (for OrgUser roles).
REQ-APP-047: The user's Email address (often used as a unique login identifier) shall typically not be editable after creation to avoid identity issues. If it must be, careful validation for uniqueness is required. For MVP, it's safer to make it non-editable post-creation.
REQ-APP-048: There shall be no direct "Edit Password" field. Instead, a "Send Password Reset Link" (dummy email for MVP) or "Force Password Reset on Next Login" option should be considered for managing user passwords if an OrgAdmin needs to intervene. For MVP, OrgAdmin might not directly reset passwords; users use the "Forgot Password" flow.
REQ-APP-049: Upon successful update, the user list shall reflect the changes, and a success notification displayed.
3.4.5. Deactivating/Activating and Deleting Organisation Users
REQ-APP-050: The OrgAdmin shall be able to (de)activate a user account within their Organisation via an action in the user list (e.g., a toggle switch for IsActive or an "Activate/Deactivate" button).
A deactivated user shall not be able to log in.
REQ-APP-051: The OrgAdmin shall be able to delete a user account within their Organisation (with a confirmation dialog: "Are you sure you want to delete user [User Name]? This action cannot be undone.").
Consider implications of deleting a user who is currently assigned active DPRs/Grievances (e.g., prompt to reassign items, or items become unassigned). For MVP, deletion might be restricted if active assignments exist, or assignments are simply cleared.
An OrgAdmin cannot delete their own account via this interface.
3.4.6. Backend API Support
REQ-APP-052: Dedicated backend API endpoints (e.g., under /api/app/organisations/{orgId}/users or /api/app/users with scoping) shall support all CRUD operations for organisation-specific users, enforcing OrgAdmin role and organisationId scoping.
3.5. Main Application - Notice Module (DPDPA Sections 5, 6; Implied obligations for various notices)
This module enables Data Fiduciaries (Organisation Users) to generate DPDPA-compliant notices for Data Principals regarding the processing of their personal data. It involves a three-tab workflow: Questionnaire, Notice Type & Preview, and Translation.
3.5.0. General Module Access & State
REQ-APP-053: All authenticated Organisation Users (OrgAdmin, OrgUser) shall be able to access the Notice Module via the left navigation panel.
REQ-APP-054: The module shall maintain the state of the notice being created/edited across its three tabs until the user explicitly saves or abandons the process. (e.g., using React Context or a state management library scoped to this module).
3.5.1. Tab 1: Questionnaire For Notice (Data Collection for Notice Content - DPDPA Section 5(1))
REQ-APP-055 (Interface): This tab shall present a structured, interactive questionnaire designed to collect all necessary information required to populate a DPDPA-compliant notice.
REQ-APP-056 (Categorization): The questionnaire shall be divided into logical, collapsible sections/categories using MUI Accordion or similar, for better organization and usability. Categories shall include (but not be limited to):
A. Basic Identifying Information of Data Fiduciary: (Pre-filled from Organisation profile, but confirmable/editable for this notice if needed – e.g., specific department).
B. Personal Data to be Processed:
Contact Details (e.g., Name, Email, Phone, Address)
Financial Information (e.g., Bank Account, Credit Card for payments)
Health Data (if applicable)
Demographic Data (e.g., Age, Gender)
Technical Data (e.g., IP Address, Cookies, Device ID)
Other Categories (as relevant to the Fiduciary)
C. Purposes of Processing: For each category/item of personal data selected in (B).
D. Data of Children and Persons with Disabilities (DPDPA Section 9):
Specific questions to prompt the Fiduciary to document:
If they process personal data of children (below 18 years).
If they process personal data of persons with disabilities who have lawful guardians.
The method by which verifiable parental/guardian consent is obtained (Fiduciary describes their own process).
Confirmation that processing is not likely to cause detrimental effects to a child's well-being.
Confirmation that tracking, behavioral monitoring, or targeted advertising is NOT directed at children (unless permitted under exemptions).
E. Sensitive Personal Data (if applicable beyond D, general):
Questions regarding any other data defined or treated as sensitive that is being processed and specific consent/safeguards.
F. Lawful Basis (Beyond Consent): Section to document if processing relies on "Certain Legitimate Uses" (DPDPA Section 7) for any specific data/purpose, and which ones.
G. Data Sharing & Third Parties:
Does the Fiduciary share personal data with third parties (Data Processors or other Fiduciaries)? (Yes/No Radio)
If Yes: Repeatable input fields for [Name of Third Party], [Type of Third Party (Processor/Fiduciary)], [Categories of Data Shared], [Purpose of Sharing].
H. Cross-Border Data Transfer (DPDPA Section 16):
Does the Fiduciary transfer personal data outside India? (Yes/No)
If Yes: [Countries Transferred To], [Safeguards for Transfer] (Fiduciary describes their measures).
I. Data Retention Period: For each category/purpose, the intended retention period or the criteria used to determine it.
J. Rights of Data Principals (DPDPA Sections 11-14):
Information on how Data Principals can exercise their rights (Access, Correction, Erasure, Grievance Redressal, Nomination). This would typically be a link to their rights portal/contact (i.e., the ComplyArkWebApp CreateRequestPageURL for this Organisation).
Contact details of the Data Protection Officer (DPO) or designated contact person for grievances/queries (Name, Email, Phone – as per DPDPA Section 5(1)(iii) requiring manner to complain to Board & Sec 6(3) DPO contact for consent request).
K. Security Safeguards (DPDPA Section 8(5)): A general description of technical and organizational security measures implemented by the Fiduciary (Fiduciary describes their measures).
L. Algorithmic Verification Due Diligence (if applicable):
Does the Fiduciary use algorithms for significant decision-making or profiling? (Yes/No)
If Yes: Description of due diligence undertaken to ensure fairness and prevent bias.
M. Tokenization Practices (if applicable):
Does the Fiduciary use tokenization for any personal data? (Yes/No)
If Yes: Brief description of its application.
REQ-APP-057 (Field Interaction): Within each data category (e.g., Personal Data to be Processed), individual data items (e.g., "Email Address," "Phone Number") shall be presented with:
A checkbox for selection (indicating this data is processed for the notice being generated).
A mandatory textbox for "Specific Purpose(s) & Reason for Collection" if the item is selected.
REQ-APP-058 (Dynamic Fields): Users shall be able to:
Add custom data field items within relevant categories (e.g., a new type of "Technical Data").
Edit the labels of pre-defined or custom data fields (to match their internal terminology if needed).
REQ-APP-059 (Data Persistence & Validation):
Data entered in the questionnaire shall be temporarily persisted (e.g., in component state or a shared module context) as the user navigates between fields/sections.
Basic client-side validation (e.g., mandatory fields, email format) should be present.
REQ-APP-060 ("Next" Button): A "Next" button shall take the user to Tab 2, passing all collected and formatted questionnaire data.
3.5.2. Tab 2: Notice Type and Preview (Notice Composition - DPDPA Section 5(3) for language options)
REQ-APP-061 (Interface): This tab allows the user to select a notice structure and combine it with the data collected in Tab 1.
REQ-APP-062 (Template Selection):
A dropdown list labeled "Select Existing Template" shall be populated with Notice Templates (from Template table, filtered by the Organisation's IndustryID or showing all).
Selecting a template shall load its TemplateBody into the main text editor (REQ-APP-064) and note its TemplatePath (original file name).
REQ-APP-063 (Upload Custom Format):
An "Upload Notice Format" button shall allow users to upload their own notice document (PDF or DOCX).
The name of the uploaded file shall be displayed. This uploaded file will serve as the structural base if selected, instead of a pre-set template's body.
REQ-APP-064 (Main Text Editor):
A rich text editor (MUI TextareaAutosize for MVP, or a simple WYSIWYG like react-quill if feasible) shall be provided for composing/editing the main content of the notice.
If an existing template is chosen, its body is pre-filled here. Users can then edit it.
If a custom format is uploaded, this editor can be used for additional text or to manually integrate parts of the questionnaire data.
REQ-APP-065 (Questionnaire Data Display):
A clearly demarcated, non-editable, scrollable multi-line textbox (labeled "Data from Questionnaire - For Reference/Copying") shall display a well-formatted, read-only summary of all data points selected and entered in Tab 1.
Format Example:
**Personal Data Processed:**
 - Contact Details: Name (Purpose: To identify user), Email (Purpose: For communication)
 - Financial Information: Credit Card Number (Purpose: To process payment)
**Data Sharing:**
 - Third Party: PaymentGatewayX, Type: Processor, Data: Credit Card Info, Purpose: Payment Processing
**Rights & Contact:**
 - Exercise Rights: [Link to CreateRequestPageURL]
 - DPO Contact: [DPO Name], [dpo@email.com]
REQ-APP-066 (Notice Title Prefix): A mandatory text input field for "Notice Title Prefix" (e.g., "Website Privacy Policy", "Employee Data Notice", "App Consent Form"). This will be used in naming the final notice.
REQ-APP-067 (Language Option - for Notice Generation):
A dropdown to select the primary language for the notice being generated in this step (defaults to "English"). This refers to the language of the template/editor content itself, not the subsequent translation.
The DPDPA requires notices to be in English OR any language specified in the Eighth Schedule. This dropdown allows selection if a template is available in another Eighth Schedule language.
REQ-APP-068 (Preview Functionality):
A "Preview Notice" button shall open a modal displaying:
If a template's body was used: The current content of the main text editor.
If a custom format was uploaded: The name of the uploaded file (as the base) AND the content of the main text editor (as additional/appended text).
The content of the "Data from Questionnaire" box will not be automatically merged for preview in MVP unless the user explicitly copies it into the main editor. The preview is primarily for the editor's content.
REQ-APP-069 ("Save & Next" - Notice Finalization & Persistence):
On click, the system shall:
Perform validation (e.g., Notice Title Prefix is filled).
Construct the final NoticeName: [NoticeTitlePrefix]_[OrganisationID]_V[VersionNumber]. The system must check for existing notices with the same prefix for that OrganisationID and automatically increment the VersionNumber (e.g., V1, V2).
NoticeBody to be saved in Notice table: The content from the main text editor (REQ-APP-064).
NoticeType to be saved: If an existing template was selected, its TemplateName (or TemplatePath filename). If a custom format was uploaded, the name of that uploaded file.
File System Storage:
If a custom format (e.g., MyCustomNotice.pdf) was uploaded and is the base: This uploaded file is copied/renamed to GeneratedNotices/[OrgID]/[FinalNoticeName].pdf (or .docx). The text editor content (if any) is considered supplementary and is saved in Notice.NoticeBody but not automatically merged into this base file for MVP.
If a pre-set template's body was used and edited: The content of the main text editor (which includes user edits and potentially pasted questionnaire data) is saved as a new file. For MVP, this will be saved as GeneratedNotices/[OrgID]/[FinalNoticeName].txt. (Basic PDF generation from text is a stretch goal for MVP).
The FolderLocation (full path to the saved file in GeneratedNotices/) is stored in the Notice table.
CreatedByUserID (from logged-in user) and CreatedAt timestamp are recorded.
The newly created NoticeID is passed to Tab 3.
A success notification is displayed.
3.5.3. Tab 3: Translation (Multi-language Support - DPDPA Section 5(3))
REQ-APP-070 (Interface): This tab allows users to (simulate) translate the notice generated in Tab 2.
REQ-APP-071 (Display Original Document):
Upon loading Tab 3 (with a NoticeID from Tab 2), the system shall fetch and display a "tile" or card for the "Original Document."
Tile content: NoticeName (e.g., "Website Privacy Policy_Org123_V1"), Version, Language (e.g., "English - Original").
Download Options: Buttons to download the original notice file (e.g., "Download PDF", "Download DOCX", or "Download .txt" depending on what was saved in REQ-APP-069). These link to a backend file-serving endpoint.
REQ-APP-072 (Language Selection for Translation):
A list of the 22 official Indian languages specified in the Eighth Schedule of the Constitution shall be displayed with checkboxes next to each.
Languages for which IndicTrans2 provides support (as per documentation) shall be visually highlighted (e.g., bold text or an icon).
A "Select All Available Languages" checkbox shall be provided to check all languages, or perhaps all IndicTrans2-supported languages.
REQ-APP-073 ("Translate" Button & Dummy LLM Integration):
A "Translate" button.
On click, the frontend sends a request to a backend API (POST /api/app/notices/translate-notice) with: noticeId and an array of selected targetLanguageCodes (e.g., hin_Deva, tam_Taml).
Backend (Dummy) Logic:
Fetch the original notice content (either from Notice.NoticeBody if it was text, or by reading the file from Notice.FolderLocation).
For each targetLanguageCode in the request:
Simulate translation: Prepend "[DUMMY TRANSLATION to {lang_code}]: " to the original content.
Construct TranslatedFileName: [OriginalNoticeName]_[lang_code].[original_extension] (e.g., Website Privacy Policy_Org123_V1_hin_Deva.txt).
Save this dummy translated content as a new file in NoticesTranslated/[OrgID]/[TranslatedFileName].
The API responds with an array of objects, each containing { languageName, languageCode, translatedFilePath, translatedFileName } for successfully "translated" files.
REQ-APP-074 (Display Translated Notices):
Upon successful response from the translation API, the frontend shall dynamically render new "tiles" or cards for each language for which a translation was generated.
Each translated notice tile shall display: Language Name (e.g., "Hindi", "Tamil"), TranslatedFileName.
Download Options: Buttons to download the translated notice file (e.g., "Download PDF", "Download .txt"). These link to a backend file-serving endpoint.
REQ-APP-075 (Backend File Serving for Downloads):
Backend endpoints (GET /api/app/notices/download-original/:noticeId and GET /api/app/notices/download-translated?filePath=path_to_file) to securely serve the original and translated notice files for download.
3.6. External Facing - Create Request Page (DPDPA Sections 12, 13, 14)
This section defines the requirements for the publicly accessible webpage that Data Principals will use to submit Data Principal Requests (DPRs) and Grievances to a specific Organisation (Data Fiduciary) using ComplyArkWebApp.
3.6.1. Access and Organisation Identification
REQ-EXT-001: The Create Request Page shall be accessible via a unique, unguessable URL specific to each Organisation. This URL is generated by the System Admin and stored in Organisation.RequestPageURL (e.g., http://localhost:3000/request/{organisation_uuid}).
REQ-EXT-002: When a user accesses this URL, the frontend shall extract the organisation_uuid (or identifier).
REQ-EXT-003: The frontend shall make a backend API call (GET /api/external/organisation-info/{organisation_uuid}) to fetch and prominently display the BusinessName of the Organisation to assure the Data Principal they are on the correct page. If the identifier is invalid, an appropriate error page shall be shown.
3.6.2. Basic External User Authentication (Simplified for MVP)
REQ-EXT-004: Before accessing the request submission forms, the external user (Data Principal) shall encounter a simplified login/identification step. For MVP, this will be:
A form with "Email" and "Password" fields.
"Login" and "Register" (or "Proceed as Guest" if no persistence of external users is desired) buttons.
MVP Behavior: No actual user accounts are created or validated on the backend for these external requesters for the purpose of general platform login. The email provided will be captured with the request. The "password" field can be a dummy field for UI completeness, or a simple client-side check for being non-empty if "Register/Login" flow is simulated.
Alternatively, for extreme MVP simplicity, skip login and directly present request options, capturing PII in the request form itself. Clarification from initial discussion suggests a dummy login: this makes it feel more like a portal.
REQ-EXT-005: Placeholder UI elements for "Login with Google" or other social logins may be present but shall be non-functional for MVP, marked as "Coming Soon."
REQ-EXT-006: The purpose of this step in MVP is primarily to guide the user flow and capture an email consistently, rather than robust authentication.
3.6.3. Request Type Selection
REQ-EXT-007: After the (dummy) login/proceed step, the page shall clearly present two main selectable options to the Data Principal:
"Raise a Data Principal Request (Exercise Your Rights)"
"Log a Grievance / Complaint"
REQ-EXT-008: Selecting an option shall navigate the user to the respective form (DPR or Grievance).
3.6.4. Data Principal Request (DPR) Form & Submission
REQ-EXT-009 (Form Fields): If "Raise a Data Principal Request" is selected, a form shall be displayed with the following mandatory fields:
First Name (Text Input)
Last Name (Text Input)
Email Address (Email Input, pre-fill if captured at dummy login, validated format)
Phone Number (Text Input, optional but recommended)
Request Type (Dropdown, mandatory, options derived from DPDPA rights):
"Right to Access Information" (DPDPA Section 11)
"Right to Correction and Erasure of Personal Data" (DPDPA Section 12 - for MVP, this can be one type, with details in comment, or split if preferred: "Request Correction/Completion/Updating", "Request Erasure")
"Right to Nominate" (DPDPA Section 14)
Request Comment / Details (Multiline Textbox, mandatory – e.g., for correction, specify data to correct; for erasure, reason if any; for nomination, nominee details).
REQ-EXT-010 (Captcha - Desirable Post-MVP): A CAPTCHA mechanism to prevent bot submissions is desirable but deferred post-MVP for simplicity.
REQ-EXT-011 (Submission): A "Submit Request" button. On click:
Client-side validation of mandatory fields.
Data (including the organisation_uuid from URL and captured email) is sent via POST to a backend API endpoint (e.g., /api/external/dpr/submit).
REQ-EXT-012 (Backend DPR Processing): The backend API shall:
Validate inputs.
Identify the OrganisationID based on the organisation_uuid.
Create a new record in the DPRequests table with all submitted details.
Set CurrentStatusID to the ID corresponding to 'Submitted' (from RequestStatus table).
Set AssignedToUserID to the default OrgAdmin of that OrganisationID.
Calculate ExpectedCompletionDate = CreatedAt + SLA_days (for 'Submitted' status).
Create an initial record in DPRequestHistory table (e.g., "Request submitted by Data Principal via external portal", ChangedByUserID can be NULL or a system identifier).
Return a success response.
REQ-EXT-013 (Post-Submission UI): Upon successful submission:
The form fields shall be disabled.
A clear confirmation message shall be displayed to the Data Principal (e.g., "Your Data Principal Request has been successfully submitted to [Organisation Name]. You will be contacted via the email provided. Reference ID: [Optional, if backend returns a simple reference]").
Provide an option to submit another request or return to a neutral page.
3.6.5. Grievance Logging Form & Submission
REQ-EXT-014 (Form Fields): If "Log a Grievance / Complaint" is selected, a form shall be displayed with the following mandatory fields:
First Name (Text Input)
Last Name (Text Input)
Email Address (Email Input, pre-fill if captured at dummy login, validated format)
Phone Number (Text Input, optional but recommended)
Grievance Details / Comment (Multiline Textbox, mandatory).
REQ-EXT-015 (Submission): A "Submit Grievance" button. On click:
Client-side validation.
Data (including organisation_uuid and email) is sent via POST to a backend API endpoint (e.g., /api/external/grievances/submit).
REQ-EXT-016 (Backend Grievance Processing): The backend API shall:
Validate inputs.
Identify OrganisationID.
Create a new record in the Grievances table.
Set CurrentStatusID to 'Submitted'.
Set AssignedToUserID to default OrgAdmin.
Calculate ExpectedCompletionDate.
Create an initial record in GrievanceHistory.
Return a success response.
REQ-EXT-017 (Post-Submission UI): Upon successful submission:
The form fields shall be disabled.
A clear confirmation message (e.g., "Your Grievance has been successfully submitted to [Organisation Name]. You will be contacted via the email provided.").
3.6.6. General UI/UX for External Page
REQ-EXT-018: The external page shall have a clean, professional, and simple design, distinct from the main application's internal UI but trustworthy.
REQ-EXT-019: It shall be responsive and usable on common desktop and mobile browsers.
REQ-EXT-020: Clear error messages shall be displayed for any validation failures or submission errors.
3.7. Main Application - Data Principal Request (DPR) Module (DPDPA Sections 11, 12, 13, 14)
This module is used by internal Organisation Users (OrgAdmins and authorized OrgUsers) to manage and process Data Principal Requests received from external requesters via the "Create Request Page" or other channels (though MVP focuses on intake from the external page).
3.7.1. Access and Overview
REQ-APP-076: Authenticated Organisation Users shall be able to access the "Data Principal Requests" module via the left navigation panel.
REQ-APP-077: The module shall provide a consolidated view of all DPRs submitted to the user's Organisation.
3.7.2. DPR Listing Page
REQ-APP-078 (Status Tiles): At the top of the listing page, summary tiles shall display the count of DPRs for each active RequestStatus (e.g., "Submitted: 5", "InProgress: 3", "AwaitingInfo: 1").
These tiles shall be clickable, and clicking a tile shall filter the main DPR list below by that status.
REQ-APP-079 (Filtering Options): Comprehensive filtering options shall be available to refine the DPR list:
Status: Dropdown to select one or more RequestStatusID (fetched from RequestStatus table, including 'Closed' for historical searches). Default: Show all non-closed statuses.
Assigned To: Dropdown to select an AssignedToUserID (populated with users from the current Organisation). OrgAdmin sees all users; OrgUser might only see themselves or their team (for MVP, OrgUser sees requests assigned to them by default if not an Admin).
Request Type: Dropdown to select DPR RequestType (Access, Correction/Erasure, Nomination).
Creation Date Range: Date pickers for "From Date" and "To Date" based on DPRequests.CreatedAt.
A "Clear Filters" button shall reset all filters to default.
REQ-APP-080 (Search): A search bar shall allow searching across key fields like Requester Name, Email, or DPR ID (if displayed).
REQ-APP-081 (Data Table): The main content area shall display DPRs in a paginated and sortable data table (DataTableWrapper component).
Default Sort Order: Newest requests first (by DPRequests.CreatedAt descending).
Table Columns:
DPR ID (DPRequests.DPRequestID)
Requester Full Name (DPRequests.FirstName + DPRequests.LastName)
Requester Email (DPRequests.Email)
Request Type (DPRequests.RequestType)
Current Status (RequestStatus.RequestStatusName)
Assigned To (Full name of Users.FirstName + Users.LastName for DPRequests.AssignedToUserID)
Created Date (DPRequests.CreatedAt, formatted)
Expected Completion Date (DPRequests.ExpectedCompletionDate, formatted, perhaps highlighted if overdue)
Last Updated Date (DPRequests.LastUpdatedAt, formatted)
REQ-APP-082 (Row Interaction): Each row in the DPR table shall be clickable, navigating the user to the DPR Detail Page for that specific DPRequestID.
3.7.3. DPR Detail Page
REQ-APP-083 (Data Display): This page shall display all available details for a selected DPR. The DPRequestID should be prominent (e.g., in the page header). Information shall be grouped logically:
Requester Information (Mostly Read-Only):
Full Name, Email, Phone Number.
Request Details (Read-Only):
Request Type.
Request Comment / Details (original submission).
Created At timestamp.
Organisation ID it belongs to (for reference, though user is scoped).
Processing Information (Editable by authorized users):
Current Status (Dropdown, populated from RequestStatus table).
Assigned To (Dropdown, populated with users from the current Organisation. Editable by OrgAdmin or users with specific reassignment permission).
Expected Completion Date (Read-only, calculated based on CreatedAt and SLA of current/initial status).
Completed On Time? (Read-only flag, set upon closure).
Closure Comment (Multiline Textbox, becomes visible and mandatory if CurrentStatusID is changed to 'Closed').
Closed At timestamp (Read-only, set upon closure).
Last Updated At timestamp.
REQ-APP-084 (Update Actions): An "Update Request" or "Save Changes" button shall be present.
Clicking this button shall trigger a backend API call (PUT /api/app/dpr/{id}) to save any changes made to editable fields (Status, Assigned To, Closure Comment).
The backend shall validate permissions (e.g., only OrgAdmin can change AssignedToUserID; OrgUser with CanEdit can change CurrentStatusID for requests assigned to them or as per broader policy).
REQ-APP-085 (Status Change Logic):
When CurrentStatusID is changed to a status corresponding to 'Closed':
The "Closure Comment" field becomes mandatory.
ClosedAt timestamp is set by the backend.
CompletedOnTime is calculated by the backend (comparing ClosedAt with ExpectedCompletionDate).
Once closed, all fields (except potentially adding internal notes to history) should become read-only or an "Reopen" action (post-MVP) would be needed.
REQ-APP-086 (Expected Completion Date Recalculation - MVP Simplification):
For MVP, the ExpectedCompletionDate is calculated once based on the SLA of the initial 'Submitted' status and CreatedAt. It does not dynamically change with every internal status update unless a status like "AwaitingInfo" explicitly "pauses" the SLA clock (this pausing logic is complex and deferred post-MVP). The primary visual cue for urgency will be comparing this fixed ExpectedCompletionDate with the current date.
3.7.4. DPR History Trail
REQ-APP-087: The DPR Detail Page shall include a prominent section displaying the "History Trail" or "Audit Log" for the request.
REQ-APP-088: This trail shall list all entries from the DPRequestHistory table associated with the current DPRequestID, ordered chronologically (newest or oldest first, user preference TBD - newest first is common).
REQ-APP-089 (History Entry Display): Each history entry shall clearly display:
Timestamp (DPRequestHistory.ChangedAt)
User who made the change (Users.FirstName + Users.LastName for DPRequestHistory.ChangedByUserID, or "System/External" if applicable).
Action/Comment (DPRequestHistory.Comment - e.g., "Status changed from 'Submitted' to 'InProgress'", "Assigned to Kavita Rao", "Closure Comment: [comment text]").
If status changed: Old Status Name and New Status Name.
If assignment changed: Old Assignee Name and New Assignee Name.
REQ-APP-090 (System-Generated History): Every significant change made via the UI (status update, assignment change, closure) shall automatically generate a corresponding, descriptive entry in the DPRequestHistory table by the backend.
REQ-APP-090a (Manual History Notes - Optional MVP): Consideration for a simple "Add Internal Note" button on the detail page that allows users to add a textual comment to the history trail without changing status or assignment (useful for internal communication logging).
3.7.5. Backend API Support
REQ-APP-091: Backend APIs shall support:
GET /api/app/dpr: List DPRs with filtering, pagination, sorting.
GET /api/app/dpr/{id}: Fetch single DPR details and its full history.
PUT /api/app/dpr/{id}: Update DPR status, assignment, closure details, and automatically log history.
GET /api/app/organisations/{orgId}/users: (Already exists or part of user module) To populate "Assigned To" dropdowns.
GET /api/app/request-statuses: (Already exists or part of admin module, but make accessible to app) To populate "Status" dropdowns.
3.8. Main Application - Grievances Module (DPDPA Section 13)
This module is used by internal Organisation Users (OrgAdmins and authorized OrgUsers) to manage and process Grievances received from external requesters (Data Principals) via the "Create Request Page" or other channels (though MVP focuses on intake from the external page). It provides a mechanism for Data Fiduciaries to address complaints regarding their data processing activities.
3.8.1. Access and Overview
REQ-APP-092: Authenticated Organisation Users shall be able to access the "Grievances" module via the left navigation panel.
REQ-APP-093: The module shall provide a consolidated view of all Grievances submitted to the user's Organisation.
REQ-APP-094: The overall UI/UX, workflow, and functionalities within the Grievances module shall closely mirror those of the Data Principal Request (DPR) Module (Section 3.7) for consistency, with appropriate labeling changes (e.g., "Grievance ID" instead of "DPR ID", "Grievance Details" instead of "Request Details").
3.8.2. Grievance Listing Page
REQ-APP-095 (Status Tiles): At the top of the listing page, summary tiles shall display the count of Grievances for each active RequestStatus (e.g., "Submitted: X", "InProgress: Y"). These tiles shall be clickable to filter the Grievance list.
REQ-APP-096 (Filtering Options): Comprehensive filtering options shall be available:
Status: Dropdown to select one or more RequestStatusID. Default: Show all non-closed statuses.
Assigned To: Dropdown to select an AssignedToUserID.
Creation Date Range: Date pickers for Grievances.CreatedAt.
A "Clear Filters" button.
REQ-APP-097 (Search): A search bar shall allow searching across Requester Name, Email, or Grievance ID.
REQ-APP-098 (Data Table): Grievances shall be displayed in a paginated and sortable data table.
Default Sort Order: Newest grievances first (by Grievances.CreatedAt descending).
Table Columns:
Grievance ID (Grievances.GrievanceID)
Requester Full Name (Grievances.FirstName + Grievances.LastName)
Requester Email (Grievances.Email)
Current Status (RequestStatus.RequestStatusName)
Assigned To (Full name of Users.FirstName + Users.LastName for Grievances.AssignedToUserID)
Created Date (Grievances.CreatedAt, formatted)
Expected Completion Date (Grievances.ExpectedCompletionDate, formatted, perhaps highlighted if overdue)
Last Updated Date (Grievances.LastUpdatedAt, formatted)
REQ-APP-099 (Row Interaction): Each row in the Grievance table shall be clickable, navigating to the Grievance Detail Page.
3.8.3. Grievance Detail Page
REQ-APP-100 (Data Display): This page shall display all details for a selected Grievance. GrievanceID prominent.
Requester Information (Read-Only): Full Name, Email, Phone Number.
Grievance Details (Read-Only): Original Grievance Comment, Created At.
Processing Information (Editable by authorized users):
Current Status (Dropdown).
Assigned To (Dropdown, editable by OrgAdmin).
Expected Completion Date (Read-only).
Completed On Time? (Read-only).
Closure Comment (Multiline Textbox, visible/mandatory for 'Closed' status).
Closed At timestamp (Read-only).
Last Updated At timestamp.
REQ-APP-101 (Update Actions): An "Update Grievance" or "Save Changes" button triggering PUT /api/app/grievances/{id}. Backend validates permissions.
REQ-APP-102 (Status Change Logic): Identical to DPR Module (REQ-APP-085):
'Closed' status requires "Closure Comment", sets ClosedAt, calculates CompletedOnTime.
Once closed, fields become read-only.
REQ-APP-103 (Expected Completion Date Recalculation - MVP Simplification): Identical to DPR Module (REQ-APP-086) - fixed based on initial 'Submitted' SLA.
3.8.4. Grievance History Trail
REQ-APP-104: The Grievance Detail Page shall include a "History Trail" section.
REQ-APP-105: Lists entries from GrievanceHistory table, ordered chronologically.
REQ-APP-106 (History Entry Display): Timestamp, User who made change, Action/Comment, Old/New Status, Old/New Assignee.
REQ-APP-107 (System-Generated History): Significant changes auto-generate GrievanceHistory entries.
REQ-APP-107a (Manual History Notes - Optional MVP): Option to add internal notes to the history.
3.8.5. Backend API Support
REQ-APP-108: Backend APIs shall support:
GET /api/app/grievances: List Grievances with filtering, pagination, sorting.
GET /api/app/grievances/{id}: Fetch single Grievance details and its full history.
PUT /api/app/grievances/{id}: Update Grievance status, assignment, closure details, and log history.
(Shared APIs for users and request statuses as used by DPR module).
3.9. Main Application - Record of Processing Activities (RoPA) & Data Processing Agreement (DPA) Management Support (DPDPA Section 8 accountability, specifically 8(1), 8(3), 8(4))
This module assists Data Fiduciaries in creating and maintaining their Record of Processing Activities (RoPA) as an essential part of their accountability under the DPDPA. For MVP, RoPA data entry is manual, leveraging information architecture similar to the Notice Questionnaire and providing clear visualization. It also provides a way to manage (store) Data Processing Agreements (DPAs).
3.9.1. RoPA - Purpose and Access
REQ-APP-109: Authenticated Organisation Users shall be able to access a "Record of Processing Activities (RoPA)" or "Data Inventory" module via the left navigation panel.
REQ-APP-110: The purpose of this module is to allow the Data Fiduciary to document and maintain a comprehensive record of all its personal data processing activities.
3.9.2. RoPA - Data Input and Management (Manual)
REQ-APP-111 (Structure Leverages Notice Questionnaire Data): The system shall provide an interface for manually inputting and managing RoPA entries. Much of the information required for a RoPA aligns with the data collected in the Notice Module's Questionnaire (Section 3.5.1).
The RoPA input interface should be structured similarly to the Notice Questionnaire, with clear sections for each processing activity.
Instead of generating a single notice, this module will allow for creating and managing multiple distinct processing activity records.
REQ-APP-112 (Creating a Processing Activity Record): Users shall be able to "Add New Processing Activity." Each record shall capture at least the following DPDPA-relevant details (many map from Notice Questionnaire fields):
a. Name/Description of Processing Activity: (e.g., "Customer Order Processing," "Employee Payroll," "Website Analytics," "Marketing Email Campaigns").
b. Purpose(s) of Processing: Clear, specific, and lawful purposes for this activity.
c. Categories of Data Principals: (e.g., Customers, Employees, Website Visitors).
d. Categories of Personal Data Processed for this Activity: (Detailed list, e.g., Name, Email, Address for "Customer Order Processing"; Bank Account, Tax ID for "Employee Payroll").
e. Lawful Basis for Processing: (Consent, or specific Legitimate Uses under DPDPA Section 7). If consent, reference how/where consent is obtained.
f. Data of Children / Persons with Disabilities (if applicable to this activity): Documentation of specific measures for consent and protection as per DPDPA Section 9.
g. Data Fiduciary Details: (Name and contact details of the Data Fiduciary – pre-filled from Org profile).
h. Data Protection Officer (DPO) / Contact Person: (Contact details, if appointed).
i. Data Processors Involved (DPDPA Section 8(3)):
Repeatable section: [Name of Data Processor], [Address/Contact], [Service Provided], [Link/Reference to DPA stored in Compliance Docs Module - REQ-APP-114].
j. Third-Party Data Sharing (other than Processors): If data is shared with other Data Fiduciaries for this activity: [Name of Recipient Fiduciary], [Categories of Data Shared], [Purpose of Sharing], [Lawful Basis for Sharing].
k. Cross-Border Data Transfers (DPDPA Section 16) (if applicable to this activity): [Country of Transfer], [Data Categories Transferred], [Safeguards Implemented].
l. Data Retention Period for this Activity: Specific retention period or criteria.
m. General Description of Security Measures (Technical & Organisational - DPDPA Section 8(5)) for this activity.
n. Algorithmic Decision-Making/Profiling (if applicable to this activity): Description of any automated decision-making with legal or significant effect, and measures for fairness/due diligence (as per your clarification).
o. Use of Tokenization (if applicable to this activity): Description of tokenization practices for data involved in this activity.
REQ-APP-113 (Editing and Deleting Activity Records): Users shall be able to edit existing processing activity records and delete them (with confirmation).
3.9.3. RoPA - Visualization, Viewing, and Export
REQ-APP-114: The system shall provide a clear, structured, and easily understandable interface to view all recorded processing activities.
This could be a master list (data table) of all processing activities, where clicking an activity shows its full details.
Columns in master list: Activity Name, Main Purpose(s), Categories of DPs, Key Data Categories, Lawful Basis.
REQ-APP-115 (Visualization - Emphasis): While detailed data mapping visualizations are post-MVP, the RoPA viewing interface must be more than just raw data fields. It should aim for:
Clear headings for each RoPA element (a-o from REQ-APP-112).
Well-formatted display of lists (e.g., Data Processors, Data Categories).
Easy readability.
REQ-APP-116 (Filtering and Searching RoPA): Users should be able to search RoPA records (e.g., by activity name, purpose, data category involved) and potentially filter (e.g., by lawful basis, activities involving cross-border transfer).
REQ-APP-117 (Export RoPA): Users shall be able to export the entire RoPA or selected activity records in standard formats:
CSV: Mandatory for data manipulation.
PDF: Desirable for printable, well-formatted record-keeping. The PDF should present the data in a clean, report-like structure.
3.9.4. Data Processing Agreement (DPA) Management Support (Fiduciary's Perspective - DPDPA Section 8(3))
REQ-APP-118 (No DPA Generation for MVP): The ComplyArkWebApp MVP will not generate DPA documents.
REQ-APP-119 (Storage of Executed DPAs): Data Fiduciaries shall use the Compliance Documentation Module (Section 3.10) to upload and store their executed DPAs with their Data Processors.
REQ-APP-120 (Linking DPAs in RoPA): When documenting a "Processing Activity" in the RoPA (REQ-APP-112.i), if a Data Processor is involved, the user should be able to:
Enter the name of the Data Processor.
Provide a reference or (if technically feasible for MVP, a direct link) to the corresponding DPA document stored in the Compliance Documentation Module. This might be a manual text field for "DPA Document Reference/Location" for MVP.
REQ-APP-121 (DPA Checklist - Optional MVP Enhancement):
Consider providing a simple, non-exhaustive checklist within the RoPA section for "Data Processors Involved" or as a separate informational resource. This checklist would list key clauses/points Data Fiduciaries should typically ensure are covered in their DPAs with Data Processors (as per DPDPA Section 8(3) and good practice, e.g., scope, security, breach notification, audit rights, sub-processor restrictions). This is for guidance, not a legal tool.
3.9.5. Backend API Support
REQ-APP-122: Backend APIs shall support:
POST /api/app/ropa/activities: Create a new RoPA processing activity record.
GET /api/app/ropa/activities: List all RoPA activity records for the organisation (with filtering/search).
GET /api/app/ropa/activities/{activityId}: Get details of a specific RoPA activity.
PUT /api/app/ropa/activities/{activityId}: Update a RoPA activity record.
DELETE /api/app/ropa/activities/{activityId}: Delete a RoPA activity record.
Endpoints for exporting RoPA data (e.g., generating CSV content).
3.10. Main Application - Compliance Documentation Module (DPDPA Section 8 accountability)
This module provides a centralized, secure repository for Organisation Users to store, organize, and manage all their DPDPA compliance-related documents.
3.10.1. Purpose and Access
REQ-APP-123: Authenticated Organisation Users shall be able to access the "Compliance Documentation" (or "Document Library," "Records Management") module via the left navigation panel.
REQ-APP-124: The module serves as a digital filing cabinet for the Organisation's DPDPA records, policies, notices, agreements, and other relevant compliance artifacts. All documents are scoped to the user's Organisation.
3.10.2. Folder Management
REQ-APP-125 (Create Folder): Users shall be able to create new folders within the current directory path to organize documents.
A "New Folder" button shall prompt for a folder name.
Folder names should adhere to typical file system naming conventions (validated by backend/frontend).
Folders can be nested to create a hierarchical structure.
REQ-APP-126 (View Folders): Folders shall be visually distinct from files in the listing (e.g., using folder icons).
REQ-APP-127 (Navigate Folders): Clicking a folder name shall navigate the user into that folder, updating the view to show its contents and updating the breadcrumb trail.
REQ-APP-128 (Rename Folder - Desirable Post-MVP): For MVP, renaming folders might be deferred. If included, users can rename folders they created or have permission for.
REQ-APP-129 (Delete Folder): Users shall be able to delete folders (with a confirmation dialog: "Are you sure you want to delete the folder '[FolderName]' and all its contents? This action cannot be undone.").
Deleting a folder shall recursively delete all sub-folders and files within it from the file system and their corresponding metadata from OrganisationDocuments table.
Permissions for deletion should be considered (e.g., only creator or OrgAdmin).
3.10.3. File Management
REQ-APP-130 (Upload Files):
An "Upload File(s)" button shall allow users to select one or more files from their local system.
Supported file types for MVP should include common document formats: PDF, DOCX, XLSX, TXT, PPTX, JPG, PNG. A configurable list of allowed extensions should be maintained.
Upon successful upload, files are stored in the Organisation's scoped directory on the server (e.g., OrganisationSpecificDocs/OrgID/current_path/).
Metadata for each uploaded file (OrgID, FileName, FilePath (relative to org root), FileType, UploadedByUserID, UploadedAt, optional Description) shall be saved to the OrganisationDocuments table.
Users may be prompted to add an optional description during/after upload.
REQ-APP-131 (View Files): Files shall be listed alongside folders, with distinct icons based on file type (if feasible).
REQ-APP-132 (Download Files): Users shall be able to download any file listed. Clicking a file name or a dedicated download icon shall initiate the file download.
REQ-APP-133 (Rename File - Desirable Post-MVP): For MVP, renaming files might be deferred. If included, users can rename files, which should update both the file system name and the OrganisationDocuments.FileName/FilePath.
REQ-APP-134 (Delete Files): Users shall be able to delete individual files (with a confirmation dialog: "Are you sure you want to delete '[FileName]'?").
Deletion removes the file from the file system and its metadata from OrganisationDocuments.
Permissions for deletion should be considered.
REQ-APP-135 (File Versioning - Post-MVP): Version control for uploaded documents is out of scope for MVP. Each upload of a file with the same name might overwrite or be saved with a suffix (user choice or system default TBD if implemented later). For MVP, assume overwrite or encourage unique naming.
3.10.4. Document Listing and Navigation
REQ-APP-136 (Display): The main view shall list files and folders within the current directory path.
List View Columns: Icon (type), Name, Size, Last Modified (from file system or UploadedAt from DB), Uploaded By (User's Name), Actions (Download, Delete, etc.).
Grid view with larger icons is an alternative display option (post-MVP).
REQ-APP-137 (Breadcrumb Navigation): A breadcrumb trail shall always be visible, showing the current path within the Organisation's document root (e.g., "Compliance Docs > Policies > 2024"). Each part of the breadcrumb shall be clickable to navigate to that parent directory.
REQ-APP-138 (Search - Basic for MVP): A basic search functionality to find files/folders by name within the current directory and its subdirectories (recursive search is more advanced).
REQ-APP-139 (Sorting): Users shall be able to sort the file/folder list by Name, Size, Last Modified date.
3.10.5. Integration & Quick Links (Linking to other module outputs)
REQ-APP-140: The Compliance Documentation module should provide easy access or views to documents generated by other modules, even if their primary storage is elsewhere. This promotes it as the central document hub.
a. Generated Notices: A dedicated section or smart folder (virtual view) labeled "Generated Notices" that lists all notices created via the Notice Module (Tab 2 output, from GeneratedNotices/OrgID/). Users can view metadata and download these notices. These are typically read-only from this view (managed via Notice Module).
b. Translated Notices: Similar section/smart folder for "Translated Notices" (from NoticesTranslated/OrgID/).
c. Notice Templates (Informational): A section/smart folder "Available Organisation Templates" providing a read-only view/download access to the Notice Templates relevant to the Organisation's industry (from TemplateRepo/ but filtered). These are managed by System Admin.
REQ-APP-141: DPAs uploaded here can be referenced from the RoPA module (as per REQ-APP-120).
3.10.6. Backend API Support
REQ-APP-142: Backend APIs shall handle:
GET /api/app/documents?path=...: List files and folders in a given path for the org.
POST /api/app/documents/create-folder: Create a new folder.
POST /api/app/documents/upload?path=...: Upload files, save to file system, and store metadata in OrganisationDocuments.
DELETE /api/app/documents?itemPath=...&itemType=...: Delete file or folder.
GET /api/app/documents/download?filePath=...: Serve a file for download.
(APIs to list generated/translated notices and templates might leverage existing notice/template service endpoints with appropriate filtering for these quick link views).
3.11. Main Application - Task Management Module (Basic)
This module provides a simple way for Organisation Users (primarily OrgAdmins, but tasks can be assigned to OrgUsers) to create, assign, and track compliance-related tasks. It's a general-purpose tool to help manage activities not explicitly covered by other automated workflows in the MVP.
3.11.1. Purpose and Access
REQ-APP-143: Authenticated Organisation Users shall be able to access a "Tasks" or "Compliance Tasks" module via the left navigation panel (visibility might be OrgAdmin-centric or open to all users to see tasks assigned to them).
REQ-APP-144: The purpose is to provide a lightweight task management capability to help Organisations track manual compliance actions, reminders, and follow-ups.
3.11.2. Task Creation
REQ-APP-145: Users with permission (e.g., OrgAdmin or users with a "Create Task" permission if more granular control is added later) shall be able to create new tasks.
REQ-APP-146 (Task Fields): A "Create New Task" form (modal or dedicated page) shall capture:
Task Title / Name: (Text Input, mandatory, concise description of the task).
Description: (Multiline Textbox, optional, for more details, steps, or context).
Assigned To: (Dropdown, populated with users from the current Organisation. Can be assigned to self or others). Defaults to creator or unassigned.
Due Date: (Date Picker, optional).
Priority: (Dropdown, optional, e.g., High, Medium, Low).
Status: (Dropdown, defaults to 'To Do' or 'Open'. Other options: 'InProgress', 'Completed', 'OnHold').
Related To (Optional Contextual Linking - Basic for MVP):
(Text Input/Dropdown - Post MVP idea) Link to a specific Notice ID, DPR ID, Grievance ID, or Document Name from Compliance Docs. For MVP, this might just be a free-text field for "Reference".
REQ-APP-147 (Task Creation - Checklist Items):
The module should facilitate the creation of pre-defined checklist items, such as "Perform Algorithmic Verification Due Diligence" (as per DPDPA Section 10 for SDFs, but good practice for others too) or "Annual Privacy Policy Review." The OrgAdmin could manually create these as recurring tasks or one-off tasks. No automated suggestion of these tasks in MVP.
3.11.3. Task Listing and Viewing
REQ-APP-148: A main task listing page shall display tasks relevant to the user:
OrgAdmin may see all tasks for the Organisation.
OrgUser primarily sees tasks assigned to them, or tasks they created.
REQ-APP-149 (Filtering and Sorting): The task list shall be filterable by:
Status (To Do, InProgress, Completed, etc.)
Assigned To
Due Date (e.g., Overdue, Today, Next 7 days)
Priority
The list should be sortable by Title, Due Date, Priority, Status.
REQ-APP-150 (Data Table Display): Tasks shall be displayed in a data table with columns such as:
Task Title
Assigned To
Due Date (highlighted if overdue)
Priority
Status
Created Date
Actions (Edit, Mark as Complete, Delete)
REQ-APP-151 (Task Detail View - Basic for MVP): Clicking a task title might expand it in place or open a simple modal showing full Description and all fields. A dedicated detail page is not strictly necessary for MVP if all info fits well.
3.11.4. Task Updates and Management
REQ-APP-152 (Edit Task): Users with permission (creator or assignee, or OrgAdmin) shall be able to edit task details (Title, Description, Assigned To, Due Date, Priority, Status).
REQ-APP-153 (Status Updates): Users shall be able to easily update the status of a task (e.g., from 'To Do' to 'InProgress', or directly to 'Completed').
A "Mark as Complete" quick action button might be available in the list view.
REQ-APP-154 (Comments/Activity Log - Post-MVP): A detailed activity log or comment thread per task is out of scope for MVP but a desirable future enhancement. For MVP, updates are reflected in the main fields.
REQ-APP-155 (Delete Task): Users with permission shall be able to delete tasks (with confirmation).
3.11.5. Notifications (Basic / Placeholder for MVP)
REQ-APP-156: While full-fledged email/in-app notifications are post-MVP, the system should consider:
Visual cues on the Dashboard for overdue tasks or tasks newly assigned to the logged-in user.
(Future: Email reminders for upcoming due dates or new assignments).
3.11.6. Backend API Support (No dedicated Task table planned for MVP - simpler approach)
MVP Simplification: To avoid creating many new tables for a basic task manager, for MVP, tasks could potentially be managed using a flexible field within an existing relevant entity (e.g., a JSON field in DPRequests or Grievances for tasks related to them) or, if truly general, a very simple GeneralTasks table linked to OrganisationID.
If a GeneralTasks table is created for MVP:
TaskID (PK)
OrganisationID (FK)
Title (NVARCHAR, NOT NULL)
Description (NVARCHAR)
AssignedToUserID (FK to Users, NULLABLE)
DueDate (DATETIME, NULLABLE)
Priority (NVARCHAR, e.g., 'High', 'Medium', 'Low', NULLABLE)
Status (NVARCHAR, e.g., 'ToDo', 'InProgress', 'Completed', NOT NULL)
CreatedByUserID (FK to Users)
CreatedAt (DATETIME)
UpdatedAt (DATETIME)
REQ-APP-157: Backend APIs would then support CRUD operations on this GeneralTasks table, scoped by OrganisationID.
POST /api/app/tasks
GET /api/app/tasks (with filters)
PUT /api/app/tasks/{taskId}
DELETE /api/app/tasks/{taskId}
4. Data Requirements
This section outlines the data that ComplyArkWebApp MVP will handle, including its storage, privacy considerations from the platform's perspective, and basic backup/recovery strategies.
4.1. Database Schema
REQ-DATA-001: All structured application data shall be stored in a relational database, specifically MS SQL Server, named complyarkDB.
REQ-DATA-002: The database schema shall be designed as per the detailed CREATE TABLE statements provided and agreed upon in the "Database Schema (MS SQL)" section of our earlier discussions (Phase 1, M1.1). This includes tables for:
Core Entities: Industry, Organisation, Users, Template, RequestStatus.
Notice Module: Notice.
DPR Module: DPRequests, DPRequestHistory.
Grievance Module: Grievances, GrievanceHistory.
Compliance Documentation: OrganisationDocuments (for metadata of uploaded files).
Task Management (if implemented with a dedicated table for MVP): GeneralTasks (or similar, as discussed in REQ-APP-157).
REQ-DATA-003: Primary keys shall be auto-incrementing integers (e.g., INT IDENTITY(1,1)). Foreign key constraints shall be established to maintain referential integrity between tables.
REQ-DATA-004: Appropriate data types, nullability constraints, and unique constraints shall be applied to table columns as defined in the schema.
REQ-DATA-005: Timestamps (CreatedAt, UpdatedAt) shall be consistently used for relevant tables to track record creation and modification times.
4.2. File Storage
REQ-DATA-006: Non-structured data, specifically uploaded files, shall be stored in the server's local file system within designated, organized directories. For MVP, cloud-based object storage (e.g., AWS S3, Azure Blob Storage) is out of scope.
REQ-DATA-007 (Designated Folders):
TemplateRepo/: For Notice Template files uploaded by System Admins (as per REQ-ADM-022).
GeneratedNotices/[OrganisationID]/: For notice documents generated by Organisation Users via the Notice Module (Tab 2 output, as per REQ-APP-069). Sub-folders per OrganisationID are crucial for data segregation.
NoticesTranslated/[OrganisationID]/: For (dummy) translated notice documents (as per REQ-APP-073). Sub-folders per OrganisationID.
OrganisationSpecificDocs/[OrganisationID]/: Root directory for files uploaded by Organisation Users via the Compliance Documentation module (as per REQ-APP-130). This will contain user-created sub-folder structures.
REQ-DATA-008: File paths stored in the database (e.g., Template.TemplatePath, Notice.FolderLocation, OrganisationDocuments.FilePath) shall be relative to a configurable application root or absolute paths managed consistently by the backend. For MVP, paths relative to the application's file storage root are preferred.
REQ-DATA-009: The backend application must have necessary read/write permissions to these file system directories.
4.3. Data Privacy (Platform's Handling of Client and End-User Data)
REQ-DATA-010 (Client Organisation Data): ComplyArkWebApp will store administrative and configuration data about its client Organisations (Data Fiduciaries), such as business details, contact information, user accounts for the platform, and the compliance-related documentation they create or upload (e.g., RoPA content, notices, uploaded policies, DPR/Grievance case data). This data is essential for the platform's operation.
REQ-DATA-011 (Data Principal's Personal Data - Limited Scope):
ComplyArkWebApp is not intended to directly access, process, or store the raw, extensive personal data lakes or operational databases of its client Organisations' Data Principals.
The platform will process personal data of Data Principals only to the extent that it is submitted to the platform through specific channels:
Via the external "Create Request Page" when Data Principals submit DPRs or Grievances (e.g., name, email, phone, details of their request/grievance).
If explicitly entered by Organisation Users into the Notice Questionnaire or RoPA fields (e.g., describing categories of data, not the actual data itself unless an example is provided by the Fiduciary user).
If contained within documents uploaded by Organisation Users into the Compliance Documentation module.
REQ-DATA-012 (Platform as Data Processor): In the context of handling the personal data submitted through DPR/Grievance forms, or any PII within uploaded documents by the Fiduciary, ComplyArk (the company) acts as a Data Processor on behalf of the Data Fiduciary (the client Organisation). ComplyArkWebApp (the platform) facilitates this processing.
REQ-DATA-013 (Data Segregation): All data related to a specific client Organisation (database records linked by OrganisationID, files stored in OrganisationID-scoped folders) must be strictly segregated and inaccessible to other client Organisations.
4.4. Data Backup & Recovery (MVP Strategy)
REQ-DATA-014 (Database Backup):
For MVP development and local/pilot deployment, regular manual or scheduled (e.g., daily SQL Server Agent job) backups of the complyarkDB database shall be performed.
Backup files shall be stored securely in a separate location from the primary database server.
A documented procedure for restoring the database from a backup should exist.
REQ-DATA-015 (File System Backup):
Regular manual or scripted backups of the file storage directories (TemplateRepo, GeneratedNotices, NoticesTranslated, OrganisationSpecificDocs) shall be performed.
These backups should also be stored in a separate, secure location.
A documented procedure for restoring files/directories should exist.
REQ-DATA-016 (Recovery Point Objective (RPO) & Recovery Time Objective (RTO) - MVP Context):
For MVP pilot, RPO (maximum acceptable data loss) might be ~24 hours (based on daily backups).
RTO (maximum time to restore service) will depend on manual restoration procedures and could be several hours.
These are MVP-level objectives; production systems would require more stringent RPO/RTO and automated solutions.
4.5. Data Retention (Platform Data - Post-MVP Consideration)
REQ-DATA-017: The policy for retention of a client Organisation's data on the ComplyArkWebApp platform after their subscription ends or their account is terminated (including how long data is kept before permanent deletion) is a critical policy decision but is considered post-MVP for detailed implementation. For MVP, data remains until manually purged by a System Admin if an org is offboarded.
5. Non-Functional Requirements (NFRs)
This section defines the quality attributes, operational characteristics, and constraints of the ComplyArkWebApp MVP. These are crucial for ensuring the system is usable, reliable, secure enough for MVP, and maintainable.
5.1. Usability
NFR-001 (Intuitive Interface): The User Interface (UI) across all modules (System Admin, Main Application, External Request Page) shall be intuitive, logical, and easy to navigate for the defined target users with standard computer literacy. Minimal training should be required after initial onboarding/familiarization.
NFR-002 (Clarity of Terminology & Guidance):
Terminology used within the application shall align with the DPDPA where applicable and be presented in clear, plain English.
Where legal or technical terms are unavoidable, inline help, tooltips (MUI Tooltip), or info icons providing brief explanations should be considered to assist non-expert users.
NFR-003 (Forms and Data Entry):
All data entry forms shall have clear labels for each field.
Mandatory fields shall be clearly indicated (e.g., with an asterisk "*").
Client-side input validation shall be implemented for common formats (e.g., email, phone numbers, dates) to provide immediate feedback.
User-friendly error messages shall be displayed next to fields with invalid input or upon form submission failure.
NFR-004 (Visual Design & Interaction Consistency):
A consistent visual design (leveraging Material UI theming, typography, color palette, iconography) shall be applied throughout the application.
Interaction patterns (e.g., for buttons, modals, data tables, navigation) shall be consistent to provide a predictable user experience (UX).
The application shall provide clear visual feedback for user actions (e.g., loading indicators for API calls, success/error messages via snackbars/alerts).
NFR-004a (Readability): Font sizes, contrasts, and layout shall ensure good readability.
5.2. Performance & Scalability (MVP Focus)
NFR-005 (Page Load Times): Average load times for frequently accessed pages (e.g., Dashboard, Module Listing Pages) shall be under 3-4 seconds on a typical broadband internet connection and standard desktop hardware.
NFR-006 (API Response Times): Backend API response times for common read operations (e.g., fetching lists for DataTables, fetching detail views) should ideally be under 2 seconds for typical MVP data volumes. Write operations (create, update) should also complete promptly.
NFR-007 (File Operations): Uploading and downloading files up to 5MB (typical document sizes) shall be responsive, without causing the UI to freeze. Progress indicators for larger uploads/downloads are desirable (post-MVP if complex).
NFR-008 (DataTable Performance): DataTables should render smoothly and remain interactive (sorting, pagination) with up to a few hundred rows of data (typical for MVP Organisation scope). Pagination shall be used for larger datasets.
NFR-017 (Scalability Foundation - Backend): The backend code shall be structured modularly (services, controllers, routes) to facilitate easier identification of bottlenecks and future scaling of specific components if needed post-MVP.
NFR-018 (Scalability Foundation - Database): Database queries shall be written efficiently, utilizing appropriate indexing for frequently queried columns (e.g., foreign keys, status fields, date fields used in filters). Avoid N+1 query problems.
5.3. Reliability & Availability (MVP Focus)
NFR-009 (Stability): The MVP application shall be stable during normal usage by pilot users, without frequent unexpected crashes, errors, or freezes.
NFR-010 (Data Integrity): The system must ensure data integrity. Data saved by users shall be accurately persisted in the database and file system. Foreign key constraints and proper transaction management (for multi-step DB operations) will support this.
NFR-011 (Core Function Reliability): Core functionalities as defined in Section 3 (e.g., login, notice generation workflow, DPR/Grievance submission and processing, document upload) must operate reliably and produce expected outcomes.
NFR-011a (Availability - Pilot): For the pilot phase, the application should aim for high availability during agreed-upon testing/business hours. Mechanisms for monitoring basic application health (e.g., server responsiveness) should be considered even for MVP.
5.4. Security (MVP Basics)
NFR-012 (HTTPS): All data transmitted between the client (browser) and the backend server shall be encrypted using HTTPS.
NFR-013 (Password Security): User passwords shall be securely hashed using a strong algorithm (e.g., bcrypt) before being stored in the Users table. Passwords shall never be stored in plain text.
NFR-014 (Protection Against Common Vulnerabilities):
Input Sanitization: User-supplied input displayed back in the UI or used in constructing file paths must be sanitized to prevent Cross-Site Scripting (XSS) vulnerabilities.
SQL Injection Prevention: Database queries shall be constructed using parameterized queries or an ORM that inherently protects against SQL injection. Dynamic SQL construction from user input must be avoided.
Secure File Uploads: Validate file types and potentially scan uploaded files (post-MVP for scanning). Do not execute uploaded files or serve them from directories with execute permissions.
NFR-015 (Session Management):
JWTs used for session management shall be securely generated, transmitted (HTTPS only), and have reasonable expiration times.
Consider mechanisms for token invalidation on logout (client-side removal is standard, backend blacklisting is more robust but post-MVP).
JWTs should be stored securely on the client (e.g., HttpOnly cookies if possible for web, or secure storage for other client types – for React web, often localStorage with awareness of XSS risks).
NFR-016 (Authorization/RBAC Enforcement): All sensitive backend API endpoints must rigorously enforce role-based access control and data scoping (e.g., an OrgUser from OrgA cannot access data from OrgB) based on the authenticated user's JWT claims. Do not rely solely on frontend UI hiding elements.
NFR-016a (Dependency Security): Keep third-party libraries (both frontend and backend) reasonably up-to-date and be aware of known vulnerabilities (e.g., using npm audit).
5.5. Maintainability
NFR-019 (Code Quality & Organization):
Code (both frontend and backend) shall be well-organized into logical modules, components, services, etc., following the agreed-upon project structure.
Consistent coding standards and naming conventions shall be followed.
Code shall include meaningful inline comments for complex logic or non-obvious decisions.
Avoid "magic numbers" or hardcoded strings; use constants or configuration variables where appropriate.
NFR-020 (Configuration Management): Sensitive configurations (database credentials, JWT secrets, API keys for external services) shall be managed externally from the codebase (e.g., using .env files) and not committed to version control.
NFR-020a (Modularity): Design components and services to be as modular and reusable as possible to simplify future enhancements and maintenance.
5.6. Browser Compatibility
NFR-021: The ComplyArkWebApp frontend shall be tested and function correctly on the latest stable versions of the following modern web browsers:
Google Chrome
Mozilla Firefox
Microsoft Edge
Apple Safari (on macOS)
Basic responsive design should ensure usability on common desktop screen resolutions. Mobile-specific optimization is desirable but secondary for this B2B MVP.
5.7. Accessibility (Basic Considerations for MVP)
NFR-022: Employ semantic HTML5 elements where appropriate to improve a
ccessibility.
NFR-023: Ensure basic keyboard navigation is possible for primary interactive elements (forms, buttons, links).
NFR-024: Ensure sufficient color contrast for text and important UI elements to meet basic readability standards (e.g., WCAG AA contrast ratios as a guideline).
NFR-025: Provide alt text for meaningful images. For decorative images, use empty alt="".
6. External Interfaces / Integrations
This section describes any external systems or services that ComplyArkWebApp MVP will interact with, the nature of these interactions, and the data exchanged. For the MVP, most external integrations are either placeholders or very basic.
6.1. Translation Service (e.g., IndicTrans2 - Placeholder/Dummy for MVP)
REQ-INT-001 (Purpose): To provide translation capabilities for generated notices into the 22 official Indian languages, as required by DPDPA Section 5(3) and detailed in the Notice Module (Section 3.5.3).
REQ-INT-002 (MVP Implementation - Dummy):
The ComplyArkWebApp backend shall include a dummy/simulated translation service endpoint (POST /api/app/notices/translate-notice).
This dummy service will not make actual calls to an external LLM like IndicTrans2 during the MVP phase.
It will receive the original notice content (or a reference to it) and a list of target language codes.
It will simulate translation by, for example, prepending a language identifier to the original text (e.g., "[DUMMY TRANSLATION to hin_Deva]: {original_text}").
It will save these "translated" outputs as separate files in the designated NoticesTranslated/[OrgID]/ directory.
REQ-INT-003 (Data Exchanged with Dummy Service - Internal Backend Call):
Input to Dummy Service:
noticeId: Identifier of the original notice to be "translated."
originalNoticeContent: The actual text content of the notice.
targetLanguageCodes: An array of language codes (e.g., ["hin_Deva", "tam_Taml"]).
Output from Dummy Service (to frontend via API response):
An array of objects, each representing a "translated" file:
languageName: (e.g., "Hindi", "Tamil")
languageCode: (e.g., "hin_Deva")
translatedFilePath: Path to the saved dummy translated file.
translatedFileName: Name of the saved dummy translated file.
REQ-INT-004 (Future Real Integration - API Contract Consideration):
The design of the dummy service endpoint and its request/response structure should ideally mimic what a real integration with a service like IndicTrans2 might look like to minimize rework later.
This includes considering authentication mechanisms (API keys), rate limiting, error handling, and the format of text submission and retrieval that a real LLM API would expect. This is for design foresight, not MVP implementation of these advanced aspects.
6.2. Email Service (Placeholder/Dummy for MVP)
REQ-INT-005 (Purpose): Primarily for user-related notifications such as password reset links. Future uses could include task notifications or system alerts.
REQ-INT-006 (MVP Implementation - Dummy):
The ComplyArkWebApp backend will not integrate with a live external email sending service (e.g., SendGrid, AWS SES, Mailgun) for the MVP.
When an email notification is supposed to be sent (e.g., for "Forgot Password" REQ-APP-004):
The backend will generate the content of the email (including any tokens or links).
Instead of sending it, the backend will log the full email content (recipient, subject, body) to the server console.
For the "Forgot Password" flow, the reset token/link logged to the console can be manually copied and used in the browser to simulate the user clicking the link from an email.
REQ-INT-007 (Data Exchanged - Internal Logging):
Recipient Email Address
Email Subject
Email Body (HTML or plain text, including any dynamic content like reset tokens/links)
REQ-INT-008 (Future Real Integration - Service Abstraction):
It is recommended to abstract the email sending logic in the backend into a dedicated service module. This module would contain the dummy logging logic for MVP. Post-MVP, this module can be updated to integrate with a real email service without requiring widespread changes in other parts of the backend code that trigger email sends.
6.3. Social Login Providers (Google, etc. - UI Placeholders Only for MVP)
REQ-INT-009 (Purpose): To offer alternative, convenient login methods for users of the external "Create Request Page."
REQ-INT-010 (MVP Implementation - UI Placeholders):
The external login page (REQ-EXT-004) may display UI buttons like "Login with Google" or "Login with [OtherProvider]".
These buttons shall be non-functional in the MVP.
Clicking them might show a message like "Coming Soon" or simply do nothing.
No backend integration or API calls to social identity providers will be implemented for MVP.
8. Error Handling & Logging
This section defines the requirements for how ComplyArkWebApp MVP will handle errors, provide feedback to users, and log relevant information for debugging and monitoring purposes.
8.1. User-Facing Error Handling & Feedback
REQ-ERR-001 (Clear Error Messages): When an error occurs due to invalid user input, system issues, or API failures, the application shall display clear, user-friendly error messages. Messages should avoid overly technical jargon.
Example (Validation): "Please enter a valid email address."
Example (API Error): "Could not save your changes. Please try again later. If the problem persists, contact support."
REQ-ERR-002 (Inline Form Validation Errors): For data entry forms, validation errors (e.g., mandatory field missing, incorrect format) shall be displayed inline, next to or below the respective form field, upon attempting to submit the form or as the user types/blurs (client-side validation).
REQ-ERR-003 (Global Notifications for API Errors): For errors resulting from backend API calls (e.g., server error, network issue, failed save operation), a global notification mechanism (e.g., MUI Snackbar or Alert component) shall be used to inform the user without disrupting the entire page.
These notifications should be dismissible by the user.
They should indicate the nature of the problem (e.g., "Error saving organisation details," "Failed to load user list").
REQ-ERR-004 (Success Notifications): Successful completion of significant user actions (e.g., creating an organisation, saving a notice, submitting a DPR) shall also be confirmed with a clear success notification (e.g., "Organisation created successfully!").
REQ-ERR-005 (Loading Indicators): During long-running operations, especially those involving API calls (e.g., fetching data for a table, submitting a large form, uploading a file), the UI shall display appropriate loading indicators (e.g., spinners, progress bars, disabled buttons with loading text) to inform the user that the system is processing their request.
REQ-ERR-006 (Graceful Degradation - Basic): If a non-critical part of a page fails to load or a minor feature encounters an error, the rest of the page/application should remain functional where possible. For MVP, this means isolated component errors shouldn't crash the entire application.
REQ-ERR-007 (Not Found / Unauthorized Pages):
Attempting to access a non-existent URL within the application shall display a user-friendly "404 - Page Not Found" error page.
Attempting to access a resource or perform an action for which the user is not authorized (as determined by backend RBAC) shall result in a clear "403 - Access Denied" or "Unauthorized" message/page.
8.2. Backend Error Handling & API Responses
REQ-ERR-008 (Consistent API Error Structure): Backend API responses for errors shall follow a consistent JSON structure, including:
An appropriate HTTP status code (e.g., 400 for bad request/validation error, 401 for unauthorized, 403 for forbidden, 404 for not found, 500 for server error).
A machine-readable error code or type (e.g., VALIDATION_ERROR, UNAUTHENTICATED, INTERNAL_SERVER_ERROR).
A human-readable error message (which can be used by the frontend).
Optionally, for validation errors, a list of specific field errors: [{ field: 'fieldName', message: 'Error detail' }].
REQ-ERR-009 (Centralized Error Handling Middleware - Backend): A centralized error handling middleware shall be implemented in the Express.js backend to catch unhandled exceptions, format error responses consistently (as per REQ-ERR-008), and log errors (as per REQ-ERR-011).
REQ-ERR-010 (Input Validation - Backend): All data received by backend API endpoints from clients (frontend, external page) must be rigorously validated for type, format, presence of mandatory fields, and business logic constraints before processing or database interaction. Invalid data should result in a 400-level error response.
8.3. Logging (MVP Scope)
REQ-ERR-011 (Backend Application Error Logging):
Unhandled exceptions and significant errors occurring in the backend application logic (e.g., database connection failures, critical service failures, unexpected errors during request processing) shall be logged.
For MVP, logging shall be directed to the server console. (Post-MVP, this would be to a persistent log file or a centralized logging service).
Log entries should include:
Timestamp.
Error level (e.g., ERROR, WARN).
Error message.
Stack trace (for exceptions).
Relevant request context if possible (e.g., API endpoint, user ID if authenticated – being mindful of not logging PII excessively in error messages).
REQ-ERR-012 (Backend API Request Logging - Basic):
Consider basic logging of incoming API requests (e.g., method, URL, status code of response, processing time) to the console for debugging during development and pilot. (e.g., using a middleware like morgan in Express). This is primarily for development insight in MVP.
REQ-ERR-013 (Frontend Console Logging):
During development, frontend developers shall use console.log(), console.error(), etc., for debugging purposes.
Most verbose console.log statements should be removed or guarded (e.g., by an environment flag) before deploying even for a pilot, to avoid cluttering the browser console for end-users. Critical frontend errors may still be logged to the console.
REQ-ERR-014 (No Sensitive Data in Logs): Logs (both backend and frontend) must not contain sensitive personal data (e.g., passwords, full credit card numbers, detailed health information) unless absolutely necessary for diagnosing a specific, secured PII-related issue, and even then, with extreme caution and masking.
REQ-ERR-015 (Audit Trail Logging - Functional): This is distinct from error/debug logging. Functional audit trails (e.g., DPRequestHistory, GrievanceHistory, changes to core admin data) are part of the application's features and are stored in dedicated database tables as per previous sections. Section 5.6 of the original MRD mentioned an immutable audit trail which is ambitious for MVP DB-only logs; our DB history tables are the MVP equivalent.
9. Future Considerations (Post-MVP Roadmap High-Level)
This section outlines potential features, enhancements, and strategic directions for ComplyArkWebApp beyond the Minimum Viable Product (MVP). These items are not committed for the initial release but represent areas for future growth and product evolution based on user feedback, market demands, and further development of DPDPA Rules.
9.1. Enhanced AI & Automation Capabilities
9.1.1. NLP-based Data Discovery & Classification: Integrate Natural Language Processing (NLP) tools to help Data Fiduciaries scan sample documents or connect to data sources (with explicit permission and security considerations) to semi-automatically identify and classify personal data elements, assisting in RoPA creation.
9.1.2. Automated RoPA Updates: Explore integrations or triggers that could suggest or facilitate updates to the RoPA when new systems or processing activities are detected or reported.
9.1.3. AI-Assisted DPIA: Develop wizards or AI-driven questionnaires to guide users through Data Protection Impact Assessments (DPIAs), suggesting potential risks and mitigation strategies based on input.
9.1.4. Intelligent Policy Generation: Enhance the AI template customization (REQ-APP-E2 from original MRD, now implicitly part of Notice/Doc features) to provide more sophisticated generation of privacy policies and other compliance documents based on detailed organisational context.
9.1.5. AI-Powered Simplified Language Summaries: Use AI to generate plain language summaries of complex legal notices or policy sections for better Data Principal understanding.
9.1.6. Advanced AI Agentic Workflows: Explore AI agents that can proactively monitor for compliance gaps, suggest remedial actions, or automate routine compliance checks.
9.1.7. Real LLM Integration for Translation: Replace the dummy translation service with a production-ready integration with IndicTrans2 or other suitable multilingual LLMs, including managing API keys, costs, and quality control.
9.2. Expanded Module Functionality
9.2.1. Data Processor Portal: A dedicated portal for Data Processors engaged by the Data Fiduciary. Processors could:
Receive and acknowledge processing instructions.
Manage their parts of Data Processing Agreements (DPAs).
Report data breaches to the Fiduciary.
Respond to Fiduciary audit requests.
9.2.2. Advanced Consent Management:
A dedicated Data Principal-facing dashboard for managing consents given to a specific Fiduciary.
Granular consent options and preference management.
Consent lifecycle tracking and versioning.
Integration with Fiduciary's websites/apps for real-time consent capture/withdrawal.
9.2.3. Automated Notice Delivery: Integrate with email services (SendGrid, SES) and potentially SMS gateways or in-app notification systems for automated distribution of generated notices.
9.2.4. Dedicated DPIA Module: A full-fledged module to conduct, document, and track DPIAs, including risk assessment matrices, mitigation plans, and DPO review workflows.
9.2.5. Data Breach Management & Reporting Aid:
Advanced workflows for managing internal breach investigation and response.
Automated assistance in preparing breach notifications for the Data Protection Board and Data Principals, aligning with DPDPA timelines and content requirements.
9.2.6. Vendor Management / Third-Party Risk Module: Tools to assess and manage risks associated with third-party vendors (Data Processors), including DPA tracking, security questionnaire management, and audit scheduling.
9.2.7. Employee Training & Awareness Module: Platform for delivering DPDPA training content, tracking completion, and managing awareness campaigns.
9.2.8. Significant Data Fiduciary (SDF) Toolkit: Specific features and workflows tailored to the additional obligations of SDFs under DPDPA Section 10 (e.g., DPO appointment logs, audit scheduling, enhanced DPIA requirements).
9.3. Advanced Technical & Platform Enhancements
9.3.1. Advanced Security Features:
Multi-Factor Authentication (MFA) for all user roles.
More granular Role-Based Access Control (RBAC) within organisations.
Advanced encryption options (e.g., encryption at rest for sensitive fields, customer-managed keys).
Intrusion Detection/Prevention Systems (IDS/IPS).
Regular third-party security audits and certifications (e.g., ISO 27001, SOC 2).
9.3.2. Integrations with External Systems:
APIs for integration with clients' existing CRM, ERP, HRMS systems for RoPA data population or DPR fulfillment assistance.
Integration with Identity Providers (IdP) like Azure AD, Okta for Single Sign-On (SSO).
Integration with legal tech or GRC (Governance, Risk, Compliance) platforms.
9.3.3. Advanced Reporting & Analytics: Customizable reports, trend analysis on DPRs/grievances, compliance dashboards with KPIs for executive overview.
9.3.4. Scalable Cloud Infrastructure: Migration to robust cloud storage (AWS S3, Azure Blob) for files, and scalable database solutions (e.g., managed SQL services, NoSQL options for certain data types).
9.3.5. Full Audit Logging: Comprehensive and immutable audit trails for all significant actions within the platform, exportable for regulatory review.
9.3.6. Internationalization (I18n) of Application UI: Support for multiple UI languages for the platform itself.
9.3.7. Mobile Application: Native or progressive web apps for on-the-go access for certain user roles or functionalities.
9.4. Business & Service Model Evolution
9.4.1. Tiered Subscription Plans: Offering different feature sets and usage limits based on subscription tiers.
9.4.2. Value-Added Services: Potential for offering expert consultation, DPO-as-a-Service, or managed compliance services built around the platform.
9.4.3. Marketplace/Ecosystem: Integrations with other compliance tools or legal service providers.
9.5. Regulatory Landscape Adaptation
9.5.1. Support for DPDP Rules: As the detailed DPDP Rules are notified, the platform will need to be updated to incorporate specific requirements and workflows derived from these rules.
9.5.2. Support for Other Regulations: Potential expansion to cover other Indian or international data protection and privacy regulations (e.g., GDPR if clients have an international presence, sector-specific regulations).
10. Assumptions & Dependencies
This section lists key assumptions made during the planning of the ComplyArkWebApp MVP and identifies critical dependencies that could impact its development and deployment.
10.1. Assumptions
10.1.1. DPDPA Act as Primary Reference: It is assumed that The Digital Personal Data Protection Act, 2023 (No. 22 of 2023) as provided is the stable and primary legal text for defining compliance requirements for the MVP. While forthcoming DPDP Rules will add detail, the MVP focuses on core obligations derivable from the Act itself.
10.1.2. Target User Technical Proficiency: It is assumed that primary users (Data Fiduciary personnel) will have standard business computer literacy and access to modern web browsers on desktop/laptop computers. Extensive technical expertise is not assumed.
10.1.3. MVP Focus on Facilitation, Not Legal Advice: ComplyArkWebApp MVP is a tool to facilitate compliance management and documentation. It is assumed that the platform does not provide legal advice, and users (Data Fiduciaries) are responsible for their own legal interpretations and compliance decisions. Templates and guidance provided are for informational purposes and should be reviewed by the Fiduciary's legal counsel.
10.1.4. Manual Data Entry for Core Records: It is assumed that for MVP, key data inputs for RoPA and initial notice generation will be manual. Automated data discovery or direct system integration for these purposes is out of MVP scope.
10.1.5. Dummy/Simulated External Services for MVP: It is assumed that dummy implementations for services like LLM translation and email sending (logging to console) are acceptable for the MVP phase to prove application flow, with real integrations planned post-MVP.
10.1.6. Local File System Storage for MVP: It is assumed that storing uploaded files and generated documents on the local server's file system is acceptable for the MVP development and pilot phase. Migration to cloud object storage is a post-MVP consideration.
10.1.7. English as Sole UI Language for MVP: It is assumed that the entire application User Interface (System Admin and Main Application) will be in English for the MVP.
10.1.8. Development & Pilot Environment: It is assumed that a suitable development and pilot testing environment, including access to an MS SQL Server instance, will be available and maintained.
10.1.9. Scope of DPDPA Applicability: The MVP assumes its users (Data Fiduciaries) are entities to whom the DPDPA applies. The platform does not determine applicability for an organisation.
10.1.10. Client Responsibility for Accuracy: While the platform provides tools for documentation, the accuracy and completeness of the information entered by the Data Fiduciary (e.g., in questionnaires, RoPA) remain the responsibility of the Data Fiduciary.
10.1.11. Feedback Loop for Pilot: It is assumed that pilot users will provide timely and constructive feedback to help refine the product post-MVP.
10.2. Dependencies
10.2.1. Technology Stack Availability & Stability:
Node.js & React Ecosystem: Dependency on the stability and continued availability of core Node.js, Express.js, React, and Material UI libraries and their ecosystems.
MS SQL Server: Dependency on a functional and accessible MS SQL Server database instance for development, testing, and pilot deployment.
10.2.2. Development Team & Resources: Dependency on the availability of skilled development resources (frontend, backend, database) as per the project timeline.
10.2.3. Clarity on DPDPA Interpretations (Ongoing): While the Act is the base, ongoing clarifications or widely accepted interpretations of certain DPDPA provisions by regulatory bodies or industry consensus may influence feature refinement post-MVP. For MVP, development will adhere to the plain text and clear implications of the Act.
10.2.4. IndicTrans2 (or similar) Documentation (for Future Integration): For the eventual real integration of translation services, dependency on clear API documentation, availability, and terms of service of the chosen LLM provider.
10.2.5. Infrastructure for Pilot Deployment: Dependency on appropriate server infrastructure (whether local, on-premise, or basic cloud VM) for hosting the backend, database, and frontend build for the pilot phase. This includes sufficient storage, compute resources, and network accessibility.
10.2.6. Finalized Design Assets & UI/UX Guidelines: Dependency on finalized UI mockups, wireframes, and any specific branding guidelines (if applicable) before extensive frontend development of each module. (Material UI provides a strong base).
10.2.7. User Acceptance and Onboarding for Pilot: Dependency on the willingness and availability of selected pilot organisations/users to engage with the MVP and provide feedback. Successful onboarding by the ComplyArk team is also a dependency.
11. Acceptance Criteria (Overall MVP)
This section defines the high-level acceptance criteria that the ComplyArkWebApp MVP must meet to be considered complete and ready for its initial pilot phase. These criteria ensure that the core objectives of the MVP are achieved. Detailed acceptance criteria for individual user stories or features will be defined during sprint planning but will align with these overall objectives.
11.1. Core Functionality & User Roles
AC-MVP-001: System Administrator (complyarkadmin) can successfully log in and perform all defined CRUD operations on Organisations, Industries, System-Wide Users (SystemAdmins), Notice Templates (including file upload), and Request Statuses via the System Admin interface.
AC-MVP-002: Upon Organisation creation by System Admin, a default OrgAdmin user is automatically created with correct initial credentials and permissions, and a unique RequestPageURL is generated and stored.
AC-MVP-003: Organisation Users (OrgAdmin and OrgUser) can successfully log in to the main application using their specific credentials, scoped to their assigned Organisation. The main application layout (header with Org Name, navigation panel, dark mode toggle) is functional.
AC-MVP-004: OrgAdmin can successfully perform CRUD operations on users (primarily OrgUsers) within their own Organisation, including setting basic CanEdit/CanDelete permissions.
AC-MVP-005: OrgUser can view their own profile and change their password.
11.2. Notice Module Workflow
AC-MVP-006: An Organisation User can successfully complete the Notice Questionnaire (Tab 1), selecting and inputting data across all defined categories, including the section for Children/Disability data considerations.
AC-MVP-007: An Organisation User can select a pre-set Notice Template OR upload a custom notice format (PDF/DOCX) in the Notice Module (Tab 2).
AC-MVP-008: The system correctly populates/displays data from Tab 1 in Tab 2 for reference.
AC-MVP-009: An Organisation User can successfully save a notice in Tab 2. The system correctly generates a versioned NoticeName, saves the notice content to the database (Notice table), and saves the corresponding notice document to the correct GeneratedNotices/[OrgID]/ file system location.
AC-MVP-010: In Tab 3 of the Notice Module, the original generated notice is displayed with download options. The user can select target languages and initiate the (dummy) translation process.
AC-MVP-011: (Dummy) Translated notice files are created in NoticesTranslated/[OrgID]/, and corresponding tiles with download links are displayed in the UI.
1.3. External Request Page & DPR/Grievance Modules
AC-MVP-012: An external Data Principal can access an Organisation's specific CreateRequestPage via its unique URL and (after dummy login) successfully submit a Data Principal Request (of any defined type) and a separate Grievance.
AC-MVP-013: Submitted DPRs and Grievances are correctly saved to their respective database tables (DPRequests, Grievances), linked to the correct OrganisationID, assigned to the default OrgAdmin, have an initial 'Submitted' status, and have their ExpectedCompletionDate calculated. Initial history entries are created.
AC-MVP-014: Organisation Users can view lists of DPRs and Grievances for their organisation, with working filters (status, assigned to, type (DPR), date) and search functionality.
AC-MVP-015: Organisation Users can open a specific DPR or Grievance to view its full details and complete chronological history trail.
AC-MVP-016: Authorised Organisation Users (OrgAdmin for assignment, OrgAdmin/OrgUser with CanEdit for status) can successfully update the status and assignment of DPRs/Grievances. Closure with mandatory comments is functional. All updates are correctly logged in the respective history table.
11.4. RoPA & Compliance Documentation
AC-MVP-017: Organisation Users can manually create, view, edit, and delete Record of Processing Activity (RoPA) entries, capturing all defined RoPA elements.
AC-MVP-018: The RoPA viewing interface presents the data in a clear, structured, and readable format. RoPA data can be exported to CSV.
AC-MVP-019: Organisation Users can use the Compliance Documentation module to create folders, upload supported file types, view folder/file listings with breadcrumb navigation, download files, and delete files/folders.
AC-MVP-020: Quick links/views within the Compliance Documentation module correctly display generated notices, translated notices, and applicable templates.
11.5. Task Management & Dashboard
AC-MVP-021: Organisation Users can create, assign, and update the status of basic compliance tasks.
AC-MVP-022: The main application Dashboard correctly displays the Organisation Name, visual summaries (pie charts) of DPR/Grievance statuses, and accurate lists of escalated DPRs/Grievances for the logged-in user's Organisation (with appropriate scope for OrgAdmin vs. OrgUser).
11.6. Non-Functional Requirements (Adherence)
AC-MVP-023 (Usability): The application is generally intuitive for target users, with clear navigation, consistent UI (Material UI based), and helpful feedback for actions and errors, meeting key NFRs from Section 5.1.
AC-MVP-024 (Performance): Core page loads and data interactions meet the basic performance NFRs outlined in Section 5.2 for typical MVP data volumes. The application does not exhibit significant lag or unresponsiveness during normal use.
AC-MVP-025 (Reliability): The application is stable, and core workflows can be completed without frequent crashes or data corruption, meeting key NFRs from Section 5.3.
AC-MVP-026 (Security): Basic security NFRs (HTTPS, password hashing, backend RBAC enforcement, basic input sanitization) as outlined in Section 5.4 are implemented.
AC-MVP-027 (Browser Compatibility): The application functions as expected on the latest stable versions of Chrome, Firefox, and Edge.
11.7. Development & Setup
AC-MVP-028: The codebase is organized according to the agreed-upon project structure.
AC-MVP-029: The README.md file provides clear and sufficient instructions for setting up the development environment (backend, frontend, database) and running the application locally.
11.8. Overall Pilot Readiness
AC-MVP-030: A Data Fiduciary organisation can successfully use the ComplyArkWebApp MVP to perform the end-to-end basic DPDPA compliance management tasks included in the MVP scope (from understanding processing activities via RoPA/Notice questionnaire, to generating a notice, to receiving and managing a DPR).

