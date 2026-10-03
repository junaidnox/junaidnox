# Windows Registry Abuse Analysis

A defensive cybersecurity lab for studying suspicious Windows script behavior, registry permission abuse, temporary script execution, and PowerShell downloader patterns.

This project is built for blue-team learning, malware-analysis practice, and Windows hardening research. It focuses on behavior, detection, and defense.

## Scope

This lab explains how suspicious Windows scripts commonly:

- Download remote code through PowerShell
- Save temporary files with random names
- Request administrator privileges
- Scan Windows Registry paths
- Modify Registry Access Control Lists
- Remove temporary artifacts after execution

## What This Project Does Not Provide

This project does not provide software activation, license bypassing, piracy tools, crack scripts, or instructions for avoiding payment for commercial software.

The goal is to understand risky behavior so defenders can identify and block it.

## Repository Structure

```text
windows-registry-abuse-analysis/
├── README.md
├── analysis/
│   ├── powershell-downloader.md
│   ├── registry-acl-abuse.md
│   └── suspicious-script-indicators.md
├── detections/
│   ├── sigma-powershell-download.yml
│   └── windows-event-ids.md
├── defense/
│   └── hardening-checklist.md
├── labs/
│   └── safe-analysis-workflow.md
└── screenshots/
```

## Why This Matters

Many unsafe Windows scripts are small and readable, but they still perform high-risk actions. A script may look simple while quietly downloading code, executing from temporary folders, changing permissions, and deleting traces.

Blue-team analysts should know how to break this behavior into observable events.

## Example Suspicious Behaviors

| Behavior | Why It Matters |
|---|---|
| Downloads script from a remote URL | Common in loaders, unsafe installers, and post-exploitation tooling |
| Saves into a Temp directory | Often used for short-lived execution |
| Uses random file names | Makes tracking and allowlisting harder |
| Checks for administrator rights | Indicates a need for system-level changes |
| Modifies Registry permissions | Can block normal software or security controls |
| Deletes itself after execution | Reduces forensic evidence |

## Learning Outcomes

After completing this lab, you should understand how to:

- Explain PowerShell downloader behavior
- Identify suspicious temporary execution
- Recognize Registry ACL tampering
- Map suspicious script actions to Windows logs
- Write basic detection logic
- Build a safer analysis workflow

## Suggested Use

Use this repository as a defensive study project. Add screenshots from your own isolated lab, write notes in your own words, and keep every example focused on detection and hardening.
