Comply Ark Phased Development Plan

Phase 1: Foundation, System Administration Core & Basic App Shell
Estimated Duration: 6-7 Weeks
Goal: Establish an unshakeable project foundation, fully functional System Admin interface for all core master data management, and a secure, authenticated entry point into the main application shell for Organisation Users. This phase lays the groundwork for all subsequent development.
KPIs for Phase 1:
KPI 1.1 (DB Setup): 100% of the defined MVP MS SQL database schema implemented, validated, and core master data tables (Industry, RequestStatus) along with an initial SystemAdmin user seeded successfully.
KPI 1.2 (Admin Auth): System Admin login via /admin/login is secure (using JWTs, hashed passwords) and fully functional. Role-based protection for admin routes is effective.
KPI 1.3 (Admin CRUD Complete): Full Create, Read, Update, Delete (CRUD) functionality for Organisations (including default OrgAdmin user creation and RequestPageURL generation), Industries, System-Wide Users (SystemAdmins), Notice Templates (including file upload/delete to/from TemplateRepo), and Request Statuses is implemented and accessible via the System Admin UI.
KPI 1.4 (Org User Auth Shell): Default Organisation Administrators (created during Organisation onboarding) can successfully log in to the main application (/app/login) and view the basic application shell (header displaying their Organisation Name, empty navigation links, logout functionality).
KPI 1.5 (API Coverage & Testing): 100% backend API endpoint coverage for all Phase 1 Admin functionalities and core App Authentication. All endpoints documented and successfully tested using Postman/Insomnia.
KPI 1.6 (Unit Test Coverage): Backend service layers for core entities (Industry, Organisation, User, Template, RequestStatus, Auth) achieve >70% unit test coverage.
KPI 1.7 (Reusable Components): Core reusable frontend components (DataTableWrapper, ConfirmationDialog, SnackbarNotification, basic FormModalWrapper) are developed, documented (props, usage), and integrated into Admin UI tabs.
KPI 1.8 (Error Handling): Consistent client-side and server-side error handling mechanisms are in place, providing user-friendly messages for common errors (validation, API failures). Basic request logging is implemented on the backend.
KPI 1.9 (Project Structure & Docs): Backend and frontend project structures are established as per the agreed outline. Initial README.md with comprehensive setup instructions for both environments is complete and validated. Version control (Git) is actively used with the defined branching strategy.
Runnable Checkpoint 1.A (Target: End of Week 2-3):
Demonstrable: System Admin login functionality. Full CRUD for Industries and Request Statuses via Admin UI. DataTableWrapper, ConfirmationDialog, SnackbarNotification components built and usable. Basic backend request logging active. DB schema created and seeded.
Verification: Manual E2E testing of these features. Review of component reusability.
Runnable Checkpoint 1.B (Target: End of Week 4-5):
Demonstrable: In addition to 1.A, full CRUD for Organisations (including default OrgAdmin creation and RequestPageURL) and Notice Templates (including file uploads/downloads/deletions to TemplateRepo) via Admin UI.
Verification: Manual E2E testing. Verification of file operations and default user creation logic.
Runnable Checkpoint 1.C (Target: End of Phase, Week 6-7):
Demonstrable: All System Admin functionalities complete, including System-Wide User Management. Organisation Administrators can log into the main application shell and see their Organisation Name in the header. All Phase 1 KPIs are met.
Verification: Full E2E testing of all Phase 1 features. Code reviews complete. Documentation updated.

