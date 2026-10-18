# update-vat-rate(UpdateVatRate)

A console application written in C# used to update VAT rates stored in a Firebird database—automating manual adjustments in the WODA module of the INFO SYSTEM.

---

## Problem

When settling items in the WODA program from INFO SYSTEM, the system automatically assigned an **incorrect VAT rate** to individual items.

Manually correcting this error for multiple accounts presented two problems:
- **Time-consuming**: manual updates required reviewing all entries in the database
- **Permission restrictions**: corrections could not be made via the WODA user interface without elevated database access permissions

This created a bottleneck in the invoicing process and required manual intervention during each correction cycle.

---

## Solution

Built a **standalone C# console tool** that:

1. **Validates database connection** — ensures the Firebird database is accessible before proceeding
2. **Identifies affected accounts** — queries the database for entries with incorrect VAT rates
3. **Executes SQL updates** — applies the correct tax percentage to identified records in a single batch operation
4. **Logs execution** — records success/failure for audit purposes

The application runs as a scheduled task or on-demand, requiring no user interaction beyond triggering it.

---

## Stack

- **Language**: C#
- **Framework**: .NET Framework 4.8
- **Database Driver**: FirebirdSql.Data.FirebirdClient v10.3.4
- **Configuration**: System.Configuration.ConfigurationManager v10.0.10

---

## Role and Decisions

**My Responsibilities:**
- I designed the application architecture and the database connectivity layer
- I implemented error handling for connection failures
- I added configuration management using an external file to store connection strings

**Key Decisions:**
- **Console application** — simplicity and portability
- **External configuration** — easy connection setup by changing the database connection string
- **Connection verification** — early termination of the process if the database was inaccessible, which prevented incomplete updates

---

## Result

**Before:** [~3-5 min] to change the VAT rate to the correct one; with multiple accounts, the time increases with the number of accounts.

**After:** [~2-3 min] — a fully automated adjustment that handles multiple accounts with a single program run.