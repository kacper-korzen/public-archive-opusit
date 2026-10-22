# isagent-update-test-repo(ISAgent Update Test)
Test update panel for the INFOSYSTEM software repository. The platform enables file management on an FTP server (adding and deleting) with secure access via a login system. The code and documentation were developed with the support of AI tools (Claude, Gemma 4).

## Problem

One of INFO SYSTE's other distributors released a new product for **automatically installing software updates on clients' servers** without the need for a remote connection using tools such as TeamViewer or AeroAdmin. The challenge was to:

- Build a system for managing the versions of software available for download
- Creating an interface for managing update files on the server
- Ensuring communication between the administration panel and the update download mechanism
- Enabling local testing before deployment to production

---

## Solution

1. **Administration Panel** (PHP + HTML/CSS/JS)
   - Interface for managing update files (upload/delete)
   - Login system with authentication
 

2. **API** (PHP + SQLite)
   - Customization of the provided API template to work with our own database
   - SQLite as the database for storing software version metadata
   - Customization of SQL queries to retrieve a list of available versions and files

3. **Test Infrastructure** (Docker + Nginx)
   - Containerization for local testing
   - Nginx as a reverse proxy
   - Migration to Apache on the production server with configuration adjustments

---

## Stack

| Component | Technology | Notes |
|-----------|------------|-------|
| Frontend | PHP, HTML5, CSS3, JavaScript | Admin panel |
| Backend | PHP | API and business logic |
| Database | SQLite | Software version metadata |
| Local server | Docker + Nginx | Container testing |
| Production server | Apache | API deployment and testing |
| AI assistance | Claude, Gemma 4 | Code & documentation support |

---

## Roles & Decisions

**My role:**
- Architecture of the entire system (dashboard + API + infrastructure)
- Implementation of the administrative dashboard with AI assistance
- Adaptation of the API template to a SQLite database
- Preparation of Docker + Nginx configurations

**Key Decisions:**

| Decision | Rationale |
|---------|-------------|
| **SQLite instead of a relational DB** | Lightweight, self-contained, ideal for storing version metadata without overly complex infrastructure |
| **Docker for local testing** | Environment isolation, reproducibility; quick verification before production |
| **AI assistance for the dashboard** | Accelerated UI/UX implementation; focus on business logic |
| **Apache in production** | Compatible with the client's infrastructure; configuration options tailored to requirements |

---

## Effect

✅ **Functional dashboard** — administrators can manage updates without SSH access
✅ **Automatic downloads** — customers install updates without intervention
✅ **Testability** — Docker enabled local testing before deployment
✅ **Zero downtime** — migration from Nginx (dev) to Apache (prod) went smoothly
✅ **Scalability** — the API supports new versions without changes to the panel

---

## Technical Details

### Implemented features:
- Update file management (upload/delete)
- Secure login to the admin panel
- Automatic creation of directory structures
- Retrieving version metadata from the API
- Remote updates for INFOSYSTEM customers