# tmp-edit

## Description

This script copies a file to the system's temporary directory (`$TMPDIR` or `\tmp`) for editing, helping reduce input lag when editing files on remote mounts (e.g., `sshfs`). After editing, the file is synced back to its original location. This script was designed for MacOS, the script uses `fswatch` to detect changes and automatically sync the file in the background. This allows syncing even while the editor is runing.

This is useful if you are mounting a filesystem using `sshfs` and you want to edit in your preffered editor, which might allow system wide clipboard, configration etc. The main reason is that as `sshfs` uses `ssh` as backend, it is slow, causing input lags and jitters even in the lightest of editors.

## Requirements

- **Bash**: For running the script.
- **An Editor**: Set `$EDITOR` (e.g., `nvim`, `vim`, `nano`).
- **fswatch (macOS)**: Install via Homebrew (`brew install fswatch`).

## Installation and Usage

```bash
chmod +x /path/to/edit
export PATH="$PATH:/path/to/edit"

edit <file_path> 
edit /mnt/sshfs/remote_file.txt
```
