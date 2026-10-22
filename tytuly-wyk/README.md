# tytuly-wyk(SQL Server XML Import)

Minimalist Python automation for importing enforcement orders into a database

## Problem

One of the government agencies identified a lack of access to archived enforcement orders. It was necessary to migrate this data to a database and make it available through the interface.

## Solution

I developed **a minimal automation script in Python** that:

1. **Reads the configuration** — retrieves the database connection details and the path to the XML files
2. **Validates the connection** — tests access to the database
3. **Creates the structure** — adds a new column to the database to store the titles
4. **Imports data** — scans the directory and inserts the contents into the database


## Stack

- **Python** 
- **SQL Server** (database engine)
- **uv** (package manager)

---

## Roles & Decisions

**Why Python?**
- Fast implementation, ready-made libraries for XML and SQL
- Easy configuration management (`.ini` file)

**Why a separate column?**
- Isolation of archived data from the current structure
- Transparency—we'll preserve the history of operations

**Why validate the connection?**
- Early detection of configuration errors
- Saves debugging time in production

**Error handling:**
- Check for the existence of the config file


## Effect

 **Access:** Officials can now view archived records in the system
 **Maintenance:** The script can be run again without duplicating data (idempotent)

---