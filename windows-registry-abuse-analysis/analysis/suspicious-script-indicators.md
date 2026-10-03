# Suspicious Script Indicators

This page lists behaviors that deserve attention during script review.

## High-Value Indicators

| Indicator | Why It Is Suspicious |
|---|---|
| Remote download and immediate execution | May indicate a loader pattern |
| Randomized filename | Makes static detection harder |
| Temp directory execution | Common for short-lived payloads |
| Admin privilege check | Script may need system-level control |
| Registry scanning | May be searching for application or persistence locations |
| ACL modification | Can block removal or hide tampering |
| Self-deletion | Reduces forensic evidence |

## Review Questions

Ask these before running any unknown script:

- Who wrote it?
- Where is it downloading from?
- Does it execute downloaded content?
- Does it require administrator rights?
- Does it modify the Registry?
- Does it change permissions?
- Does it delete logs or temporary files?
- Can the behavior be tested safely in a virtual machine?

## Risk Rating Guide

| Risk | Description |
|---|---|
| Low | Reads local information only |
| Medium | Writes files or changes user-level settings |
| High | Downloads and executes remote code |
| Critical | Runs as admin and changes Registry/security permissions |
