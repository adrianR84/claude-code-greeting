---
name: greeting
description: Greet the user with a personalized message using your configured settings. Use when the user wants to be greeted or asks for a hello.
---

# Greeting Plugin

A customizable greeting plugin with user-configurable settings.

## Current Settings

| Setting | Value | Description |
|---------|-------|-------------|
| `userName` | ${user_config.userName} | Your name for personalized greetings |
| `greetingStyle` | ${user_config.greetingStyle} | formal, friendly, casual, or enthusiastic |
| `includeTime` | ${user_config.includeTime} | Whether to show the current time |

---

## /greeting-plugin:greeting

Greet the user with a personalized message based on configured settings.

**Usage:** `/greeting-plugin:greeting`

**Behavior:**
1. Read the user's configured `userName` and `greetingStyle` from settings
2. Determine the appropriate time-of-day phrase based on current hour
3. Generate the greeting matching their style preference
4. Include the current time if `includeTime` is enabled

### Greeting Templates

**Formal:**
"Good [morning/afternoon/evening], ${user_config.userName}. The current time is [TIME]. How may I assist you today?"

**Friendly (default):**
"Hello there, ${user_config.userName}! Hope you're having a wonderful [day/evening]. Current time: [TIME]. What can I help you with?"

**Casual:**
"Hey ${user_config.userName}! [TIME] - perfect timing! What's up?"

**Enthusiastic:**
"GREETINGS ${user_config.userName}!!! It's [TIME] and the possibilities are ENDLESS! How can I make your day AMAZING?!"

---

## Changing Settings

Settings are configured at installation time via prompts. To change them after installation:

1. Open `~/.claude/settings.json` (user scope) or `.claude/settings.json` (project scope)
2. Find the `pluginConfigs` section
3. Update the `greeting-plugin` options:

```json
"pluginConfigs": {
  "greeting-plugin": {
    "options": {
      "userName": "Your Name",
      "greetingStyle": "casual",
      "includeTime": true
    }
  }
}
```

4. Restart Claude Code or use `/reload-plugins`

## Quick Reference

| Action | Command |
|--------|---------|
| Get a greeting | `/greeting-plugin:greeting` |

## Notes

- If no userName is configured, defaults to "Friend"
- Time is displayed in 24-hour format when enabled
- Settings persist across sessions via `settings.json`
