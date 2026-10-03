# Windows Script Hardening Checklist

Use this checklist to reduce risk from unsafe scripts.

## PowerShell Controls

- Enable PowerShell Script Block Logging
- Enable PowerShell Module Logging
- Use Constrained Language Mode where appropriate
- Restrict unsigned scripts with execution policy and application control
- Monitor use of `Invoke-WebRequest`, `Invoke-RestMethod`, and `Invoke-Expression`

## Endpoint Controls

- Use Microsoft Defender or another EDR tool
- Enable cloud-delivered protection
- Block known unsafe script patterns
- Alert on execution from user Temp paths
- Alert on random `.cmd`, `.bat`, and `.ps1` files in Temp

## Windows Registry Controls

- Audit sensitive Registry paths
- Monitor Registry permission changes
- Alert when scripts change ownership or deny rules
- Review unexpected writes under application configuration paths

## Safe User Practice

- Do not run unknown scripts as administrator
- Read scripts before execution
- Avoid shortened URLs for scripts
- Prefer official vendor sources
- Test unknown scripts in a virtual machine

## Analyst Rule

Treat this sequence as high risk:

```text
remote download -> temp file -> admin execution -> registry permission change -> cleanup
```
