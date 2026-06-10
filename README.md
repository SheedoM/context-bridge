# 🌉 Context Bridge

The Context Bridge skill prevents context loss when hitting AI usage limits mid-development. By typing `/checkpoint`, your local AI agent acts as an emergency brake, instantly saving a noise-free snapshot of your workspace—including active file trees, data shapes, and immediate next steps—into a structured `checkpoint.md` file. Drop this artifact into any fresh AI model to resume complex development seamlessly.

## 🚀 Installation

You don't need to download any packages. Just run the single terminal command for your specific AI tool. This will safely append the Context Bridge protocol to your project's existing configuration file.

**For Cursor:**
```bash
curl -s https://raw.githubusercontent.com/SheedoM/context-bridge/main/context-bridge.md >> .cursorrules
```

**For Claude Code:**
```bash
curl -s https://raw.githubusercontent.com/SheedoM/context-bridge/main/context-bridge.md >> CLAUDE.md
```

**For Windsurf:**
```bash
curl -s https://raw.githubusercontent.com/SheedoM/context-bridge/main/context-bridge.md >> .windsurfrules
```

**For Antigravity / Codex (Generic System Prompt):**
```bash
curl -s https://raw.githubusercontent.com/SheedoM/context-bridge/main/context-bridge.md >> system.md
```

## ⚡ Triggering the Bridge
When you are nearing your token/usage limit, simply type `/checkpoint` in the chat. The AI will immediately generate a `checkpoint.md` file in your root directory.
