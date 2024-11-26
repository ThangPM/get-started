# Setting up SSH for GitHub

This guide explains how to set up SSH authentication for GitHub.

1. Create a new SSH key by opening terminal and running:
```bash
ssh-keygen -t ed25519 -C "your@email.com"
```

When prompted, press Enter to save the key in the default location. Optionally set a passphrase for extra security.

2. Start the SSH agent:
```bash
eval "$(ssh-agent -s)"
```

3. Add the new key to the agent:
```bash
ssh-add ~/.ssh/id_ed25519
```

4. Copy the public key. The command varies by operating system:

Mac:
```bash
pbcopy < ~/.ssh/id_ed25519.pub
```

Linux:
```bash
xclip -sel clip < ~/.ssh/id_ed25519.pub
```

Windows (PowerShell):
```powershell
Get-Content ~/.ssh/id_ed25519.pub | Set-Clipboard
```

5. Add the key to GitHub:
- Navigate to GitHub.com → Settings (from profile dropdown)
- Select "SSH and GPG keys" → "New SSH key"
- Enter a descriptive title (e.g., "Work Laptop")
- Paste the copied public key
- Click "Add SSH key"

6. Test the connection:
```bash
ssh -T git@github.com
```

A success message should appear with the GitHub username. SSH is now configured and ready for use with Git repositories.
