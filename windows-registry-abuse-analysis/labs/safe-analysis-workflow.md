# Safe Analysis Workflow

This workflow is for studying suspicious Windows scripts without publishing bypass tools or running unsafe code on your main system.

## Lab Setup

Use:

- A Windows virtual machine
- No personal accounts
- Snapshot before testing
- Microsoft Defender enabled
- Sysmon installed
- PowerShell logging enabled

## Before Running Any Script

1. Save a copy for static review
2. Identify remote URLs
3. Identify file write paths
4. Identify process execution commands
5. Identify Registry operations
6. Identify cleanup commands

## Static Review Checklist

Look for:

- Download commands
- Encoded commands
- Obfuscated variables
- Administrator checks
- Registry commands
- Permission changes
- Self-deletion

## Dynamic Review Checklist

If you run a script in a lab, capture:

- Process tree
- Network connections
- Files created
- Registry keys touched
- Security alerts
- PowerShell logs

## Report Format

Use this format for each analyzed script:

```text
Script name:
Source:
Purpose claimed by author:
Observed behavior:
Risk rating:
Important commands:
Files created:
Registry changes:
Network activity:
Detection ideas:
Hardening advice:
```