Milestones & Detailed Tasks:
M1.1: Project & Environment Setup (Est. Duration: 3-4 days)
Task M1.1.1 (Backend - Project Init): Initialize Node.js project (npm init or yarn init). Install core dependencies: express, mssql (SQL Server driver), bcryptjs (password hashing), jsonwebtoken (JWTs), dotenv (environment variables), cors (Cross-Origin Resource Sharing), nodemon (dev auto-restart), multer (file uploads). Set up basic package.json scripts (e.g., dev, start).
PRD Link: Technology Stack (Preamble)
Task M1.1.2 (Backend - Directory Structure): Create backend source directory structure: src/, with subdirectories config/, controllers/, middleware/, migrations/ (optional, for schema changes), models/ (if using ORM, else for DB interaction modules), routes/, services/, utils/.
PRD Link: Project Structure Outline
Task M1.1.3 (Backend - DB Config & Connection): Implement src/config/db.js to handle MS SQL connection parameters using dotenv (e.g., DB_USER, DB_PASSWORD, DB_SERVER, DB_DATABASE). Create a utility function to establish and test the database connection.
PRD Link: REQ-DATA-001
Task M1.1.4 (Backend - Server Setup): Implement server.js (or app.js) to initialize the Express application, configure middleware (CORS, express.json(), express.urlencoded()), set up port listening from .env, and include a basic root route (/) for health checks. Implement a stub for global error handling middleware. Implement request logging middleware (e.g., morgan in dev mode).
PRD Link: NFR-012, REQ-ERR-009, REQ-ERR-012
Task M1.1.5 (Frontend - Project Init): Initialize React project using Create React App or Vite (npx create-react-app complyark-frontend or npm create vite@latest complyark-frontend -- --template react). Install core dependencies: @mui/material, @mui/icons-material, @emotion/react, @emotion/styled, axios, react-router-dom. Install state management library if decided early (e.g., Zustand, Redux Toolkit).
PRD Link: Technology Stack (Preamble)
Task M1.1.6 (Frontend - Directory Structure): Create frontend source directory structure: src/, with subdirectories admin/, app/, assets/, components/, contexts/, hooks/, layouts/, pages/, services/, theme/, utils/.
PRD Link: Project Structure Outline
Task M1.1.7 (DB - Schema Creation): Write and execute SQL scripts (.sql files) to create all tables defined in the "Finalized Database Schema" section (Industry, Organisation, Users, Template, RequestStatus, Notice, DPRequests, DPRequestHistory, Grievances, GrievanceHistory, OrganisationDocuments, RoPAEntries, GeneralTasks). Ensure all PKs, FKs, constraints, defaults, and data types are correctly implemented.
PRD Link: REQ-DATA-002, REQ-DATA-003, REQ-DATA-004
Task M1.1.8 (DB - Seeding Core Data): Write and execute SQL seed scripts to populate:
Industry table with initial list (E-commerce, Healthcare, FinTech, etc.).
RequestStatus table with initial statuses ('Submitted', 'InProgress', 'AwaitingInfo', 'Reassigned', 'Escalated', 'Closed') and their default SLAs.
Users table with one SystemAdmin record (e.g., complyarkadmin@example.com, with a pre-hashed password for complyarkadmin).
PRD Link: REQ-ADM-002, REQ-ADM-015, REQ-ADM-023
Task M1.1.9 (DevOps - Version Control): Initialize Git repository in the project root. Create main and develop branches. Define and document a branching strategy (e.g., Gitflow: feature/, bugfix/, release/). Implement a comprehensive .gitignore file for Node.js and React.
Task M1.1.10 (Documentation - Initial README): Create README.md in the project root. Include: Project Title, Brief Description, Prerequisites (Node.js version, NPM/Yarn, MS SQL Server), Backend Setup Instructions (clone, npm install, .env configuration, DB connection, run dev server), Frontend Setup Instructions (clone, npm install, run dev server).
Task M1.1.11 (File System - Utility Folders): Manually create the physical top-level folders on the development server where backend will store files: TemplateRepo/, GeneratedNotices/, NoticesTranslated/, OrganisationSpecificDocs/. Ensure backend process has write permissions (configure locally).
PRD Link: REQ-DATA-007
M1.2: System Admin Authentication (Est. Duration: 3 days) (PRD Ref: REQ-ADM-001 to REQ-ADM-003, REQ-ADM-003a)
Task M1.2.1 (Backend - Controller & Service): Create src/controllers/authController.js and src/services/authService.js.
authService.adminLogin(email, password): Fetch SystemAdmin user from Users by email. If user exists and Role is 'SystemAdmin', use bcryptjs.compare() to verify password. If valid, generate JWT.
JWT payload: userId, role: 'SystemAdmin', firstName. Sign with JWT_SECRET from .env. Set an appropriate expiry (e.g., JWT_EXPIRES_IN from .env).
authController.adminLogin(req, res, next): Call service, send token in response on success, handle errors.
Task M1.2.2 (Backend - Routes): Create src/routes/authRoutes.js. Define POST /api/auth/admin/login route pointing to authController.adminLogin. Register these routes in server.js.
Task M1.2.3 (Backend - Middleware): Create src/middleware/authMiddleware.js.
protectSystemAdmin(req, res, next): Verify JWT from Authorization header (Bearer token). If valid and role is 'SystemAdmin', attach req.user (decoded token payload) and call next(). Else, return 401/403 error.
Task M1.2.4 (Frontend - Login Page): Create src/pages/AdminLoginPage.js. Implement UI form (MUI TextField for email/password, Button for login). Manage form state (email, password, loading, error).
Task M1.2.5 (Frontend - Service Call): Create src/services/authApiService.js (or update existing authService.js). Implement adminLogin(email, password) function to make POST request to /api/auth/admin/login.
Task M1.2.6 (Frontend - Context): Create/Update src/contexts/AuthContext.js.
State: user, token, isAuthenticated, isLoading, error, role.
loginAdminAction(email, password): Calls authApiService.adminLogin, on success stores token (e.g., in localStorage), decodes token to get user info, updates context state, navigates to admin dashboard. Handles errors.
logoutAction: Clears token, resets context state, navigates to login page.
Task M1.2.7 (Testing): API test login with correct/incorrect credentials. Frontend test login flow, error messages, successful redirect, token storage, context update.
M1.3: System Admin Core UI & Reusable Components (Est. Duration: 4-5 days)
Task M1.3.1 (Frontend - Layout): Create src/layouts/AdminLayout.js.
Persistent MUI AppBar (header): App Name ("ComplyArk System Admin"), "Go to Main App" link (placeholder, non-functional initially).
MUI Tabs component below AppBar for navigating admin modules (Organisations, Users, Industries, Templates, Request Statuses). Tab selection updates a local state.
Task M1.3.2 (Frontend - Protected Route): Create src/components/AdminProtectedRoute.js. This Higher-Order Component (HOC) or wrapper component checks AuthContext for isAuthenticated and role === 'SystemAdmin'. If not, redirects to /admin/login.
Task M1.3.3 (Frontend - Routing): Update src/App.js (or a dedicated AdminRouter.js).
Route /admin/login to AdminLoginPage.js.
Protected route /admin/dashboard (or /admin/) wrapped by AdminProtectedRoute renders AdminLayout. Content area of AdminLayout will render specific Tab components based on selected tab.
Task M1.3.4 (Frontend - DataTableWrapper): Create src/components/DataTableWrapper.js.
Props: data (array), columns (array of column defs: field, headerName, sortable, renderCell), isLoading (boolean), error (string/object), totalRows (for server-side pagination), rowsPerPageOptions (array), onPageChange (func), onRowsPerPageChange (func), onSortChange (func), onEdit (func, takes row data), onDelete (func, takes row data), searchPlaceholder (string), onSearchChange (func).
Internal state for client-side search term, sort model, pagination if client-side.
Uses MUI: TableContainer, Table, TableHead, TableRow, TableCell, TableSortLabel, TableBody, TablePagination.
"Actions" column with MUI IconButton for Edit and Delete, calling onEdit and onDelete.
Task M1.3.5 (Frontend - ConfirmationDialog): Create src/components/ConfirmationDialog.js.
Props: open (boolean), onClose (func), onConfirm (func), title (string), message (string).
Uses MUI Dialog, DialogTitle, DialogContent, DialogContentText, DialogActions, Button.
Task M1.3.6 (Frontend - SnackbarNotification): Create src/contexts/NotificationContext.js and src/components/SnackbarNotification.js.
Context provides showNotification(message, severity) function (severity: 'success', 'error', 'warning', 'info').
Component uses MUI Snackbar and Alert to display messages. Auto-hide after a few seconds.
Task M1.3.7 (Frontend - FormModalWrapper): Create src/components/FormModalWrapper.js.
Props: open, onClose, title, onSubmit, children (the form fields), isSubmitting.
Uses MUI Dialog with DialogTitle, DialogContent (for form), DialogActions (Submit, Cancel buttons).
Task M1.3.8 (Testing): Basic rendering tests for layouts and reusable components. Storybook setup for components is desirable (Post-MVP).
M1.4 to M1.8 (Admin CRUD Modules): For each module (Industry, Request Status, Organisation, Notice Template, System-Wide User), the tasks are similar and will reuse components from M1.3:
Sub-Milestone X.1 (Backend):
Task X.1.1: Create [entity]Controller.js and [entity]Service.js.
Task X.1.2: Implement service functions for full CRUD operations (Create, Get All with pagination/filter/sort, Get By ID, Update, Delete) interacting with the respective DB table.
Specific for OrganisationService: Logic for default OrgAdmin creation & RequestPageURL generation within createOrganisation service method (transactional).
Specific for TemplateService: Logic for file upload to TemplateRepo (using multer middleware in route) and file deletion from server within create/update/delete service methods.
Task X.1.3: Define [entity]Routes.js with appropriate HTTP methods and paths, protected by protectSystemAdmin. Include file download route for Templates.
Task X.1.4: Write comprehensive unit tests for [entity]Service.js.
Sub-Milestone X.2 (Frontend):
Task X.2.1: Create src/admin/[Entity]Tab.js component.
Task X.2.2: Implement "Add New [Entity]" button, which opens FormModalWrapper.
Task X.2.3: Design and implement the form fields for creating/editing the entity within the modal. Manage form state (e.g., using react-hook-form or simple state).
Specific for Organisation Form: Industry dropdown populated from GET /api/admin/industries.
Specific for Template Form: Industry dropdown, File input for template file.
Task X.2.4: Create src/services/[entity]ApiService.js for all CRUD API calls.
Task X.2.5: Integrate DataTableWrapper to display list of entities. Call appropriate API to fetch data.
Task X.2.6: Implement handleEdit (pre-fill form in modal with row data) and handleDelete (show ConfirmationDialog, then call API) functions.
Task X.2.7: Use NotificationContext to show success/error messages.
Sub-Milestone X.3 (Testing):
Task X.3.1: API contract testing for all [entity] endpoints using Postman/Insomnia.
Task X.3.2: Frontend manual E2E testing of the CRUD flow for the entity.
Runnable Checkpoint 1.A after M1.4 (Industry) & M1.5 (Request Status) are complete.
Runnable Checkpoint 1.B after M1.6 (Organisation) & M1.7 (Template) are complete.
M1.9: Main Application Shell & Organisation User Authentication (Est. Duration: 4 days) (PRD Ref: REQ-APP-001 to REQ-APP-009)
Task M1.9.1 (Backend - Auth Logic): authController.js, authService.js:
orgUserLogin(email, password) service: Fetch user by email from Users. Verify OrganisationID is not NULL, Organisation.IsActive, Users.IsActive. Bcrypt compare password. If valid, generate JWT.
JWT payload for OrgUser: userId, organisationId, role ('OrgAdmin'/'OrgUser'), firstName, lastName, canEdit, canDelete.
Task M1.9.2 (Backend - Route): authRoutes.js: Define POST /api/auth/login route for OrgUsers.
Task M1.9.3 (Backend - Middleware): authMiddleware.js:
protectOrgUser(req, res, next): Verify JWT, check if role is 'OrgAdmin' or 'OrgUser'. Attach req.user (decoded token). If req.user.organisationId is missing or user is not active, deny access.
Task M1.9.4 (Frontend - Login Page): Create src/app/auth/LoginPage.js. UI form similar to Admin login.
Task M1.9.5 (Frontend - Service & Context): authApiService.js: orgUserLogin function.
AuthContext.js: loginOrgUserAction, logoutAction. Store OrgUser specific details from token.
Task M1.9.6 (Frontend - Main App Layout): Create src/layouts/MainAppLayout.js.
MUI AppBar: Display AuthContext.user.organisationName (needs to be fetched post-login or added to JWT if small). User menu (display AuthContext.user.firstName, Logout option).
MUI Drawer (Left Nav): Static links for MVP (Dashboard, Users (conditional), Notice, DPR, Grievances, Docs, Profile). Active link highlighting.
Dark Mode Toggle: Implement basic MUI theme switching using ThemeContext.js and persist preference.
Task M1.9.7 (Frontend - Protected Route & Routing): Create src/components/OrgProtectedRoute.js.
Update App.js (or AppRouter.js): Route /app/login to LoginPage.js. Protected route /app/dashboard (and other future app/* routes) wrapped by OrgProtectedRoute renders MainAppLayout. Default redirect to /app/dashboard after login.
Task M1.9.8 (Testing): Manually create an OrgUser via SysAdmin UI (or directly in DB if Org CRUD not fully ready). Test login with this OrgUser. Verify layout, OrgName display, navigation links (non-functional targets okay), logout.
M1.10: Phase 1 Integration, Comprehensive Testing & Review (Est. Duration: 3 days)
Task M1.10.1 (Integration Testing): Test overall flow: SysAdmin creates Org -> Default OrgAdmin logs into Main App. SysAdmin creates Industry -> Industry appears in Org creation form. SysAdmin creates Template -> Template available (conceptually) for Notice Module.
Task M1.10.2 (API Documentation & Collection): Consolidate and finalize Postman/Insomnia collection for all Phase 1 APIs with example requests/responses.
Task M1.10.3 (E2E Scenario Testing): Document and manually execute key E2E scenarios for Phase 1.
Task M1.10.4 (Code Reviews): Conduct thorough peer code reviews for all backend and frontend deliverables of Phase 1. Focus on adherence to standards, NFRs, security basics.
Task M1.10.5 (Documentation Update): Ensure README.md is comprehensive and accurate for setting up and running the current state of the project. Document any critical decisions or deviations.
Task M1.10.6 (KPI Verification): Verify all KPIs for Phase 1 are met.
(Runnable Checkpoint 1.C / End of Phase)
Phase 2: Core Main Application Modules - Dashboard, Org User Mgmt, Profile (Est. Duration: 4-5 Weeks)
* Goal: Deliver essential user-facing features within the main application for Organisation Users: a dynamic (though initially with some placeholders for later data integration) dashboard, comprehensive organisation-level user management for OrgAdmins, and individual user profile viewing/password management capabilities for all authenticated Organisation users.
* KPIs for Phase 2:
* KPI 2.1 (Dashboard Display): The main application Dashboard correctly displays the logged-in user's Organisation Name and renders UI elements for charts and tables (populated with dummy/placeholder data for DPR/Grievance stats in this phase).
* KPI 2.2 (Org User CRUD - OrgAdmin): Organisation Administrators can perform full CRUD operations (Create, Read with pagination/filter/search, Update details & permissions, Deactivate/Delete) on OrgUser accounts within their own Organisation via the dedicated "Users" module.
* KPI 2.3 (User Profile & Password): All authenticated Organisation Users (OrgAdmin, OrgUser) can view their own profile details and successfully change their own password through the "My Profile" section. The "Forgot Password" flow is functional (with dummy email).
* KPI 2.4 (RBAC - User Module): Role-based access control for the Organisation User Management module is strictly enforced (only OrgAdmin can access and perform management actions).
* KPI 2.5 (API Coverage & Testing): 100% backend API endpoint coverage for all Phase 2 features (Dashboard summary (dummy), Org-scoped User CRUD, Profile management, Password change/reset). All new/updated endpoints documented and successfully tested using Postman/Insomnia.
* KPI 2.6 (Unit Test Coverage): Backend service layers for new functionalities (Org-scoped User service, Profile service) achieve >70% unit test coverage.
* KPI 2.7 (UI Consistency & Reusability): Frontend components for Phase 2 modules maintain UI consistency with Phase 1 and effectively utilize shared components (DataTableWrapper, FormModalWrapper, etc.).
* Runnable Checkpoint 2.A (Target: Mid-Phase, Est. Week 2):
* Demonstrable: Basic Dashboard UI elements are present and display Organisation Name. Organisation User Management module: OrgAdmin can list existing users (default admin) and view their details. User Profile page displays current user's info.
* Verification: Manual E2E of these view functionalities. API tests for read operations.
* Runnable Checkpoint 2.B (Target: End of Phase, Week 4-5):
* Demonstrable: Full Dashboard functionality (with dummy data for charts/escalations, ready for Phase 4 data integration). Full CRUD for Organisation User Management by OrgAdmin. User Profile view and Change Password functionality are complete. Forgot Password flow works (with console-logged token). All Phase 2 KPIs met.
* Verification: Full E2E testing of all Phase 2 features. Code reviews complete. Documentation updated.
*   **Milestones:**

	*   **M2.1: Basic Dashboard Implementation (Org User View) (Est. Duration: 4-5 days)** (PRD Ref: REQ-APP-010 to REQ-APP-013, REQ-APP-015, REQ-APP-016, REQ-APP-035, REQ-APP-036)
    	*   **Task M2.1.1 (Backend - Controller & Service):** Create `src/controllers/dashboardController.js` and `src/services/dashboardService.js`.
    	*   **Task M2.1.2 (Backend - API Endpoint):** Implement `GET /api/app/dashboard/summary` endpoint.
        	*   `dashboardService.getSummary(organisationId)`:
            	*   Fetch `Organisation.BusinessName` using `organisationId` from `req.user`.
            	*   Return *dummy/hardcoded* data structure for MVP dashboard stats:
                	```json
                	{
                  	"organisationName": "Fetched Org Name",
                  	"dprStatusCounts": [ { "name": "Submitted", "value": 5 }, { "name": "InProgress", "value": 2 } ],
                  	"grievanceStatusCounts": [ { "name": "Submitted", "value": 3 }, { "name": "Closed", "value": 10 } ],
                  	"escalatedDprs": [ { "id": "DPR001", "requester": "John Doe", "type": "Access", "dueDate": "YYYY-MM-DD", "assignedTo": "Jane Smith", "status": "Submitted" } ],
                  	"escalatedGrievances": [ { "id": "GRV005", "requester": "Peter Pan", "dueDate": "YYYY-MM-DD", "assignedTo": "Self", "status": "InProgress" } ]
                	}
                	```
            	*   *This structure anticipates real data for Phase 4.*
    	*   **Task M2.1.3 (Backend - Route):** Define route in `src/routes/dashboardRoutes.js`, protected by `protectOrgUser`.
    	*   **Task M2.1.4 (Backend):** Unit tests for `dashboardService.getSummary` (testing structure of dummy data).
    	*   **Task M2.1.5 (Frontend - Page & Service):** Create `src/app/dashboard/DashboardPage.js`. Create `src/services/dashboardApiService.js` to call the summary endpoint.
    	*   **Task M2.1.6 (Frontend - Data Fetching & Display):** In `DashboardPage.js`, fetch data on component mount. Display welcome message and Organisation Name.
    	*   **Task M2.1.7 (Frontend - Reusable Chart Component):** Create `src/app/dashboard/components/StatusPieChart.js`.
        	*   Props: `title` (string), `data` (array of `{name, value}`).
        	*   Uses a charting library (e.g., `recharts` - install if not already) to render a pie chart with labels and tooltips.
        	*   Integrate two instances on `DashboardPage.js` for `dprStatusCounts` and `grievanceStatusCounts` using the fetched dummy data.
    	*   **Task M2.1.8 (Frontend - Reusable Table for Escalated Items):** Create `src/app/dashboard/components/EscalatedItemsTable.js`.
        	*   Props: `title` (string), `items` (array), `columnsConfig` (array), `onItemClick` (function to handle row click).
        	*   Uses `DataTableWrapper` internally or a simpler MUI `Table`.
        	*   Integrate two instances on `DashboardPage.js` for `escalatedDprs` and `escalatedGrievances` using dummy data. `onItemClick` will be wired up in Phase 4.
    	*   **Task M2.1.9 (Frontend - Styling):** Apply styling for a clean dashboard layout using MUI Grid or Stack.
    	*   **Task M2.1.10 (Testing):** API test for dummy data structure. Frontend: Verify dashboard renders with dummy data, charts display, tables display.

	*   **M2.2: Organisation User Management (OrgAdmin Role) - Backend (Est. Duration: 4-5 days)** (PRD Ref: REQ-APP-014, REQ-APP-016, REQ-APP-017, REQ-APP-037, REQ-APP-038, REQ-APP-052)
    	*   **Task M2.2.1 (Backend - Controller & Service):** Create `src/controllers/orgUserController.js` and `src/services/orgUserService.js` (or enhance existing user service if structured for multi-scope).
    	*   **Task M2.2.2 (Backend API - Create OrgUser):** `POST /api/app/users` (scoped to current Org).
        	*   Middleware: `protectOrgUser` and `checkRole(['OrgAdmin'])`.
        	*   Service `orgUserService.createOrgUser(data, creatingOrgAdminId, organisationId)`:
            	*   Validate input (email unique across `Users` table).
            	*   Hash password using `bcryptjs`.
            	*   Set `OrganisationID` from `req.user.organisationId`.
            	*   Role defaults to 'OrgUser'. Store `CanEdit`, `CanDelete` flags.
    	*   **Task M2.2.3 (Backend API - List OrgUsers):** `GET /api/app/users`.
        	*   Middleware: `protectOrgUser` and `checkRole(['OrgAdmin'])`.
        	*   Service `orgUserService.listOrgUsers(organisationId, filters, pagination)`: Returns users for `req.user.organisationId`. Implement pagination, search (Name, Email), filter (Role, IsActive).
    	*   **Task M2.2.4 (Backend API - Get Single OrgUser):** `GET /api/app/users/:userId`.
        	*   Middleware: `protectOrgUser` and `checkRole(['OrgAdmin'])`.
        	*   Service: Fetch user only if `Users.OrganisationID` matches `req.user.organisationId`.
    	*   **Task M2.2.5 (Backend API - Update OrgUser):** `PUT /api/app/users/:userId`.
        	*   Middleware: `protectOrgUser` and `checkRole(['OrgAdmin'])`.
        	*   Service: Update user if in same Org. Modifiable fields: FirstName, LastName, Phone, IsActive, CanEdit, CanDelete. Email and Role are not updatable by OrgAdmin for MVP simplicity.
    	*   **Task M2.2.6 (Backend API - Delete OrgUser):** `DELETE /api/app/users/:userId`.
        	*   Middleware: `protectOrgUser` and `checkRole(['OrgAdmin'])`.
        	*   Service: Delete (soft: `IsActive = false`, or hard delete for MVP) user if in same Org. Prevent self-delete. Consider implications if user has active assignments (for MVP, allow delete, assignments become unassigned or reassign manually).
    	*   **Task M2.2.7 (Backend):** Comprehensive unit tests for `orgUserService.js` covering all CRUD operations, permission logic, and scoping.
    	*   **Task M2.2.8 (Testing):** API contract testing (Postman) for all `/api/app/users` endpoints. Test role enforcement.

	*   **M2.3: Organisation User Management (OrgAdmin Role) - Frontend (Est. Duration: 4-5 days)** (PRD Ref: REQ-APP-014 to REQ-APP-017, REQ-APP-039 to REQ-APP-051)
    	*   **Task M2.3.1 (Frontend - Page & Routing):** Create `src/app/users/OrgUsersPage.js`.
        	*   Add route `/app/users` in `App.js`, protected by `OrgProtectedRoute` and an additional check for `AuthContext.user.role === 'OrgAdmin'`.
    	*   **Task M2.3.2 (Frontend - UI):**
        	*   "Add New User" button (opens `FormModalWrapper`).
        	*   Filter controls for user list (Role (though mostly 'OrgUser'), Status (Active/Inactive)). Search input.
    	*   **Task M2.3.3 (Frontend - Form):** Form fields within `FormModalWrapper` for creating/editing OrgUsers:
        	*   FirstName, LastName, Email, Phone. Password & Confirm Password (only on create). IsActive (checkbox). `CanEdit` & `CanDelete` permissions (checkboxes). Role is implicitly 'OrgUser' for creation by OrgAdmin.
    	*   **Task M2.3.4 (Frontend - Service):** Create `src/services/orgUserApiService.js` for API interactions.
    	*   **Task M2.3.5 (Frontend - DataTable):** Integrate `DataTableWrapper` to list users from `GET /api/app/users`.
        	*   Columns: Name, Email, Phone, Role, Active, CanEdit, CanDelete, Actions (Edit, Delete).
    	*   **Task M2.3.6 (Frontend - CRUD Logic):** Implement `handleAddUser`, `handleEditUser` (pre-fill form), `handleDeleteUser` (with `ConfirmationDialog`). Call respective API service functions. Update UI on success. Use `SnackbarNotification`.
    	*   **Task M2.3.7 (Frontend):** UI state management for forms, loading indicators, error messages.
    	*   **Task M2.3.8 (Testing):** Manual E2E testing of OrgUser CRUD by OrgAdmin. Verify filters, search, pagination. Test permission flag updates.
    	*   *(Runnable Checkpoint 2.A after M2.1 and basic User Listing in M2.3)*

	*   **M2.4: User Profile View & Change Password (All Org Roles) (Est. Duration: 3-4 days)** (PRD Ref: REQ-APP-004, REQ-APP-012 to REQ-APP-014)
    	*   **Task M2.4.1 (Backend - Profile Controller & Service):** Create `src/controllers/profileController.js`, `src/services/profileService.js`.
    	*   **Task M2.4.2 (Backend API - Get Profile):** `GET /api/app/profile/me`.
        	*   Middleware: `protectOrgUser`.
        	*   Service `profileService.getMyProfile(userId)`: Fetches details for `req.user.userId` from `Users` table.
    	*   **Task M2.4.3 (Backend API - Change Own Password):** `POST /api/app/profile/me/change-password`.
        	*   Middleware: `protectOrgUser`.
        	*   Inputs: `currentPassword`, `newPassword`.
        	*   Service `profileService.changeMyPassword(userId, currentPassword, newPassword)`: Fetch user, bcrypt compare `currentPassword`. If match, hash `newPassword` and update `PasswordHash`.
    	*   **Task M2.4.4 (Backend - Forgot/Reset Password API - if not fully done in P1):**
        	*   `POST /api/auth/forgot-password`: Input `email`. Service: Find user by email. Generate unique, time-limited `PasswordResetToken`. Store hashed token and `PasswordResetExpires` in `Users` table. (Dummy email: log token/link to console).
        	*   `POST /api/auth/reset-password/:token`: Input `newPassword`. Service: Find user by hashed `PasswordResetToken`. Check token expiry. If valid, update `PasswordHash`, clear token fields.
    	*   **Task M2.4.5 (Backend):** Unit tests for `profileService.js` and password reset token logic.
    	*   **Task M2.4.6 (Frontend - Profile Page):** Create `src/app/profile/MyProfilePage.js`. Add route `/app/profile`.
        	*   Fetch and display current user's details (FirstName, LastName, Email, Phone, Role) from `/api/app/profile/me`. Mostly read-only.
    	*   **Task M2.4.7 (Frontend - Change Password Form):** Section/modal on `MyProfilePage.js` for "Change Password".
        	*   Fields: Current Password, New Password, Confirm New Password. Client-side validation. Call `/api/app/profile/me/change-password`.
    	*   **Task M2.4.8 (Frontend - Forgot/Reset Pages):** Create `src/app/auth/ForgotPasswordPage.js` and `src/app/auth/ResetPasswordPage.js`.
        	*   `ForgotPasswordPage.js`: Email input form, calls `/api/auth/forgot-password`.
        	*   `ResetPasswordPage.js`: Takes token from URL param. New Password/Confirm form, calls `/api/auth/reset-password/:token`.
    	*   **Task M2.4.9 (Frontend):** Update `authApiService.js` for these new API calls.
    	*   **Task M2.4.10 (Testing):** Test profile view for OrgAdmin and OrgUser. Test change password. Test full forgot/reset password flow (manually copying token from console).

	*   **M2.5: Phase 2 Integration, Comprehensive Testing & Review (Est. Duration: 3 days)**
    	*   **Task M2.5.1 (Integration):** Ensure all Phase 2 modules are correctly integrated with the main app layout and `AuthContext`. Test navigation between Dashboard, Users (OrgAdmin), Profile.
    	*   **Task M2.5.2 (API Testing):** Update Postman collection with all new/updated Phase 2 APIs. Execute all tests.
    	*   **Task M2.5.3 (E2E Testing):**
        	*   OrgAdmin logs in -> views dashboard -> navigates to Users module -> creates, edits, deactivates, deletes an OrgUser.
        	*   Newly created OrgUser logs in -> views dashboard -> navigates to My Profile -> views details -> changes password successfully.
        	*   OrgUser initiates Forgot Password flow, "receives" link (from console), resets password, logs in with new password.
    	*   **Task M2.5.4 (Code Review):** Conduct peer code reviews for all Phase 2 backend and frontend code. Check for adherence to NFRs (basic security, error handling, UI consistency).
    	*   **Task M2.5.5 (Documentation):** Update `README.md` for any new environment variables or setup steps. Document new APIs.
    	*   **Task M2.5.6 (KPI Verification):** Verify all KPIs for Phase 2 are met.
    	*   *(Runnable Checkpoint 2.B / End of Phase)*

Phase 3: Notice Generation Module (Est. Duration: 6-7 Weeks)
* Goal: Implement the complete end-to-end notice generation workflow, from detailed data collection via the questionnaire, through template/custom format selection and content editing, to (dummy) translation into multiple Indian languages, with proper data persistence and file management. This module is central to DPDPA compliance regarding informing Data Principals.
* KPIs for Phase 3:
* KPI 3.1 (Questionnaire Functionality): Notice Questionnaire (Tab 1) is fully interactive, correctly captures all required data points across all defined categories (including specific sections for DPDPA Sec 9 on Children/Disability data processing considerations), and allows dynamic addition/editing of fields. Captured data is accurately passed to subsequent tabs.
* KPI 3.2 (Template & Format Handling - Tab 2): Notice Type & Preview (Tab 2) successfully allows selection of Admin-defined templates (filtered by Organisation's industry) and upload of custom notice formats (PDF/DOCX).
* KPI 3.3 (Content Editing & Reference - Tab 2): Text editor in Tab 2 allows modification of template body or addition of custom text. Formatted questionnaire data (from Tab 1) is accurately displayed for reference and can be manually incorporated by the user.
* KPI 3.4 (Notice Persistence - Tab 2): "Save & Next" in Tab 2 correctly persists all notice data (including title, body, type, version, language, questionnaire snapshot) to the Notice database table with accurate versioning logic. The corresponding notice document (uploaded custom format or generated text file) is saved to the GeneratedNotices/[OrgID]/ file system location.
* KPI 3.5 (Translation Workflow - Tab 3): Translation (Tab 3) accurately displays the original generated notice with download options. Users can select multiple target languages. The (dummy) translation process is initiated, (dummy) translated files are created in NoticesTranslated/[OrgID]/, and UI tiles for these translated notices with download links are correctly displayed.
* KPI 3.6 (API Coverage & Testing): 100% Backend API coverage for all Notice module features (fetching templates, saving notice, dummy translation, file downloads). All new APIs documented and successfully tested via Postman/Insomnia.
* KPI 3.7 (Unit Test Coverage): Backend noticeService.js (including versioning, file operations, dummy translation logic) achieves >70% unit test coverage.
* KPI 3.8 (UI/UX): The multi-tab UI for the Notice module is intuitive, guides the user effectively through the process, and provides clear feedback and error handling.
* Runnable Checkpoint 3.A (Target: Mid-Phase, Est. Week 2-3):
* Demonstrable: Notice Questionnaire (Tab 1) is fully functional – UI interactions, data capture into frontend state/context for all categories including dynamic fields. Basic UI shell for Tab 2 and Tab 3 is present.
* Verification: Manual E2E testing of all questionnaire functionalities. Review of frontend state model for questionnaire data.
* Runnable Checkpoint 3.B (Target: Mid-Phase, Est. Week 4-5):
* Demonstrable: Notice Module Tab 2 is fully functional: users can select Admin templates (by industry), upload custom formats, use the text editor, and see questionnaire data for reference. "Save & Next" successfully creates the Notice record in the DB and saves the primary notice file to the file system with correct versioning.
* Verification: Manual E2E testing of Tab 1 -> Tab 2 save workflow. DB and file system checks. API testing for save notice endpoint.
* Runnable Checkpoint 3.C (Target: End of Phase, Week 6-7):
* Demonstrable: Notice Module Tab 3 (dummy) translation and download functionality is complete. Users can select languages, initiate "translation", and download the original and (dummy) translated files. The entire Notice module E2E flow is operational. All Phase 3 KPIs are met.
* Verification: Full E2E testing of the Notice module. Code reviews complete. Documentation updated.

     *   **Milestones:**

    *   **M3.1: Notice Module - Questionnaire (Tab 1) - UI, Data Model & State Management (Est. Duration: 6-7 days)** (PRD Ref: REQ-APP-053 to REQ-APP-060)
        *   **Task M3.1.1 (Frontend - Module Setup):** Create `src/app/notice/NoticeModulePage.js` as the main container with MUI `Tabs` for Tab 1 ("Questionnaire"), Tab 2 ("Compose & Preview"), Tab 3 ("Translate & Download").
        *   **Task M3.1.2 (Frontend - State Management):** Implement a dedicated React Context (e.g., `NoticeContext`) or a Zustand/Redux slice specifically for the Notice module. This will hold:
            *   `questionnaireData`: A structured object mirroring all categories and fields from PRD REQ-APP-056.
            *   `currentNoticeDetails`: Object to hold title, editor content, selected template/file for Tab 2.
            *   `activeNoticeId`: For when an existing notice is being edited (post-MVP) or for passing to Tab 3.
            *   Functions to update `questionnaireData`.
        *   **Task M3.1.3 (Frontend - QuestionnaireTab.js):** Implement the main UI for Tab 1.
        *   **Task M3.1.4 (Frontend - Reusable Accordion Component):** If not already generic, create `QuestionnaireCategoryAccordion.js` for each collapsible section (e.g., "Personal Data to be Processed", "Purposes of Processing", etc. as per PRD REQ-APP-056 A-M).
        *   **Task M3.1.5 (Frontend - Reusable Field Row Component):** Create `QuestionnaireFieldRow.js` for individual data items within accordions.
            *   Props: `fieldId`, `fieldLabel`, `isCustom`, `onSelectChange`, `onReasonChange`, `onLabelEdit`, `onDeleteCustomField`.
            *   Includes checkbox, label (editable if custom), reason textbox.
        *   **Task M3.1.6 (Frontend - Dynamic Category Implementation):** For each category in PRD REQ-APP-056:
            *   Define initial fields.
            *   Implement "Add Custom Field" button logic within each category – updates `questionnaireData` in context.
            *   Implement "Edit Field Label" logic for pre-defined and custom fields – updates `questionnaireData`.
            *   Implement "Delete Custom Field" logic.
        *   **Task M3.1.7 (Frontend - Specific Section Logic):**
            *   **Data Sharing/Third Parties (REQ-APP-056.G):** Implement UI for repeatable groups of [Name, Type, Data Shared, Purpose].
            *   **Children/Disability Data (REQ-APP-056.D):** Ensure clear questions and text areas for Fiduciary to document their processes.
        *   **Task M3.1.8 (Frontend - Navigation & Validation):** Implement "Next" button on Tab 1.
            *   Basic validation (e.g., at least one purpose defined, DPO contact mentioned if that's a hard rule for a notice).
            *   On click, updates `NoticeContext` with all captured `questionnaireData` and switches active tab to Tab 2.
        *   **Task M3.1.9 (Testing):** Rigorous UI testing: ensure all questionnaire interactions work, data is correctly captured in context/state, dynamic fields are manageable. Test responsiveness of accordions.
        *   *(Runnable Checkpoint 3.A after M3.1 completion)*

    *   **M3.2: Notice Module - Type & Preview (Tab 2) - UI & Template/Format Handling (Est. Duration: 5-6 days)** (PRD Ref: REQ-APP-061 to REQ-APP-068)
        *   **Task M3.2.1 (Backend - API for Templates):** `templateController.js` (or new `noticeSupportController.js`): Implement `GET /api/app/templates/by-industry`.
            *   Takes `organisationId` (from `req.user` to get `IndustryID`) or `industryId` directly.
            *   Returns active `Template` records (`TemplateID`, `TemplateName`, `TemplateBody`, `TemplatePath`) for that industry (and possibly global templates).
        *   **Task M3.2.2 (Frontend - NoticePreviewTab.js):** Implement Tab 2 UI.
        *   **Task M3.2.3 (Frontend - Template Selection):** "Select Existing Template" MUI `Select` dropdown.
            *   On component mount or industry change, fetch templates using API from Task M3.2.1.
            *   On selection, update `NoticeContext.currentNoticeDetails` with `selectedTemplateId`, `templateBody` (pre-fills editor), `templateFileName`.
        *   **Task M3.2.4 (Frontend - Custom Format Upload):** "Upload Notice Format" `<input type="file">` (accept .pdf, .docx).
            *   On file selection, store the `File` object and its name in `NoticeContext.currentNoticeDetails.uploadedCustomFormat`. Clear any selected template info.
        *   **Task M3.2.5 (Frontend - Text Editor):** Integrate MUI `TextField` (multiline, minRows, maxRows) or `react-quill` if chosen.
            *   Value bound to `NoticeContext.currentNoticeDetails.editorContent`. `onChange` updates context.
        *   **Task M3.2.6 (Frontend - Questionnaire Data Display Box):** Implement the read-only, formatted display of `questionnaireData` from `NoticeContext` as per PRD REQ-APP-065.
            *   This requires a utility function to format the `questionnaireData` object into the specified string representation.
        *   **Task M3.2.7 (Frontend - Input Fields):** "Notice Title Prefix" text input, "Primary Language of this Notice" dropdown (default "English", options for Eighth Schedule languages). Update `NoticeContext`.
        *   **Task M3.2.8 (Frontend - Preview Modal):** "Preview Notice" button opens a modal displaying content based on PRD REQ-APP-068.
        *   **Task M3.2.9 (Testing):** Test template fetching and selection, custom file upload (storing file object), editor binding, questionnaire data display, preview modal.

    *   **M3.3: Notice Module - Notice Saving & File Generation (Tab 2 - Backend & Frontend Integration) (Est. Duration: 5-6 days)** (PRD Ref: REQ-APP-069)
        *   **Task M3.3.1 (Backend - Controller & Service):** `noticeController.js`, `noticeService.js`. Design and implement `POST /api/app/notices/save-notice` endpoint.
            *   Use `multer` middleware for handling `uploadedNoticeFormatFile` if present.
        *   **Task M3.3.2 (Backend - Service Logic - `saveNotice`):**
            *   Input validation: `noticeTitlePrefix`, `editorContent`, `primaryLanguage`, `questionnaireDataSnapshot` string, `selectedTemplateId` or `uploadedNoticeFormatFile`.
            *   **Versioning:** Call `noticeService.getNextVersionNumber(organisationId, noticeTitlePrefix)`.
            *   Construct `FinalNoticeName`.
            *   **DB Insert:** Create record in `Notice` table. `NoticeBody` = `editorContent`. `QuestionnaireDataSnapshot` = formatted string. `NoticeType` based on template/upload.
            *   **File System Operations:**
                *   If `uploadedNoticeFormatFile`: Save this file to `GeneratedNotices/[OrgID]/[FinalNoticeName].ext`.
                *   Else (template body used): Save `editorContent` as `GeneratedNotices/[OrgID]/[FinalNoticeName].txt`. (Stretch: basic PDF from text using `pdf-lib`).
                *   Update `Notice.FolderLocation` with the path.
            *   Return the new `NoticeID` and `Notice` object.
        *   **Task M3.3.3 (Backend):** Implement `noticeService.getNextVersionNumber` (queries DB).
        *   **Task M3.3.4 (Backend):** Comprehensive unit tests for `noticeService.saveNotice` including versioning, DB interaction, and file system operation mocks.
        *   **Task M3.3.5 (Frontend - Save Logic):** `NoticePreviewTab.js`: "Save & Next" button's `onClick` handler.
            *   Gathers all necessary data from `NoticeContext.currentNoticeDetails` and `NoticeContext.questionnaireData` (format it).
            *   Construct `FormData` if `uploadedCustomFormat` file exists.
            *   Call `noticeApiService.saveNotice`.
            *   On success: Update `NoticeContext.activeNoticeId` with returned `NoticeID`. Show success `SnackbarNotification`. Navigate to Tab 3. Handle errors.
        *   **Task M3.3.6 (Testing):** Full E2E for Tab 1 data -> Tab 2 composition -> Save. Verify: DB `Notice` record created correctly (all fields, version). File saved correctly in `GeneratedNotices/OrgID/` with correct name and content.
        *   *(Runnable Checkpoint 3.B after M3.3 completion)*

    *   **M3.4: Notice Module - Translation (Tab 3) - UI, Dummy API & File Operations (Est. Duration: 5-6 days)** (PRD Ref: REQ-APP-070 to REQ-APP-075)
        *   **Task M3.4.1 (Backend - API for Translation):** `noticeController.js`, `noticeService.js`: `POST /api/app/notices/:noticeId/translate`.
            *   Input: `targetLanguageCodes` array in request body. `noticeId` from path.
            *   `noticeService.translateNotice(noticeId, targetLanguageCodes, organisationId)`:
                *   Fetch original `Notice` record by `noticeId` (verify it belongs to `organisationId`).
                *   Read content from `Notice.NoticeBody` or file at `Notice.FolderLocation`.
                *   Loop through `targetLanguageCodes`: Simulate translation (prepend lang code). Construct `TranslatedFileName`. Save to `NoticesTranslated/[OrgID]/[TranslatedFileName]`.
                *   Return array of `{ languageName, languageCode, translatedFilePath, translatedFileName }`.
        *   **Task M3.4.2 (Backend - API for Downloads):** `noticeController.js`:
            *   `GET /api/app/notices/:noticeId/download-original`: Serves file from `Notice.FolderLocation`.
            *   `GET /api/app/notices/download-translated?filePath=...`: Serves specified translated file. Validate `filePath` belongs to user's org for security.
        *   **Task M3.4.3 (Backend):** Unit tests for `noticeService.translateNotice` (dummy logic, file ops mocks) and download controllers.
        *   **Task M3.4.4 (Frontend - TranslationTab.js):**
            *   On load (receives/fetches `activeNoticeId` from `NoticeContext`), call `GET /api/app/notices/:noticeId` to fetch original notice details for the "Original Document" tile.
        *   **Task M3.4.5 (Frontend - NoticeTile Component):** Create `src/app/notice/components/NoticeTile.js`.
            *   Props: `title`, `version` (optional), `language`, `downloadPdfPath` (optional), `downloadDocxPath` (optional), `downloadTxtPath` (optional).
            *   Displays info and relevant download buttons. Download buttons will call API service functions.
            *   Use for original notice tile.
        *   **Task M3.4.6 (Frontend - Language Selection):** Implement language list with checkboxes, "Select All", highlight IndicTrans2 as per PRD REQ-APP-072.
        *   **Task M3.4.7 (Frontend - Translate Action):** "Translate" button: Collect selected `targetLanguageCodes`. Call `noticeApiService.translateNotice(activeNoticeId, codes)`.
        *   **Task M3.4.8 (Frontend - Display Translated Tiles):** On successful translation API response, map results to `NoticeTile` components and display them.
        *   **Task M3.4.9 (Frontend - Download Service):** `noticeApiService.js`: Add functions for `downloadOriginalNotice(noticeId)` and `downloadTranslatedNotice(filePath)` which trigger file downloads.
        *   **Task M3.4.10 (Testing):** UI for language selection. Trigger dummy translation. Verify translated tiles appear. Test download for original and all dummy translated files (check content).

    *   **M3.5: Phase 3 Integration, Comprehensive Testing & Review (Est. Duration: 3-4 days)**
        *   **Task M3.5.1 (E2E Workflow Testing):** Test the entire Notice Module flow:
            *   Fill comprehensive questionnaire in Tab 1.
            *   Tab 2: Select an admin template, edit content, add title, save. Verify DB/file.
            *   Tab 2 (separate test): Upload custom format, add title, save. Verify DB/file.
            *   Tab 3: Translate the saved notice into multiple languages. Download original and all translated versions. Verify file names and (dummy) content.
            *   Test versioning by creating another notice with the same title prefix.
        *   **Task M3.5.2 (API Testing):** Update and execute Postman collection for all Notice module APIs.
        *   **Task M3.5.3 (Code Review):** Thorough peer code reviews for all backend and frontend components of the Notice module. Focus on state management, file handling, API interactions, and UI consistency.
        *   **Task M3.5.4 (Documentation):** Document Notice module APIs, complex frontend state flows, and any specific configurations. Update `README.md` if necessary.
        *   **Task M3.5.5 (KPI Verification):** Verify all KPIs for Phase 3 are met.
        *   *(Runnable Checkpoint 3.C / End of Phase)*
   

Phase 4: External Request Page & DPR/Grievance Management Modules (Est. Duration: 6-7 Weeks)
* Goal: Implement the full lifecycle for Data Principal Requests (DPRs) and Grievances, starting from submission by external Data Principals via a dedicated, organisation-specific portal, through to internal management, tracking, status updates, and history logging by Organisation Users. Integrate these request counts and escalations into the main Dashboard.
* KPIs for Phase 4:
* KPI 4.1 (External Page Access & Auth): External Request Page is accessible via unique org URLs. The (dummy) external user login/identification flow is functional. Organisation name is correctly displayed.
* KPI 4.2 (External Submission Success): Data Principals can successfully submit both DPRs (all defined types) and Grievances via the external forms. Submitted data is accurately and securely saved to respective DB tables (DPRequests, Grievances), correctly linked to the Organisation, and an initial history record (DPRequestHistory, GrievanceHistory) is created.
* KPI 4.3 (SLA Calculation): ExpectedCompletionDate (SLA-based) is accurately calculated and stored for all new DPRs and Grievances upon submission.
* KPI 4.4 (Internal Listing & Filtering - DPR & Grievance): Organisation Users can view comprehensive, paginated, searchable, and filterable lists of DPRs and Grievances for their organisation. Status count tiles are functional.
* KPI 4.5 (Internal Detail View & History - DPR & Grievance): Organisation Users can view the full details of any DPR/Grievance, including its complete, chronological, and accurately attributed history trail.
* KPI 4.6 (Internal Update & Processing - DPR & Grievance): Authorised Organisation Users can update the status (including closure with mandatory comments which logs ClosedAt and CompletedOnTime) and reassign (OrgAdmins) DPRs/Grievances. All changes are correctly logged to the respective history table.
* KPI 4.7 (Dashboard Integration): The main application Dashboard dynamically and accurately reflects current counts of DPRs/Grievances by status and lists escalated items based on overdue ExpectedCompletionDate.
* KPI 4.8 (API Coverage & Testing): 100% Backend API coverage for all DPR, Grievance, and supporting external page functionalities. All new/updated APIs documented and successfully tested via Postman/Insomnia.
* KPI 4.9 (Unit Test Coverage): Backend service layers (dprService.js, grievanceService.js, relevant parts of externalControllerService.js) achieve >70% unit test coverage.
* Runnable Checkpoint 4.A (Target: Mid-Phase, Est. Week 2-3):
* Demonstrable: External Request Page UI complete (dummy login, org name display, navigation to forms). DPR & Grievance submission forms are functional and successfully save data to backend (DB tables DPRequests, Grievances, DPRequestHistory, GrievanceHistory are populated correctly with initial entries and calculated ExpectedCompletionDate).
* Verification: Manual E2E testing of external submission for both DPR and Grievance. DB data validation. API testing for submission endpoints.
* Runnable Checkpoint 4.B (Target: Mid-Phase, Est. Week 4-5):
* Demonstrable: DPR Management Module within the main application is fully operational: Listing page (with filters, search, pagination, status tiles), Detail View (displaying all request info and full history trail), and Update functionality (status change, assignment by OrgAdmin, closure with comments).
* Verification: Manual E2E testing of internal DPR management. API testing for DPR CRUD and history endpoints.
* Runnable Checkpoint 4.C (Target: End of Phase, Week 6-7):
* Demonstrable: Grievance Management Module is fully operational, mirroring DPR functionality. The main Dashboard is dynamically updated with real DPR/Grievance data, including accurate escalation lists. All Phase 4 KPIs are met.
* Verification: Full E2E testing of Grievance module and Dashboard integration. Final review of all Phase 4 features. Code reviews complete. Documentation updated.

     *   **Milestones:**

    *   **M4.1: External Request Page - Setup, Org Info, (Dummy) Auth & Navigation (Est. Duration: 4-5 days)** (PRD Ref: REQ-EXT-001 to REQ-EXT-008)
        *   **Task M4.1.1 (Backend - Org Info API):** `externalController.js`: Implement `GET /api/external/organisation-info/:identifier`.
            *   Service logic to find `Organisation` by the `identifier` (e.g., UUID part of `RequestPageURL`). Return `BusinessName`. Handle invalid identifier error.
        *   **Task M4.1.2 (Frontend - Layout & Routing):**
            *   Create `src/layouts/ExternalPageLayout.js` (minimalistic, professional layout).
            *   Update `App.js` routing: `/request/:orgIdentifier` -> `CreateRequestLandingPage.js`; `/request/:orgIdentifier/dpr` -> `ExternalDPRFormPage.js`; `/request/:orgIdentifier/grievance` -> `ExternalGrievanceFormPage.js`. All use `ExternalPageLayout`.
        *   **Task M4.1.3 (Frontend - Dummy Login):** `src/external/ExternalLoginPage.js`:
            *   UI for Email/Password. "Login" button.
            *   On "Login", store email in a simple client-side state/context accessible by subsequent external pages for pre-filling. No backend call for login itself. Redirect to `CreateRequestLandingPage` with `orgIdentifier`.
        *   **Task M4.1.4 (Frontend - Landing Page):** `src/external/CreateRequestLandingPage.js`:
            *   Extract `orgIdentifier` from URL. Call `/api/external/organisation-info/` to fetch and display Org Name.
            *   Buttons "Raise Data Principal Request" and "Log a Grievance" navigate to respective form URLs.
        *   **Task M4.1.5 (Testing):** Test accessing page with valid/invalid `orgIdentifier`. Test dummy login flow. Test navigation to (empty) form pages.

    *   **M4.2: External Request Page - DPR & Grievance Form Implementation & Backend Submission Logic (Est. Duration: 6-7 days)** (PRD Ref: REQ-EXT-009 to REQ-EXT-020)
        *   **Task M4.2.1 (Frontend - DPR Form):** `src/external/ExternalDPRFormPage.js`:
            *   Implement form UI with all fields per PRD REQ-EXT-009. Email pre-filled from dummy login state. Client-side validation (mandatory, email format).
        *   **Task M4.2.2 (Frontend - Grievance Form):** `src/external/ExternalGrievanceFormPage.js`:
            *   Implement form UI with all fields per PRD REQ-EXT-014. Email pre-filled. Client-side validation.
        *   **Task M4.2.3 (Backend - DPR Submission):** `externalController.js` (or `dprController.js`), `dprService.js`: `POST /api/external/dpr/submit`.
            *   Controller: Validate request body (using a validation middleware or in-controller). Extract `org_identifier`.
            *   Service `dprService.createDprFromExternal(data, orgIdentifier)`:
                *   Find `OrganisationID` from `orgIdentifier`. Handle not found.
                *   Determine initial `AssignedToUserID` (OrgAdmin of the `OrganisationID` - requires query on `Users` table).
                *   Fetch `RequestStatusID` for 'Submitted' and its `SLA_Days` from `RequestStatus` table.
                *   Calculate `ExpectedCompletionDate` = `NOW()` + `SLA_Days`.
                *   Insert new record into `DPRequests` table.
                *   Get the new `DPRequestID`.
                *   Insert initial entry into `DPRequestHistory` (`Comment`: "Request submitted via external portal.", `ChangedByUserID`: NULL or system ID, `NewStatusID`: 'Submitted').
        *   **Task M4.2.4 (Backend - Grievance Submission):** `externalController.js` (or `grievanceController.js`), `grievanceService.js`: `POST /api/external/grievances/submit`. Similar logic as DPR submission, for `Grievances` and `GrievanceHistory` tables.
        *   **Task M4.2.5 (Backend):** Robust unit tests for `dprService.createDprFromExternal` and `grievanceService.createGrievanceFromExternal` covering data insertion, history creation, SLA calculation, and error handling.
        *   **Task M4.2.6 (Frontend - Form Submission Logic):** Implement `onSubmit` handlers in `ExternalDPRFormPage.js` and `ExternalGrievanceFormPage.js`.
            *   Collect form data. Call respective backend submission APIs using `axios` or fetch.
            *   Handle API success: Disable form, show success message (PRD REQ-EXT-013, REQ-EXT-017).
            *   Handle API errors: Display user-friendly error messages.
        *   **Task M4.2.7 (Testing):** API testing for both submission endpoints with valid and invalid data. Full E2E testing of submitting DPRs (all types) and Grievances from the external UI. Verify data accurately saved in all relevant DB tables (`DPRequests`, `Grievances`, `DPRequestHistory`, `GrievanceHistory`). Verify `ExpectedCompletionDate`.
        *   *(Runnable Checkpoint 4.A after M4.2 completion)*

    *   **M4.3: DPR Management Module (Main App) - Listing & Filtering (Est. Duration: 4-5 days)** (PRD Ref: REQ-APP-076 to REQ-APP-082)
        *   **Task M4.3.1 (Backend - List DPRs API):** `dprController.js`, `dprService.js`: Enhance/Implement `GET /api/app/dpr`.
            *   Scoped to `req.user.organisationId`.
            *   Implement server-side filtering: `statusId`, `assignedToUserId`, `requestType`, `creationDateFrom`, `creationDateTo`.
            *   Implement server-side pagination (`page`, `limit`) and sorting (by any displayed column).
            *   Join with `Users` (for `AssignedToName`) and `RequestStatus` (for `StatusName`).
        *   **Task M4.3.2 (Backend - Status Counts API):** `dprController.js`, `dprService.js`: Implement `GET /api/app/dpr/status-counts`.
            *   Scoped to `req.user.organisationId`. Returns counts of DPRs for each active status.
        *   **Task M4.3.3 (Backend):** Unit tests for `dprService.listDprs` (including filter logic) and `getStatusCounts`.
        *   **Task M4.3.4 (Frontend - DPR Listing Page):** `src/app/dpr/DPRListingPage.js`:
            *   Fetch status counts and render clickable status tiles (e.g., using MUI `Chip` or `Card`). Clicking a tile applies a status filter to the DataTable.
            *   Implement UI for all filter controls: Status dropdown (multi-select or single), AssignedTo dropdown (populate with Org users via `GET /api/app/users`), RequestType dropdown, DateRangePicker.
            *   "Apply Filters" and "Clear Filters" buttons.
        *   **Task M4.3.5 (Frontend - DataTable Integration):** Integrate `DataTableWrapper` to display DPRs.
            *   Columns as per PRD REQ-APP-081. `ExpectedCompletionDate` cell should be conditionally styled if overdue (current date > expected date and status not Closed).
            *   Pass filter values, pagination state, sort state to API calls. Update DataTable when API responds.
        *   **Task M4.3.6 (Frontend - Navigation):** Row click in DataTable navigates to `DPRDetailPage` with `dprId` as a route parameter.
        *   **Task M4.3.7 (Testing):** API testing for `/api/app/dpr` with all filter combinations, pagination, sorting. Frontend: test filter UI, data table population, sorting, pagination, navigation to detail page.

    *   **M4.4: DPR Management Module (Main App) - Detail View & History Trail (Est. Duration: 4-5 days)** (PRD Ref: REQ-APP-083, REQ-APP-087 to REQ-APP-089)
        *   **Task M4.4.1 (Backend - Get DPR Details API):** `dprController.js`, `dprService.js`: Enhance/Implement `GET /api/app/dpr/:dprId`.
            *   Service logic: Fetch specific DPR by ID, ensuring it belongs to `req.user.organisationId`.
            *   Join with `Users` (for `AssignedToName`), `RequestStatus` (for `CurrentStatusName`).
            *   Fetch all associated `DPRequestHistory` records, ordered by `ChangedAt` (e.g., descending). Join `DPRequestHistory` with `Users` (for `ChangedByName`) and `RequestStatus` (for `PreviousStatusName`, `NewStatusName`).
        *   **Task M4.4.2 (Backend):** Unit tests for `dprService.getDprDetailsWithHistory`.
        *   **Task M4.4.3 (Frontend - DPR Detail Page):** `src/app/dpr/DPRDetailPage.js`:
            *   Fetch DPR details and history using `dprId` from route params on component mount.
            *   Display all DPR fields in logically grouped sections as per PRD REQ-APP-083 (Requester Info, Request Details, Processing Info).
        *   **Task M4.4.4 (Frontend - Reusable History Trail Component):** Create `src/components/RequestHistoryTrail.js`.
            *   Props: `historyItems` (array).
            *   Renders a chronological list (e.g., MUI `List` or `Timeline`) of history entries, formatted as per PRD REQ-APP-089.
            *   Integrate this component into `DPRDetailPage.js` to display the fetched history.
        *   **Task M4.4.5 (Testing):** API test for detail endpoint. Frontend: verify all DPR details and full history trail are correctly displayed for various DPRs.

    *   **M4.5: DPR Management Module (Main App) - Update Functionality (Est. Duration: 4-5 days)** (PRD Ref: REQ-APP-084 to REQ-APP-086, REQ-APP-090, REQ-APP-091)
        *   **Task M4.5.1 (Backend - Update DPR API):** `dprController.js`, `dprService.js`: Enhance/Implement `PUT /api/app/dpr/:dprId`.
            *   Middleware: `protectOrgUser`. Controller further checks `CanEdit` permission from `req.user` if not `OrgAdmin`. `OrgAdmin` can always edit/assign.
            *   Inputs: `newStatusId`, `newAssignedToUserId` (only if updater is `OrgAdmin`), `closureComment`.
            *   Service `dprService.updateDpr(dprId, data, performingUserId, organisationId)`:
                *   Fetch existing DPR. Verify it belongs to `organisationId`.
                *   If `newStatusId` is 'Closed': `closureComment` is mandatory. Set `ClosedAt = NOW()`. Calculate `CompletedOnTime` by comparing `ClosedAt` with `ExpectedCompletionDate`.
                *   Update fields in `DPRequests` table.
                *   Create detailed entry in `DPRequestHistory` table (log old/new status, old/new assignee, closure comment, `performingUserId`). Ensure this is transactional with the `DPRequests` update.
        *   **Task M4.5.2 (Backend - Add Manual Note API - Optional):** `POST /api/app/dpr/:dprId/notes`.
            *   Inputs: `commentText`. Service adds only to `DPRequestHistory` with `performingUserId`.
        *   **Task M4.5.3 (Backend):** Unit tests for `dprService.updateDpr` (various scenarios: status change, assignment, closure, permission checks).
        *   **Task M4.5.4 (Frontend - DPR Detail Page Enhancements):** `DPRDetailPage.js`:
            *   Make Status dropdown editable. Populate with active statuses from `GET /api/admin/request-statuses`.
            *   Make AssignedTo dropdown editable *only if logged-in user is `OrgAdmin`*. Populate with users from `GET /api/app/users`.
            *   Conditionally display mandatory ClosureComment `TextField` if 'Closed' status is selected.
            *   "Update Request" button: Collects changes, calls `PUT /api/app/dpr/:dprId`. Refresh data on success. Show `SnackbarNotification`.
            *   (Optional) "Add Internal Note" button and modal to call notes API.
        *   **Task M4.5.5 (Testing):** API testing for update/notes. Frontend: Test all update scenarios by OrgAdmin and authorized OrgUser. Verify history logging. Test closure logic.
        *   *(Runnable Checkpoint 4.B after M4.5 completion)*

    *   **M4.6: Grievance Management Module - Full Implementation (Main App) (Est. Duration: 5-6 days)** (PRD Ref: REQ-APP-092 to REQ-APP-108)
        *   **Task M4.6.1 (Backend):** Create `grievanceController.js`, `grievanceService.js`. Implement all APIs mirroring the DPR module, but for `Grievances` and `GrievanceHistory` tables.
            *   `GET /api/app/grievances` (list with filters: status, assignedTo, date range - NO requestType)
            *   `GET /api/app/grievances/status-counts`
            *   `GET /api/app/grievances/:grievanceId` (details + history)
            *   `PUT /api/app/grievances/:grievanceId` (update: status, assignment, closure)
            *   `POST /api/app/grievances/:grievanceId/notes` (optional manual note)
        *   **Task M4.6.2 (Backend):** Comprehensive unit tests for `grievanceService.js`.
        *   **Task M4.6.3 (Frontend):** Create `src/app/grievances/GrievanceListingPage.js` and `src/app/grievances/GrievanceDetailPage.js`.
            *   Adapt UI and logic heavily from corresponding DPR module components.
            *   Remove "Request Type" filter and display from Grievance views.
            *   Use the reusable `RequestHistoryTrail.js` component.
        *   **Task M4.6.4 (Testing):** Full API and frontend E2E testing for the entire Grievance module lifecycle. Ensure consistency with DPR module behavior.

    *   **M4.7: Dashboard Integration - Real Data for DPR & Grievances (Est. Duration: 2-3 days)** (PRD Ref: REQ-APP-016 to REQ-APP-036 related to DPR/Grievance stats & escalations)
        *   **Task M4.7.1 (Backend - Update Dashboard API):** Modify `GET /api/app/dashboard/summary` (`dashboardService.js`):
            *   Remove dummy data logic.
            *   Call `dprService.getStatusCounts(organisationId)` and `grievanceService.getStatusCounts(organisationId)`.
            *   Implement `dprService.getEscalatedDprs(organisationId)` and `grievanceService.getEscalatedGrievances(organisationId)` to query items where `ExpectedCompletionDate < GETDATE()` AND status is not 'Closed'. Select key fields for dashboard display.
            *   Structure the API response with real data for charts and escalated item tables.
        *   **Task M4.7.2 (Frontend - Update Dashboard Page):** `DashboardPage.js`:
            *   Ensure `StatusPieChart.js` and `EscalatedItemsTable.js` components correctly consume and display the real data from the updated API.
            *   Implement `onItemClick` for rows in `EscalatedItemsTable.js` to navigate to the respective DPR/Grievance detail page.
        *   **Task M4.7.3 (Testing):** Thoroughly test dashboard accuracy with various data scenarios: no requests, few requests, many requests, items becoming escalated, items being closed and removed from escalation. Test navigation from escalated items table.

    *   **M4.8: Phase 4 Integration, Comprehensive Testing & Review (Est. Duration: 3-4 days)**
        *   **Task M4.8.1 (Integration Testing):** Rigorously test all E2E flows involving external page, DPR module, Grievance module, and Dashboard.
            *   Example flow: External user submits DPR -> OrgAdmin sees it on dashboard/DPR list -> Assigns to OrgUser -> OrgUser updates status -> OrgAdmin sees history -> OrgUser closes DPR -> Dashboard reflects updated counts and DPR removed from escalation if applicable.
        *   **Task M4.8.2 (API Documentation & Collection):** Consolidate and finalize Postman/Insomnia collection for all Phase 1-4 APIs.
        *   **Task M4.8.3 (E2E Scenario Documentation & Execution):** Document key E2E test scenarios and execute them.
        *   **Task M4.8.4 (Code Review):** Conduct thorough peer code reviews for all Phase 4 backend and frontend code. Pay attention to data consistency, security of external endpoints, permission enforcement.
        *   **Task M4.8.5 (Documentation Update):** Update `README.md` and any API documentation.
        *   **Task M4.8.6 (KPI Verification):** Verify all KPIs for Phase 4 are met.
        *   *(Runnable Checkpoint 4.C / End of Phase)*
   
Phase 5: RoPA, Compliance Docs, Tasks & Final Polish (Est. Duration: 5-6 Weeks)
* Goal: Deliver the remaining core DPDPA accountability modules: Record of Processing Activities (RoPA) with manual input and structured viewing/export, Compliance Documentation management with folder/file operations, and a Basic Task Management system. Conduct comprehensive final testing across the entire application, perform UI/UX polishing, and prepare the MVP for pilot deployment.
* KPIs for Phase 5:
* KPI 5.1 (RoPA Functionality): RoPA module allows Organisation Users to manually create, view detailed structured data, edit, and delete RoPA entries capturing all PRD-defined elements. RoPA data is exportable to CSV and a basic, readable PDF.
* KPI 5.2 (Compliance Docs Functionality): Compliance Documentation module fully supports folder creation, and file (various common types) upload/download/deletion by Organisation Users within their scoped storage. Metadata for documents is tracked. Quick links to generated/translated notices and applicable templates are functional.
* KPI 5.3 (Task Management Functionality): Basic Task Management module allows Organisation Users to create, assign (to org users), update status, and delete general compliance tasks.
* KPI 5.4 (Application Stability & NFRs): The entire MVP application is stable, performs acceptably under typical MVP load, and key Non-Functional Requirements (Usability, Basic Security, Browser Compatibility) are met.
* KPI 5.5 (E2E Testing): All major end-to-end user scenarios across all modules pass without critical or high-priority issues.
* KPI 5.6 (Documentation): Comprehensive README.md for development environment setup and basic application operation is complete and validated. A list of known MVP limitations is documented.
* KPI 5.7 (API Coverage & Testing): 100% Backend API coverage for all Phase 5 features. All APIs documented and successfully tested via Postman/Insomnia.
* KPI 5.8 (Unit Test Coverage): Backend service layers for RoPA, Compliance Docs, and Tasks achieve >70% unit test coverage.
* Runnable Checkpoint 5.A (Target: Mid-Phase, Est. Week 2-3):
* Demonstrable: RoPA Module: Full CRUD for RoPA entries, structured data view. Basic PDF/CSV export functional. Compliance Documentation Module: Basic UI for listing files/folders, backend APIs for file/folder operations are complete and tested.
* Verification: Manual E2E testing of RoPA CRUD and export. API testing for RoPA and initial Compliance Docs backend.
* Runnable Checkpoint 5.B (Target: End of Phase - MVP Candidate, Week 5-6):
* Demonstrable: Full Compliance Documentation module functionality (UI for upload, create folder, delete, download, quick links). Basic Task Management module complete. All UI/UX polishing across the application finished. All Phase 5 KPIs met. The application is pilot-ready.
* Verification: Full E2E testing of all MVP features. Final NFR checks. Code reviews complete. Documentation finalized.

     *   **Milestones:**

    *   **M5.1: Record of Processing Activities (RoPA) Module - Backend (Est. Duration: 4-5 days)** (PRD Ref: REQ-APP-109 to REQ-APP-113, REQ-APP-116, REQ-APP-117, REQ-APP-122)
        *   **Task M5.1.1 (DB):** Create and finalize `RoPAEntries` table schema.
        *   **Task M5.1.2 (Backend - Controller & Service):** Create `src/controllers/ropaController.js`, `src/services/ropaService.js`.
        *   **Task M5.1.3 (Backend API - CRUD):**
            *   `POST /api/app/ropa/activities`: Create new RoPA entry. Service validates input, stores structured data (e.g., JSONB/NVARCHAR(MAX) for arrays like Data Processors).
            *   `GET /api/app/ropa/activities`: List RoPA entries for Org (paginated, searchable by `ProcessingActivityName` / `Purpose`, filterable by key RoPA elements like `LawfulBasis`).
            *   `GET /api/app/ropa/activities/:activityId`: Get details of a specific RoPA entry.
            *   `PUT /api/app/ropa/activities/:activityId`: Update RoPA entry.
            *   `DELETE /api/app/ropa/activities/:activityId`: Delete RoPA entry.
        *   **Task M5.1.4 (Backend API - Export):** Implement `GET /api/app/ropa/export?format=csv` and `GET /api/app/ropa/export?format=pdf`.
            *   Service logic to fetch all RoPA data for the Org.
            *   For CSV: Convert RoPA data (flattening JSON arrays where necessary) into CSV format string. Set appropriate `Content-Type` and `Content-Disposition` headers.
            *   For PDF (Basic): Use a server-side library (e.g., `pdfmake` or generate HTML and convert with `puppeteer` - if feasible for MVP; simpler text-based PDF using `pdf-lib` might be more realistic) to generate a structured, readable PDF document.
        *   **Task M5.1.5 (Backend):** Comprehensive unit tests for `ropaService.js` covering CRUD, data validation, and export formatting logic.
        *   **Task M5.1.6 (Testing):** API contract testing (Postman) for all RoPA endpoints, including export with different formats.

    *   **M5.2: Record of Processing Activities (RoPA) Module - Frontend (Est. Duration: 5-6 days)** (PRD Ref: REQ-APP-111 to REQ-APP-117, REQ-APP-119 to REQ-APP-121)
        *   **Task M5.2.1 (Frontend - Listing Page):** `src/app/ropa/RoPAListingPage.js`:
            *   "Add New Processing Activity" button.
            *   Filter controls (e.g., by Lawful Basis, or search by Activity Name/Purpose).
            *   Integrate `DataTableWrapper` to list RoPA entries (Key columns: Activity Name, Main Purpose(s), Lawful Basis, Last Updated).
            *   Row click navigates to view/edit mode (could be same form component). Export buttons (CSV, PDF) trigger API calls.
        *   **Task M5.2.2 (Frontend - Form Component):** `src/app/ropa/RoPAForm.js` (used for create/edit, potentially in a modal or separate route):
            *   Implement form with all fields as per PRD REQ-APP-112 (a-o). Use MUI `Accordion` or `Tabs` for logical grouping of the many fields.
            *   Implement repeatable sub-forms for "Data Processors Involved", "Third-Party Fiduciaries", "Cross-Border Transfers" (allow adding/removing multiple entries).
            *   For "Data Processors Involved", include a text field for "DPA Document Reference/Location" (manual input linking to Compliance Docs, PRD REQ-APP-120).
            *   Integrate DPA Checklist (PRD REQ-APP-121) as an informational MUI `Tooltip` or helper text near the Data Processors section.
        *   **Task M5.2.3 (Frontend - View Component):** `src/app/ropa/RoPAView.js` (or integrated display logic within `RoPAForm.js` when in read-only mode):
            *   Present a single RoPA entry's data in a well-structured, highly readable format, clearly labeling each RoPA element (PRD REQ-APP-115).
        *   **Task M5.2.4 (Frontend - Service & State):** Create `src/services/ropaApiService.js`. Manage form state and data fetching/submission logic.
        *   **Task M5.2.5 (Testing):** Full frontend E2E testing of RoPA CRUD operations. Verify structured data display. Test CSV and PDF export functionality (download and basic content check).

    *   **M5.3: Compliance Documentation Module - Backend File & Metadata Operations (Est. Duration: 4-5 days)** (PRD Ref: REQ-APP-123 to REQ-APP-135, REQ-APP-142)
        *   **Task M5.3.1 (DB):** Create and finalize `OrganisationDocuments` table schema.
        *   **Task M5.3.2 (Backend - Controller & Service):** Create `src/controllers/complianceDocController.js`, `src/services/complianceDocService.js`.
        *   **Task M5.3.3 (Backend API - List):** `GET /api/app/documents?path=...`:
            *   Service logic to list files and folders from `OrganisationSpecificDocs/[OrgID]/[current_relative_path]`.
            *   For files, join with `OrganisationDocuments` to fetch metadata (`UploadedByUserID` (join to get name), `UploadedAt`, `Description`, `FileSize`). For folders, just list name and type.
        *   **Task M5.3.4 (Backend API - Create Folder):** `POST /api/app/documents/create-folder` (Input: `folderName`, `parentPath`). Creates directory on file system.
        *   **Task M5.3.5 (Backend API - Upload File):** `POST /api/app/documents/upload?path=...` (Use `multer` for file handling).
            *   Service: Save file to specified path. Insert record into `OrganisationDocuments` (FileName, FilePath, FileType, FileSize, UploadedByUserID, UploadedAt, optional Description).
        *   **Task M5.3.6 (Backend API - Delete):** `DELETE /api/app/documents` (Input: `itemPath`, `itemType`).
            *   Service: Delete file/folder from file system. If file, delete from `OrganisationDocuments`. If folder, delete all contained files' metadata from `OrganisationDocuments` then remove folder.
        *   **Task M5.3.7 (Backend API - Download):** `GET /api/app/documents/download?filePath=...`. Securely serves the specified file.
        *   **Task M5.3.8 (Backend - Quick Link APIs):**
            *   `GET /api/app/documents/quicklinks/generated-notices`: Lists files from `GeneratedNotices/[OrgID]/`.
            *   `GET /api/app/documents/quicklinks/translated-notices`: Lists files from `NoticesTranslated/[OrgID]/`.
            *   `GET /api/app/documents/quicklinks/templates`: Lists templates from `TemplateRepo/` (filtered by Org industry).
        *   **Task M5.3.9 (Backend):** Unit tests for `complianceDocService.js` (file system interactions mocked, DB interactions).
        *   **Task M5.3.10 (Testing):** Comprehensive API testing for all document/folder operations, including path validation and security.
        *   *(Runnable Checkpoint 5.A after M5.2 and M5.3 completion)*

    *   **M5.4: Compliance Documentation Module - Frontend UI & Interactions (Est. Duration: 5-6 days)** (PRD Ref: REQ-APP-136 to REQ-APP-141)
        *   **Task M5.4.1 (Frontend - Page Structure):** `src/app/complianceDocs/ComplianceDocsPage.js`:
            *   Implement breadcrumb navigation for current path.
            *   "Upload File(s)" button (triggers file input, then calls API). "New Folder" button (opens modal for folder name).
        *   **Task M5.4.2 (Frontend - File/Folder Listing):**
            *   Use `DataTableWrapper` or custom list component to display files and folders from API.
            *   Columns/Info: Icon (file/folder type), Name, Size (files only), Last Modified / Uploaded At, Uploaded By, Actions.
            *   Folder name click updates current path and re-fetches content. File name click triggers download.
        *   **Task M5.4.3 (Frontend - Actions):** Implement Download (files) and Delete (files/folders, with `ConfirmationDialog`) actions.
        *   **Task M5.4.4 (Frontend - Service & State):** Create `src/services/complianceDocApiService.js`. Manage current path, file list, loading states.
        *   **Task M5.4.5 (Frontend - Quick Link Sections):** Implement dedicated sections or views within `ComplianceDocsPage.js` to display lists from the "quicklink" APIs (Generated Notices, Translated Notices, Available Templates). These are typically read-only lists with download capability.
        *   **Task M5.4.6 (Testing):** Full E2E testing: folder navigation, creating folders, uploading various file types, downloading files, deleting files and folders. Verify quick links.

    *   **M5.5: Basic Task Management Module (Est. Duration: 3-4 days)** (PRD Ref: REQ-APP-143 to REQ-APP-157)
        *   **Task M5.5.1 (DB - If new table):** Create `GeneralTasks` table schema (as outlined previously).
        *   **Task M5.5.2 (Backend):** `taskController.js`, `taskService.js`: Implement CRUD APIs for `GeneralTasks`, scoped by `OrganisationID`.
            *   `POST /api/app/tasks`
            *   `GET /api/app/tasks` (with filters: Status, AssignedTo, DueDate)
            *   `PUT /api/app/tasks/:taskId`
            *   `DELETE /api/app/tasks/:taskId`
        *   **Task M5.5.3 (Backend):** Unit tests for `taskService.js`.
        *   **Task M5.5.4 (Frontend - Listing Page):** `src/app/tasks/TaskListingPage.js`:
            *   "Add New Task" button. Filter controls. `DataTableWrapper` to list tasks.
        *   **Task M5.5.5 (Frontend - Form Modal):** `src/app/tasks/TaskFormModal.js`: Form fields for Task (Title, Description, AssignedTo (dropdown of org users), DueDate, Priority, Status).
        *   **Task M5.5.6 (Frontend - Service & Logic):** `taskApiService.js`. Implement frontend CRUD operations.
        *   **Task M5.5.7 (Testing):** API and frontend CRUD testing for Tasks. Verify filters.

    *   **M5.6: Comprehensive UI/UX Polish & NFR Adherence Review (Est. Duration: 4-5 days)** (PRD Ref: Section 5 NFRs)
        *   **Task M5.6.1 (UI Consistency Audit):** Walk through every page and module. Check for consistent MUI component usage, themes (light/dark), typography, spacing, iconography, button styles, modal behaviors, form layouts, table presentations.
        *   **Task M5.6.2 (Responsiveness Checks):** Test across key desktop resolutions. Ensure major layouts adapt gracefully. Basic checks on tablet-sized views.
        *   **Task M5.6.3 (Error Handling & Feedback Review):** Verify that all forms have appropriate validation, user-friendly error messages are displayed for both client-side and server-side errors, loading indicators are used for all async operations, and success notifications are consistent.
        *   **Task M5.6.4 (Usability Heuristic Evaluation):** Perform informal usability testing with team members acting as different user personas, focusing on key task flows. Identify and address major usability pain points (e.g., confusing navigation, unclear labels, inefficient workflows).
        *   **Task M5.6.5 (Accessibility Audit - Basic):** Run automated accessibility checkers (e.g., Axe DevTools browser extension). Manually check keyboard navigation for all interactive elements, semantic HTML usage, and color contrast for critical text.
        *   **Task M5.6.6 (Performance Spot-Checks):** Identify any pages or operations that feel noticeably sluggish. Investigate and apply basic optimizations (e.g., reducing re-renders in React, optimizing backend queries if an obvious issue is found).
        *   **Task M5.6.7 (Cross-Browser Testing):** Test key functionalities on latest stable versions of Chrome, Firefox, Edge, Safari (macOS).
        *   **Task M5.6.8 (Content Review):** Review all static text, labels, tooltips, and messages for clarity, correctness, and consistency.
        *   **Task M5.6.9 (Bug Fixing Marathon):** Address all critical, high, and medium priority bugs identified throughout development and during this polishing phase.

    *   **M5.7: Final End-to-End (E2E) Testing & Pilot Preparation (Est. Duration: 4-5 days)**
        *   **Task M5.7.1 (E2E Test Case Suite Execution):** Develop a suite of comprehensive E2E test cases covering all major user flows and inter-module interactions from the perspective of each user role (SystemAdmin, OrgAdmin, OrgUser, External Requester). Execute this full suite.
            *   *Example Complex Scenario:* SysAdmin onboards OrgX. OrgAdmin of OrgX logs in, creates an OrgUser. OrgUser fills Notice Questionnaire, generates a Notice. External Requester submits a DPR to OrgX. OrgUser for OrgX processes the DPR to closure. OrgAdmin reviews RoPA entries and uploads a DPA to Compliance Docs for a processor mentioned in RoPA.
        *   **Task M5.7.2 (Data Integrity & Boundary Testing):** Test with edge cases, invalid inputs, and large data sets (within MVP reasonable limits) to check for data integrity issues or unexpected behavior.
        *   **Task M5.7.3 (Security Review - Final MVP Check):** Final review against MVP security NFRs (HTTPS, password hashing, RBAC enforcement, basic XSS/SQLi prevention).
        *   **Task M5.7.4 (Pilot User Account Setup):** If specific accounts or pre-seeded data are needed for pilot users, prepare these.
        *   **Task M5.7.5 (Pilot Onboarding Material - Draft):** Draft basic onboarding guide or talking points for pilot users.

    *   **M5.8: Documentation & MVP Handoff Preparation (Est. Duration: 2-3 days)**
        *   **Task M5.8.1 (README.md Finalization):** Ensure `README.md` is complete, accurate, and validated for Prerequisites, Backend Setup, DB Setup (including seeding), Frontend Setup, Running the Application, Default Credentials, and a brief overview of key module operations.
        *   **Task M5.8.2 (API Documentation Consolidation):** Finalize Postman/Insomnia collection for all MVP APIs. Consider generating a simple API reference document (e.g., Markdown from Postman descriptions or basic Swagger UI if stubs were created).
        *   **Task M5.8.3 (Known Limitations & Deferred Features Document):** Compile a formal list of all known non-critical bugs, MVP limitations (e.g., dummy services, no MFA), and features explicitly deferred to post-MVP (from PRD Section 9). This manages expectations for the pilot.
        *   **Task M5.8.4 (Deployment Scripts/Steps - Basic Pilot):** Document clear, step-by-step instructions for deploying the MVP backend, frontend, and database to a simple pilot environment (e.g., a single server or basic cloud VMs). Include any environment variable configurations needed for pilot.
        *   **Task M5.8.5 (Code Freeze & Final Build):** Branch for MVP release. Perform final build of frontend assets.
        *   **Task M5.8.6 (Internal Handoff/Knowledge Transfer):** Ensure all team members understand the final state of the MVP, deployment steps, and how to support pilot users.
        *   *(Runnable Checkpoint 5.B / MVP Candidate / End of Phase)*
   

