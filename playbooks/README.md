# Development Environment Playbooks

This directory contains reusable Ansible playbooks for automating development environment setup tasks.

## 📋 Available Playbooks

- [Claude Code Setup](#claude-setup) - Installing and configuring Claude Code
- [Z.AI Integration Setup](#z-ai-setup) - Configuring Z.AI API integration
- [Environment Configuration](#env-config) - General environment setup

## 📋 Playbook Structure

Each playbook follows a standard Ansible structure with:
- `vars/` - Default variables
- `tasks/` - Main tasks
- `handlers/` - Event handlers
- `meta/` - Metadata

## 📝 Playbook Usage

### Running a Playbook

```bash
# Example: Run Claude Code setup playbook
ansible-playbook -i hosts localhost playbooks/claude-setup.yml

# Example: Run with custom variables
ansible-playbook -i hosts localhost playbooks/claude-setup.yml -e "api_key=your_api_key"
```

### Verifying Playbook Syntax

```bash
# Check playbook syntax
ansible-playbook --syntax-check playbooks/claude-setup.yml
```

## 🎯 Playbook Categories

### 1. Claude Code Setup Playbooks

Playbooks for installing and configuring Claude Code:

- [Installation](playbooks/tasks/claude-install.yml) - Package installation tasks
- [Configuration](playbooks/tasks/claude-config.yml) - Configuration file setup tasks
- [Verification](playbooks/tasks/claude-verify.yml) - Installation verification tasks

### 2. Z.AI Integration Playbooks

Playbooks for configuring Z.AI API integration:

- [API Key Setup](playbooks/tasks/z-ai-api-key.yml) - API key configuration
- [Environment Variables](playbooks/tasks/z-ai-env-vars.yml) - Environment variable setup
- [MCP Servers](playbooks/tasks/z-ai-mcp-servers.yml) - MCP server configuration

### 3. Environment Configuration Playbooks

Playbooks for general environment setup:

- [Node.js Setup](playbooks/tasks/nodejs-setup.yml) - Node.js installation verification
- [Git Setup](playbooks/tasks/git-setup.yml) - Git installation verification

## 📝 Contributing

When adding new playbooks:
1. Create task files in `playbooks/tasks/`
2. Create playbooks in `playbooks/` directory
3. Update this `README.md`

## 📄 License

MIT License - See LICENSE file for details.