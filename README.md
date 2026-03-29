# Greeting Plugin

A customizable greeting plugin for Claude Code with user-configurable settings.

## Features

- **Personalized greetings**: Uses your configured name
- **Multiple greeting styles**: formal, friendly, casual, or enthusiastic
- **Time-aware**: Optionally includes the current time

## Installation

### Option 1: Local Installation (Testing)

1. Add the local marketplace:

   ```
   /plugin marketplace add ./greeting-plugin
   ```

2. Install the plugin:

   ```
   /plugin install greeting-plugin@example-plugins
   ```

3. Configure your preferences when prompted

### Option 2: From a GitHub Repository

```bash
/plugin marketplace add owner/repo
/plugin install greeting-plugin@marketplace-name
```

### Option 3: Session-Only (No Install)

```bash
claude --plugin-dir ./greeting-plugin
```

## Usage

```
/greeting-plugin:greeting
```

## Configuration

Settings are prompted during installation. The `userConfig` in plugin.json defines:

| Setting         | Description                                           | Default    |
| --------------- | ----------------------------------------------------- | ---------- |
| `userName`      | Your name for personalized greetings                  | "Friend"   |
| `greetingStyle` | Greeting tone: formal, friendly, casual, enthusiastic | "friendly" |
| `includeTime`   | Include the current time in greetings                 | true       |

### Greeting Styles

- **formal**: "Good morning/afternoon/evening, [Name]. The current time is [TIME]. How may I assist you today?"
- **friendly**: "Hello there, [Name]! Hope you're having a wonderful [day/evening]. Current time: [TIME]. What can I help you with?"
- **casual**: "Hey [Name]! [TIME] - perfect timing! What's up?"
- **enthusiastic**: "GREETINGS [Name]!!! It's [TIME] and the possibilities are ENDLESS! How can I make your day AMAZING?!"

## Changing Settings After Installation

Settings are stored in `settings.json`. To change them:

1. Open `~/.claude/settings.json` (user scope)
2. Find or add `pluginConfigs.greeting-plugin.options`:

```json
"pluginConfigs": {
  "greeting-plugin": {
    "options": {
      "userName": "Your Name",
      "greetingStyle": "casual"
    }
  }
}
```

3. Restart Claude Code or use `/reload-plugins`

## Files Structure

```
greeting-plugin/
├── .claude-plugin/
│   ├── plugin.json        # Plugin manifest with userConfig schema
│   └── marketplace.json   # Marketplace listing
├── skills/
│   └── greeting/
│       └── SKILL.md       # Skill definition
└── README.md
```

## How User Configuration Works

The `userConfig` section in `plugin.json` defines configurable settings that are prompted at enable time:

```json
"userConfig": {
  "userName": {
    "description": "Your name for personalized greetings",
    "sensitive": false,
    "default": "Friend"
  }
}
```

Values are:

- Prompted during plugin enable
- Stored in `settings.json` under `pluginConfigs[<plugin-id>].options`
- Available as `${user_config.KEY}` in skill content
- Exported as `CLAUDE_PLUGIN_OPTION_<KEY>` environment variables

## License

MIT
