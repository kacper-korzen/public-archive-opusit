# migration-selects-runner(MigrationSelectsRunner)

Automated Firebird SQL query execution with HTML report generation and preview. This project was developed independently, using AI tools to assist with coding and documentation.

## Problem

Upgrading to a new version of the INFO SYSTEM software required manually running a series of SQL queries in Firebird and verifying the results. The process was time-consuming, prone to operator errors, and required repeatedly switching between tools.

---

## Solution

I built a desktop application that:

- **Configures a connection** to a Firebird database once
- **Dynamically generates buttons** for each SQL query
- **Executes queries** directly from the interface
- **Generates HTML reports** with the results
- **Displays reports** in a built-in WebView without opening a browser
- **Signals errors** by changing the button color

---

## Stack

| Component           | Technology                         | Role                        |
|---------------------|------------------------------------|-----------------------------|
| **AI Assistant**    | Claude, Gemma 4                    | Dev-time code support       |
| **C#**              | —                                  | Application logic           |
| **WPF**             | —                                  | Desktop UI                  |
| **FirebirdSql.Data.FirebirdClient** | 10.3.4          | Database connection         |
| **Microsoft.Web.WebView2** | 1.0.4258.31               | HTML report preview         |
| **System.Configuration.ConfigurationManager** | 10.0.12 | Connection config |
| **System.Text.Encoding.CodePages** | 8.0.0                 | Character encoding          |
---

## Roles & Decisions

- **Dynamic button generation** — each SQL query is a separate button, allowing for easy addition of new queries without recompilation
- **WebView2 instead of a browser** — eliminates dependence on external tools; everything is contained within a single application window
- **Button color changes upon error** — visual feedback on query status (instead of reading a text error message in the console)
- **Configuration separate from the code** — easily change connection parameters without modifying the application

---

## Effect

- ⏱️ **Significant time savings** when running a series of queries
- ✅ **Reduction in operator errors** — no need to manually copy queries
- 📊 **Automatic report generation** — saves time spent manually compiling results
- 🎨 **Better UX** — visual error feedback, all in one tool
