# Installing MiniMax Skills for OpenHands

Enable MiniMax skills in OpenHands using the built-in skill system or manual installation.

## Prerequisites

- Git
- OpenHands environment

## Installation

### Option 1: Using `/add-skill` Command (Recommended)

The easiest way to add MiniMax Skills is using the built-in `/add-skill` command:

**Add all skills:**
```
/add-skill https://github.com/MiniMax-AI/skills
```

**Add a specific skill:**
```
/add-skill https://github.com/MiniMax-AI/skills/tree/main/skills/frontend-dev
```

The skills will be installed to `<workspace>/.agents/skills/<skill-name>/`.

### Option 2: Manual Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/MiniMax-AI/skills.git ~/.minimax-skills
   ```

2. **Create the skills symlink:**
   ```bash
   mkdir -p ~/.agents/skills
   ln -s ~/.minimax-skills/skills ~/.agents/skills/minimax-skills
   ```

   **Windows (PowerShell):**
   ```powershell
   New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.agents\skills"
   cmd /c mklink /J "$env:USERPROFILE\.agents\skills\minimax-skills" "$env:USERPROFILE\.minimax-skills\skills"
   ```

3. **Restart OpenHands** to discover the skills.

## Available Skills

- **frontend-dev** — Frontend development with UI design, animations, AI-generated media assets
- **fullstack-dev** — Full-stack backend architecture and frontend-backend integration
- **android-native-dev** — Android native application development with Material Design 3
- **ios-application-dev** — iOS application development with UIKit, SnapKit, and SwiftUI
- **shader-dev** — GLSL shader techniques for stunning visual effects (ShaderToy-compatible)
- **gif-sticker-maker** — Convert photos into animated GIF stickers (Funko Pop / Pop Mart style)
- **minimax-pdf** — Generate, fill, and reformat PDF documents with a token-based design system
- **pptx-generator** — Generate, edit, and read PowerPoint presentations
- **minimax-xlsx** — Open, create, read, analyze, edit, or validate Excel/spreadsheet files
- **minimax-docx** — Professional DOCX document creation, editing, and formatting using OpenXML SDK

## Verify

```bash
ls -la ~/.agents/skills/minimax-skills
```

You should see a symlink (or junction on Windows) pointing to your minimax-skills skills directory.

To verify a specific skill:
```bash
ls ~/.agents/skills/minimax-skills/frontend-dev/SKILL.md
```

## Updating

```bash
cd ~/.minimax-skills && git pull
```

Skills update instantly through the symlink.

## Uninstalling

```bash
rm ~/.agents/skills/minimax-skills
```

Optionally delete the clone: `rm -rf ~/.minimax-skills`.

If you used `/add-skill`, remove the skill directory:
```bash
rm -rf ~/.agents/skills/<skill-name>
```