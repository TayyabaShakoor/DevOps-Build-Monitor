# DevOps Build Monitor

## A Real-Time CI/CD Pipeline Dashboard

### Overview
This project provides a centralized dashboard to monitor build statuses from multiple CI/CD tools (Jenkins, GitHub Actions, GitLab CI) in real-time.

### Technology Stack
| Layer | Technology |
|-------|------------|
| Frontend | React.js, Bootstrap, Chart.js, Socket.io-client |
| Backend | Spring Boot, Spring Security, WebSocket |
| Database | PostgreSQL |
| Build Tool | Maven |

### Features
- Real-time build status updates via WebSocket
- Multi-pipeline integration (Jenkins, GitHub Actions, GitLab CI)
- Role-based authentication (Admin/Developer/Viewer)
- Build logs viewer
- Historical trends analytics with charts
- Email and browser notifications

### Project Structure
DevOps-Build-Monitor/
├── docs/ # Documentation
├── backend/ # Spring Boot application
├── frontend/ # React application
├── database/ # SQL scripts
└── postman/ # API test collection
