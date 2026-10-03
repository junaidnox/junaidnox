# PowerShell Downloader Behavior

PowerShell is a legitimate Windows administration tool. Attackers and unsafe scripts often abuse it because it can download content, execute code, interact with Windows APIs, and run with elevated permissions.

## Common Pattern

A suspicious downloader usually follows this flow:

1. Force or configure network security settings
2. Define a remote URL
3. Download content from the URL
4. Save the content into a temporary path
5. Execute the downloaded file
6. Delete the temporary file

## Defensive Interpretation

Each step creates a different detection opportunity.

| Script Action | Defensive Question |
|---|---|
| Sets TLS protocol | Is this normal for the script's purpose? |
| Downloads from the internet | Is the domain trusted and expected? |
| Writes to Temp | Why is executable content being placed there? |
| Starts a new process | What child process was created? |
| Waits for completion | Is this a staged installer or a loader pattern? |
| Deletes the file | Is the script trying to reduce evidence? |

## Suspicious Indicators

- `Invoke-WebRequest`
- `Invoke-RestMethod`
- `iwr`
- `irm`
- `Start-Process`
- `-UseBasicParsing`
- Random file names
- Execution from `%TEMP%` or `C:\Windows\Temp`
- Download followed by immediate execution

## Analyst Notes

Do not judge the script by one command only. Build the timeline:

```text
network connection -> file write -> process creation -> registry change -> cleanup
```

That sequence is stronger than a single alert.
