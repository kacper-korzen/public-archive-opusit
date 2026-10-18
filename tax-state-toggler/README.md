# tax-state-toggler(TaxStateToggler)

## Problem

In the **INFO SYSTEM**, when printing documents, it was necessary to change the tax parameters in several database components simultaneously and then restore them to their previous state.

Manually changing these parameters through the application interface was:
- **Time-consuming** — each parameter required a separate click
- **Prone to errors** — it was easy to change the wrong parameter or forget to restore a value
- **Not repeatable** — there was no quick way to perform this operation in the future

---

## Solution

I created a **console application** in C# that automates the entire process:

1. **Connection validation** — checks access to the Firebird database
2. **Data retrieval** — collects data from the user about the system and the component
3. **Consistency verification** — before updating, checks whether all components have the same parameter type
4. **Atomic update** — updates the parameters in the database using an SQL query
5. **Security** — if the parameters differ between components, the application **warns the user** and refuses to make the change, requiring manual verification

---

## Stack

- **Language**: C#
- **.NET Framework**: 4.8
- **Database Driver**: FirebirdSql.Data.FirebirdClient v10.3.4
- **Configuration**: System.Configuration.ConfigurationManager v10.0.10

---

## Roles & Decisions

**My role**: Problem analysis, logic design

**Key decisions**:
- **CLI instead of GUI** — faster integration, easy automation
- **Consistency validation** — protection against unintended changes; the program warns the user and halts the operation instead of blindly modifying data
- **Configuration Manager** — connection parameters stored in a configuration file, not in the code

---

## Effect

- ✅ **Fully automated process** — instead of manual changes for each component
- ✅ **Secure** — parameter consistency verified before changes
- ✅ **Repeatable** — one command = complete operation
- ⏱️ **Time savings** — reduced from dozens of clicks to a single command