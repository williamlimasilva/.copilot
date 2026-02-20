# .copilot

Personal configuration repository for GitHub Copilot instructions, custom agents, and reusable skills.

## 📁 Structure

```
.copilot/
├── agents/              # Custom AI agents for specialized tasks
├── instructions/        # Language and framework-specific coding instructions
├── skills/             # Reusable skill modules for various domains
├── prompts/            # Custom prompt templates
├── snippets/           # Code snippet library
└── session-state/      # Session persistence and history
```

## 🤖 Agents

Custom agents located in [`agents/`](agents/):

- **Beast Mode** - Autonomous agent for complex problem-solving with extensive research
- **Coder** - Writes code following mandatory coding principles
- **Designer** - Handles all UI/UX design tasks
- **Orchestrator** - Multi-model orchestration (Sonnet, Codex, Gemini)
- **Planner** - Creates comprehensive implementation plans with codebase research

## 📋 Instructions

Framework-specific coding standards in [`instructions/`](instructions/):

### Backend & APIs

- [Quarkus](instructions/quarkus.instructions.md) - Enterprise Java microservices
- [Spring Boot](instructions/springboot.instructions.md) - Java/Kotlin applications
- [NestJS](instructions/nestjs.instructions.md) - Node.js server-side applications
- [Java](instructions/java.instructions.md) - Base Java development

### Frontend

- [Angular](instructions/angular.instructions.md) - TypeScript framework
- [Next.js](instructions/nextjs.instructions.md) - React framework with App Router
- [Svelte](instructions/svelte.instructions.md) - Component-based UI

### Languages

- [Python](instructions/python.instructions.md) - Python conventions
- [Go](instructions/go.instructions.md) - Idiomatic Go practices
- [C#](instructions/csharp.instructions.md) - .NET development
- [Rust](instructions/rust.instructions.md) - Systems programming

### Infrastructure

- [Terraform](instructions/terraform.instructions.md) - Infrastructure as Code
- [Ansible](instructions/ansible.instructions.md) - Configuration management
- [Shell](instructions/shell.instructions.md) - Bash/sh scripting

### Other

- [Markdown](instructions/markdown.instructions.md) - Documentation standards
- [.NET WPF](instructions/dotnet-wpf.instructions.md) - Desktop applications
- [Agents](instructions/agents.instructions.md) - Custom agent creation
- [Commits](instructions/commits.instructions.md) - Conventional commit messages

## 🎯 Skills

Comprehensive skill library in [`skills/`](skills/) covering:

### AI & Agents

- Agent frameworks (CrewAI, Azure AI Agents, autonomous agents)
- LLM integration patterns (RAG, prompt engineering, context management)
- Memory systems and tool building

### Cloud & Infrastructure

- AWS, Azure, GCP patterns
- Serverless (AWS Lambda, Azure Functions)
- Database design and optimization
- CI/CD automation

### Development

- API design (REST, GraphQL, tRPC)
- Authentication patterns (OAuth2, JWT)
- Testing strategies (TDD, E2E)
- Code review and refactoring

### Security

- Penetration testing
- Binary analysis
- Reverse engineering
- Attack tree construction

### Automation

- Browser automation (Playwright, Puppeteer)
- Task automation via MCP integrations
- Workflow orchestration

**Total Skills**: 200+ specialized domain skills

## 🚀 Usage

This repository is automatically loaded by GitHub Copilot when present in `~/.copilot/` or `%USERPROFILE%\.copilot\`.

### Instructions Apply To

Instructions automatically apply based on file patterns:

- `**/*.java` → Java, Spring Boot, Quarkus
- `**/*.ts, **/*.tsx` → Angular, Next.js, NestJS
- `**/*.py` → Python
- `**/*.tf` → Terraform
- And more...

### Running Agents

Use the `runSubagent` tool with agent names:

```bash
# Example: Run Planner agent
runSubagent("Planner", "Plan implementation for user authentication")
```

### Using Skills

Skills are automatically activated based on context keywords:

- "build agent" → `ai-agents-architect`
- "azure function" → `azure-functions`
- "playwright test" → `browser-automation`
- "refactor code" → `refactor`

## 📊 Security

See [skills-security-report-2026-02-19.md](skills-security-report-2026-02-19.md) for the latest security audit of all skills.

## 🔧 Configuration

- `config.json` - Main configuration file
- `command-history-state.json` - Command history tracking
- Session states stored in `session-state/` and `history-session-state/`

## 🔄 Automatic Sync with Upstream

This repository includes a GitHub Actions workflow that automatically syncs new content from the upstream [github/awesome-copilot](https://github.com/github/awesome-copilot) repository.

### How It Works

The workflow runs:
- **Scheduled**: Daily at 2 AM UTC (11 PM Brasília time)
- **Manual**: Can be triggered manually via GitHub Actions interface

The sync uses an **additive merge strategy**, which means:
- ✅ New files from upstream are added
- ✅ Your existing files are never overwritten
- ✅ Your custom modifications are preserved
- ✅ Deletions from upstream don't affect your local files

### Manual Trigger

To manually sync with upstream:

1. Go to the [Actions tab](../../actions) in your repository
2. Click on "Sync Upstream Directories" workflow
3. Click "Run workflow" button
4. Select the branch (usually `main`)
5. Click "Run workflow"

The workflow will sync the following directories:
- `prompts/` - New prompt templates
- `skills/` - New skill modules  
- `instructions/` - New coding instructions

### ⚙️ VS Code Integration

Add the following settings to your VS Code `settings.json` (User or Workspace) to allow the editor to automatically recognize and load agents, skills, prompts, and instructions from the folders in this repository:

```json
{
    "chat.agent.enabled": true,
    "chat.agentFilesLocations": {
        "~/.copilot/agents": true
    },
    "chat.agentSkillsLocations": {
        "~/.copilot/skills": true
    },
    "chat.promptFilesLocations": {
        "~/.copilot/prompts": true
    },
    "chat.instructionsFilesLocations": {
        "~/.copilot/instructions": true
    },
    "chat.mcp.access": "all",
    "chat.mcp.autostart": "onlyNew",
    "chat.mcp.discovery.enabled": {
        "claude-desktop": true,
        "windsurf": true,
        "cursor-global": true,
        "cursor-workspace": true
    },
    "chat.promptFiles": true,
    "chat.todoListTool.enabled": true
}
```

> Note: adjust paths if the repository is located outside your home directory.

## 📝 Development Standards

All code generation follows:

- Clean Code principles
- SOLID design patterns
- Language-specific idioms from instructions
- TDD when applicable
- Comprehensive error handling
- Security best practices

## 🤝 Contributing

This is a personal configuration repository. To create your own:

1. Fork or create `.copilot/` in your home directory
2. Add custom instructions in `instructions/`
3. Create agents in `agents/` following the agent guidelines
4. Add skills to `skills/` directory

## 📄 License

Personal configuration files - adapt as needed for your workflow.

---

**Note**: This repository contains configuration for GitHub Copilot using Claude Sonnet 4.5 as the underlying model.
