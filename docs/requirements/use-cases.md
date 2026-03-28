# Use Cases - DevOps Build Monitor

## Actors

| Actor | Description |
|-------|-------------|
| Admin | Full system access, can manage pipelines and users |
| Developer | Can view builds and logs, receive notifications |
| Viewer | Read-only access to dashboard |

## Use Cases

| ID | Use Case | Actor | Description |
|----|----------|-------|-------------|
| UC-01 | Register User | Admin | Admin creates new user accounts |
| UC-02 | Login | All | User authenticates to access dashboard |
| UC-03 | Add Pipeline | Admin | Admin configures new CI/CD pipeline |
| UC-04 | Edit Pipeline | Admin | Admin modifies existing pipeline configuration |
| UC-05 | Delete Pipeline | Admin | Admin removes pipeline and its data |
| UC-06 | View Dashboard | All | View all builds with status indicators |
| UC-07 | View Build Logs | Admin, Developer | Click to view console output |
| UC-08 | Filter Builds | All | Filter builds by pipeline or status |
| UC-09 | Search Builds | All | Search by commit message or author |
| UC-10 | View Analytics | All | View charts showing build trends |
| UC-11 | Receive Notifications | Admin, Developer | Get alerts on build failures |
| UC-12 | Logout | All | Securely end session |

## Detailed Use Case: UC-06 View Dashboard

**Actor:** All users
**Pre-condition:** User is logged in
**Steps:**
1. Dashboard loads all pipelines
2. Build cards display with color-coded status
3. WebSocket connection establishes for live updates
4. Dashboard refreshes automatically on status changes

**Post-condition:** User sees current build statuses
