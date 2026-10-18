# users-mail-reporter(FirebirdMailReporter)

## Problem
New users were waiting for manual approval. There was no automatic notification indicating how many were waiting. We had to manually check the database every day and notify the team via email—a time-consuming task that was easy to overlook.

## Solution
A minimalist CLI application in C# that:
1. Connects to a Firebird database
2. Executes an SQL query (SELECT uncommitted users)
3. Formats the result and sends it via email
4. Runs once a day via **Windows Task Scheduler**

No UI, no database—just clean code and two dependencies.

## Stack
- **Language:** C# (.NET 8.0)
- **Database:** Firebird SQL
- **Email sending:** MailKit 4.17.0
- **Database access:** FirebirdSql.Data.FirebirdClient 10.3.4
- **Execution:** Windows Task Scheduler (once a day)

## Roles & Decisions
- **Minimalism** — only essential libraries (Firebird + Mail)
- **Configuration variables** — connection string and SMTP data
- **Error handling** — try-catch at the connection and sending levels, logging to a file
- **Email format** — plain text 
- **Scheduling** — Windows Task Scheduler (fastest integration without additional processes)

## Effect
- ⏱️ **Automation:** 0 minutes of manual work per day (previously ~5-10 min)
- 📧 **Reliability:** Emails are always sent at a fixed time
- 👁️ **Visibility:** The team knows immediately how many new users are awaiting approval
- 🔧 **Maintenance:** No dependencies — easy to modify the SQL query