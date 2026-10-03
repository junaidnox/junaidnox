# Windows Event IDs For This Lab

Use these events to build a basic investigation timeline.

| Event Source | Event ID | Use |
|---|---:|---|
| Security | 4688 | Process creation |
| Security | 4672 | Special privileges assigned to a new logon |
| Security | 4657 | Registry value modified, when auditing is enabled |
| PowerShell | 4103 | Module logging |
| PowerShell | 4104 | Script block logging |
| Sysmon | 1 | Process creation |
| Sysmon | 3 | Network connection |
| Sysmon | 11 | File created |
| Sysmon | 12 | Registry object created or deleted |
| Sysmon | 13 | Registry value set |
| Sysmon | 14 | Registry object renamed |

## Investigation Timeline

Build the timeline in this order:

1. PowerShell process starts
2. Network request is made
3. Temporary file is created
4. Child process runs
5. Registry key or value changes
6. File cleanup happens

## Useful Fields

- `Image`
- `ParentImage`
- `CommandLine`
- `ParentCommandLine`
- `User`
- `IntegrityLevel`
- `DestinationHostname`
- `TargetFilename`
- `TargetObject`
