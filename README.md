# Zed Editor Configuration Management

A version-controlled approach to managing Zed editor settings and keymaps using symlinks.

## Overview

This repository contains my Zed editor configuration files that are symlinked to the actual Zed configuration directory. This approach allows for:

- Version control of editor settings
- Easy backup and restoration of configurations
- Sharing configurations across multiple machines
- Tracking changes to editor preferences over time

## Files Included

- `dotfiles/settings.json` - Main Zed editor settings
- `dotfiles/keymap.json` - Custom key bindings for Zed
- `README.md` - This documentation

## Setup Instructions

### Prerequisites

- Zed editor installed on your system
- Git for version control
- Basic familiarity with symlinks

### Installation

1. **Clone this repository** (or navigate to it if already cloned):
   ```bash
   cd ~/path/to/hegarty/zed
   ```

2. **Backup existing Zed configuration** (if any):
   ```bash
   # Create backup directory
   mkdir -p ~/.config/zed/backup

   # Backup existing files
   cp ~/.config/zed/settings.json ~/.config/zed/backup/settings.json.backup 2>/dev/null || true
   cp ~/.config/zed/keymap.json ~/.config/zed/backup/keymap.json.backup 2>/dev/null || true
   ```

3. **Remove existing configuration files**:
   ```bash
   rm -f ~/.config/zed/settings.json
   rm -f ~/.config/zed/keymap.json
   ```

4. **Create symlinks to this repository**:
   ```bash
   # Create the Zed config directory if it doesn't exist
   mkdir -p ~/.config/zed

   # Create symlinks
   ln -s $(pwd)/dotfiles/settings.json ~/.config/zed/settings.json
   ln -s $(pwd)/dotfiles/keymap.json ~/.config/zed/keymap.json
   ```

5. **Verify the symlinks**:
   ```bash
   ls -la ~/.config/zed/
   ```

   You should see output similar to:
   ```
   settings.json -> /path/to/hegarty/zed/dotfiles/settings.json
   keymap.json -> /path/to/hegarty/zed/dotfiles/keymap.json
   ```

## Current Configuration Highlights

### Settings (`settings.json`)

- **Theme**: GitHub Dark
- **Font**: Monaspace Neon (UI and buffer)
- **Font Sizes**: 16px UI, 14px buffer < I'm old, large font
- **Vim Mode**: Enabled
- **Agent**: Claude Sonnet 4 via Zed.dev
- **Features**: Copilot disabled, edit predictions disabled
- **UI**: Minimal toolbar, no scrollbars, project panel on left

### Keymaps (`keymap.json`)

Currently contains template structure with commented examples for:
- Workspace-level bindings
- Editor-level bindings
- Custom key combinations (like `shift shift` for file finder)

## Usage

### Making Changes

1. **Edit configuration files** in this repository:
   ```bash
   # Edit settings
   vim dotfiles/settings.json

   # Edit keymaps
   vim dotfiles/keymap.json
   ```

2. **Changes take effect immediately** in Zed (no restart required for most settings)

3. **Commit your changes**:
   ```bash
   git add dotfiles/
   git commit -m "Update Zed configuration: describe your changes"
   git push
   ```

### Restoring Configuration

If you need to restore your configuration on a new machine:

1. Clone this repository
2. Follow the installation steps above
3. Restart Zed to ensure all settings are loaded

### Removing Symlinks

If you want to revert to local configuration files:

```bash
# Remove symlinks
rm ~/.config/zed/settings.json
rm ~/.config/zed/keymap.json

# Restore from backup (if available)
cp ~/.config/zed/backup/settings.json.backup ~/.config/zed/settings.json 2>/dev/null || true
cp ~/.config/zed/backup/keymap.json.backup ~/.config/zed/keymap.json 2>/dev/null || true
```
