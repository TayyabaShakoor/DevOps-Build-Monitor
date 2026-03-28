# Functional Requirements - DevOps Build Monitor

## FR1: User Authentication & Authorization

### FR1.1: User Registration
- System shall allow new users to register with email, username, and password
- Password shall be encrypted before storage
- Duplicate email or username shall be rejected

### FR1.2: User Login
- System shall authenticate users using email or username and password
- System shall issue JWT token upon successful login
- Token shall expire after 24 hours

### FR1.3: Role-Based Access Control

| Role | Permissions |
|------|-------------|
| Admin | Full access: Add/Edit/Delete pipelines, Manage users, View all logs |
| Developer | View builds, View logs, Receive notifications |
| Viewer | View-only access to dashboard |

## FR2: Pipeline Management

### FR2.1: Add Pipeline (Admin only)
- Support pipeline types: Jenkins, GitHub Actions, GitLab CI
- Required fields: Name, Type, URL, API Token
- System shall validate connection before saving

### FR2.2: Edit Pipeline (Admin only)
- Update pipeline name, URL, or token
- System shall revalidate connection after update

### FR2.3: Delete Pipeline (Admin only)
- Remove pipeline and all its associated build history

## FR3: Build Monitoring

### FR3.1: Display Builds
- Show all builds from all configured pipelines
- Display: Build ID, Status, Duration, Timestamp, Commit ID, Author

### FR3.2: Status Indicators

| Color | Status | Meaning |
|-------|--------|---------|
| Green | Success | Build passed all tests |
| Red | Failed | Build failed due to errors |
| Yellow | In Progress | Build is currently running |
| Grey | Aborted | Build was manually stopped |
| Blue | Pending | Build waiting in queue |

### FR3.3: Real-time Updates
- Dashboard updates automatically without page refresh
- Updates delivered within 5 seconds of status change
- Uses WebSocket for live updates

## FR4: Build Logs Viewer
- View console output for any build
- One-click access from build card
- Logs displayed in scrollable modal window

## FR5: Analytics & Trends
- Display success vs failure ratio chart (7/14/30 day options)
- Show average build duration trend over time
- Display frequently failing jobs or tests

## FR6: Notifications System

| Type | Trigger | Format |
|------|---------|--------|
| Browser Notification | Build fails or succeeds | Popup with sound |
| Email Alert | Critical build failure | Summary email |
| Sound Alert | Build completes | Beep on failure |
| Dashboard Badge | New events | Counter on icon |

## FR7: Search & Filter
- Filter builds by pipeline name
- Filter by status (Success/Failed/In Progress/Pending)
- Search by commit message or author name
- Search by build number

## FR8: Responsive Design
- Dashboard works on desktop, tablet, and mobile screens
- Navigation adapts to screen size

## FR9: Build Duration Tracking
- Display execution time for each pipeline
- Show duration in format: Xm Ys or Xs for short builds
- Average duration visible in analytics section
