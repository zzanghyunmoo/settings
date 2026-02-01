# Claude Code Setup Guide

This guide covers installing and configuring Claude Code with Z.AI GLM Coding Plan.

## 📋 Prerequisites

- **Node.js**: Version 18 or newer
- **macOS**: Use [nvm](https://nodejs.org/en/download/) to avoid permission issues
- **Windows**: Install [Git for Windows](https://git-scm.com/download/win)

## 📦 Installation

### Option 1: Recommended (npm)
```bash
# Install Claude Code globally
npm install -g @anthropic-ai/claude-code

# Navigate to your project
cd your-awesome-project

# Start Claude Code
claude
```

### Option 2: Coding Tool Helper (Automated)
```bash
# Run interactive helper
npx @z_ai/coding-helper
```

## ⚙️ Configuration

Claude Code stores configuration in `~/.claude/settings.json`. You need to configure the following environment variables:

### Using Script (macOS/Linux)
The automated setup script handles this automatically:

```bash
curl -O https://cdn.bigmodel.cn/install/claude_code_zai_env.sh && bash ./claude_code_zai_env.sh
```

**What it does:**
- Creates or updates `~/.claude/settings.json`
- Sets up environment variables for Z.AI API
- Configures model mappings (GLM-4.7 for Sonnet/Opus, GLM-4.5-Air for Haiku)

### Manual Configuration
If you prefer to configure manually, edit `~/.claude/settings.json`:

```json
{
  "env": {
    "ANTHROPIC_AUTH_TOKEN": "your_zai_api_key",
    "ANTHROPIC_BASE_URL": "https://api.z.ai/api/anthropic",
    "API_TIMEOUT_MS": "3000000"
  }
}
```

**Important:**
- Replace `your_zai_api_key` with your actual Z.AI API key
- Get your API key from: https://z.ai/manage-apikey/apikey-list
- Open a new terminal window after making changes

### Model Mappings (Optional)

By default, Z.AI GLM Coding Plan uses:
- GLM-4.7 for `sonnet` and `opus` models
- GLM-4.5-Air for `haiku` model

You can customize this in `settings.json`:

```json
{
  "env": {
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "glm-4.7",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "glm-4.7",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "glm-4.7"
  }
}
```

## ✅ Verification

1. Open a new terminal
2. Run `claude`
3. Grant file access permissions when prompted
4. Type `/status` to check configuration
5. Verify model shows GLM-4.7 (or your custom model)

## 🔧 Troubleshooting

### Configuration not taking effect?
- Close all Claude Code windows
- Open a new terminal window
- Verify `~/.claude/settings.json` has correct JSON syntax
- Check that environment variables are properly formatted

### MacOS Permission Issues?
```bash
# Uninstall global package
sudo npm uninstall -g @anthropic-ai/claude-code

# Reinstall using nvm
nvm install node
nvm use <version>
npm install -g @anthropic-ai/claude-code
```

### Need Help?
- Check Z.AI documentation: https://docs.z.ai/scenario-example/develop-tools/claude
- GLM Coding Plan documentation: https://z.ai/subscribe

## 📚 Additional Resources

- [Z.AI Open Platform](https://z.ai/model-api)
- [API Keys Management](https://z.ai/manage-apikey/apikey-list)
- [GLM Coding Plan