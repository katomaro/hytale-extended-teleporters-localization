# Localization Guide - ExtendedTeleportHistory

## Overview

This (https://legacy.curseforge.com/hytale/mods/no-teleporters-limit) mod uses Hytale's native translation system to support multiple languages. All user-facing text is stored in `.lang` files that are automatically loaded based on the player's client language.

## File Structure

```
Server/Languages/
├── en-US/
│   └── hytale.extendedteleport.lang  (English - Default)
└── pt-BR/
    └── hytale.extendedteleport.lang  (Brazilian Portuguese)
```

## Translation File Format

### Basic Syntax

```properties
# Comments start with #
translation.key = Translation text

# Parameters use {paramName} syntax DO NOT TRANSLATE PARAMETERS NAMES
msg.limit.total = You have reached your teleporter limit ({current}/{max}).
gui.location = Location: {dimension} ({x}, {y}, {z})

# Multi-word keys use dot notation
gui.title = Teleporter Settings
cmd.trust.success = Added {name} as trusted on "{teleporter}"
```

### Key Naming Convention

- `gui.*` - GUI elements (titles, labels, buttons, placeholders)
- `cmd.*` - Command responses and messages
- `msg.*` - General messages (errors, warnings, success, info)
- `error.*` - Error messages

### Parameter Naming

Use descriptive, lowercase parameter names:
- `{name}` - Player or teleporter names
- `{current}`, `{max}` - Limits and counts
- `{x}`, `{y}`, `{z}` - Coordinates
- `{dimension}`, `{world}` - World names
- `{minutes}`, `{seconds}` - Time values

## Adding a New Language

### Step 1: Create Language File

1. Create folder: `src/main/resources/Server/Languages/{locale}/`
   - Examples: `es-ES` (Spanish), `fr-FR` (French), `de-DE` (German)
2. Create file: `hytale.extendedteleport.lang`

### Step 2: Copy and Translate

1. Copy `en-US/hytale.extendedteleport.lang` to your new language folder
2. Translate ONLY the text after the `=` sign
3. Keep all parameter placeholders like `{name}`, `{max}` where they should appear, etc.
4. Preserve section headers (lines starting with `#`)

### Step 3: Done

1. Send a Pull Request and wait.

## Translation Guidelines

### ✅ DO:
- **Keep parameter names exactly as they appear**: `{name}`, `{current}`, `{max}`
- Maintain consistent tone and terminology throughout
- Use UTF-8 encoding for special characters (accents, emoji, etc.)
- Keep translations concise for GUI elements

### ❌ DON'T:
- Change or remove parameter placeholders
- Use double quotes `"` or backslashes `\` in translations (breaks JSON)
- Add extra parameters that don't exist in the English version
- Translate parameter names (keep `{name}` not `{nome}`)
- Exceed reasonable length for GUI labels (keep < 30 characters unless you absolutely must)

## Language Fallback Chain

1. **Player's client language** (e.g., `pt-BR`)
2. **Default language** (`en-US`)
3. **Translation key itself** (as last resort)

If a translation key doesn't exist in the player's language, it falls back to English.

## Special Characters

✅ **Allowed**: All Unicode characters, emoji, accented letters, special symbols (`!@#$%^&*()`)

❌ **Forbidden**:
- Double quotes `"` (use single quotes `'` instead)
- Backslashes `\`
- Control characters (invisible characters)

## Translation Categories

### GUI Translations (~40 keys)
- Teleporter settings interface
- Dropdown options
- Button labels
- Info labels and placeholders

### Command Translations (~100 keys)
- `/teleporter list` - List formatting, flags, pagination
- `/teleporter go` - Teleportation messages
- `/teleporter trust/untrust` - Trust management
- `/teleporter destination` - Custom destinations
- `/teleporter server` - Server teleporter management

### Message Translations (~80 keys)
- Permission errors
- Limit warnings
- Warp name validation
- Success/error feedback
- Configuration messages

## Supported Languages

| Language | Code | Status | Translator |
|----------|------|--------|-----------|
| English (US) | `en-US` | ✅ Complete | Katomaro |
| Portuguese (Brazil) | `pt-BR` | ✅ Complete | Katomaro |
| German (DE) | `de-DE` | ✅ Complete | AZB |
| Spanish | `es-ES` | PARTIAL -- The repository was not updated when the translators started | @zonazero y @carre321 |

Temporary note regarding Spanish: totally my fault for not updating the repository. I added the missing keys using DeepL.

## Contributing Translations

To contribute a new language translation:

1. Fork the repository
2. Create your language folder and file
3. Translate all keys (keep parameters intact)
4. Test your translation in-game
5. Submit a pull request with:
   - Language name and code
   - Any special notes about the translation

## Support

Join disocrd on curseforge page.
