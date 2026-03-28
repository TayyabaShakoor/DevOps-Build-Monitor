# Database Schema - DevOps Build Monitor

## Table: users

| Column | Type | Constraints | Description |
|--------|------|-------------|-------------|
| id | BIGSERIAL | PRIMARY KEY | Auto-generated unique identifier |
| username | VARCHAR(50) | NOT NULL, UNIQUE | User's display name |
| email | VARCHAR(100) | NOT NULL, UNIQUE | User's email address |
| password | VARCHAR(255) | NOT NULL | BCrypt hashed password |
| role | VARCHAR(20) | NOT NULL | ADMIN, DEVELOPER, or VIEWER |
| created_at | TIMESTAMP | DEFAULT NOW() | Account creation timestamp |

## Table: pipelines

| Column | Type | Constraints | Description |
|--------|------|-------------|-------------|
| id | BIGSERIAL | PRIMARY KEY | Auto-generated unique identifier |
| name | VARCHAR(100) | NOT NULL | Display name for the pipeline |
| type | VARCHAR(20) | NOT NULL | JENKINS, GITHUB, or GITLAB |
| url | VARCHAR(500) | NOT NULL | API endpoint URL |
| api_token | VARCHAR(500) | NOT NULL | Encrypted API token |
| is_active | BOOLEAN | DEFAULT TRUE | Whether pipeline is being monitored |
| created_at | TIMESTAMP | DEFAULT NOW() | Pipeline creation timestamp |

## Table: builds

| Column | Type | Constraints | Description |
|--------|------|-------------|-------------|
| id | BIGSERIAL | PRIMARY KEY | Auto-generated identifier |
| pipeline_id | BIGINT | FOREIGN KEY | References pipelines.id |
| build_number | VARCHAR(50) | NOT NULL | External build identifier |
| status | VARCHAR(20) | NOT NULL | SUCCESS, FAILED, IN_PROGRESS, PENDING, ABORTED |
| duration | INTEGER | | Duration in seconds |
| commit_id | VARCHAR(40) | | Git commit hash |
| commit_message | TEXT | | Git commit message |
| author | VARCHAR(100) | | Commit author name |
| started_at | TIMESTAMP | | When build started |
| finished_at | TIMESTAMP | | When build completed |
| logs_url | VARCHAR(500) | | API endpoint to fetch logs |
| created_at | TIMESTAMP | DEFAULT NOW() | Record creation timestamp |

## Sample Query: Get recent builds for dashboard

```sql
SELECT b.*, p.name as pipeline_name, p.type as pipeline_type
FROM builds b
JOIN pipelines p ON b.pipeline_id = p.id
WHERE p.is_active = true
ORDER BY b.started_at DESC
LIMIT 50;
