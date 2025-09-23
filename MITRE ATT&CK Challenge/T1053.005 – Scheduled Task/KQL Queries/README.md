
---

### `kql/README.md`
```markdown
# kql/

This folder contains KQL queries and related detection logic for each challenge.

**File format**
- Use `.kql` or `.md` files. Example: `scheduled-task-detection.kql` or `scheduled-task-detection.md`.
- Start each file with a short header including: title, description, data sources, author, and tested environment.

**Template (suggested)**
```kql
// Title: Detect Scheduled Task Creation via schtasks.exe
// Description: Detects invocation of schtasks.exe with /create
// Data sources: DeviceProcessEvents, SecurityEvent
// Author: Paul
// Tested in: Microsoft Sentinel (2025-07)
// Notes: Tune ProcessCommandLine matching for environment specifics

DeviceProcessEvents
| where FileName == "schtasks.exe" and ProcessCommandLine has "/create"
| project TimeGenerated, DeviceName, AccountName, ProcessCommandLine

