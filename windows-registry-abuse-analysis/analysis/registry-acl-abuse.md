# Registry ACL Abuse

The Windows Registry stores configuration for the operating system, applications, users, services, drivers, and security settings.

Access Control Lists control who can read, write, delete, or take ownership of Registry keys.

## Why Registry ACLs Matter

Changing Registry permissions can be legitimate during software installation or system administration. It becomes suspicious when a script changes ownership, denies write access, hides configuration changes, or prevents normal updates.

## Important Terms

| Term | Meaning |
|---|---|
| Registry key | A folder-like object inside the Windows Registry |
| Registry value | A named setting stored under a key |
| ACL | A permission list that controls access |
| ACE | One permission entry inside an ACL |
| Owner | The account or identity that controls permission changes |
| Deny rule | A permission rule that blocks an action |

## Suspicious Permission Changes

Watch for scripts that:

- Take ownership of Registry keys
- Assign ownership to unusual identities
- Add explicit deny rules
- Remove inherited permissions
- Block write access to selected keys
- Change permissions shortly after downloading remote code

## Defensive View

Registry ACL tampering is rarely the first event. It usually appears after process creation and privilege elevation.

Useful timeline:

```text
PowerShell starts -> remote content downloads -> script runs as admin -> Registry keys scanned -> ACLs changed
```

## Why Attackers Like This Technique

Registry permission changes can be used to:

- Protect malicious settings from removal
- Break normal software behavior
- Stop security tools from writing updates
- Preserve unwanted configuration
- Interfere with uninstall or repair actions

## Safe Lab Direction

For public learning, do not publish a working bypass script. Instead, document the behavior pattern, detection points, and hardening steps.
