# 🌉 Context Bridge

The Context Bridge skill prevents context loss when hitting AI usage limits mid-development. By typing `/checkpoint` or '/bridge', your local AI agent acts as an emergency brake, instantly saving a noise-free snapshot of your workspace—including active file trees, data shapes, and immediate next steps—into a structured `checkpoint.md` file. Drop this artifact into any fresh AI model to resume complex development seamlessly.

## 🚀 Installation

Choose your preferred installation method below. 

### Method 1: Terminal Installation (Recommended)
Run the single terminal command for your specific AI tool. This will safely append the Context Bridge protocol to your project's existing configuration file and print a success message so you know it worked.

**For Cursor:**
```bash
curl -sf https://raw.githubusercontent.com/SheedoM/context-bridge/main/context-bridge.md >> .cursorrules && echo "✅ Context Bridge installed successfully in .cursorrules!"
```

**For Claude Code:**
```bash
curl -sf https://raw.githubusercontent.com/SheedoM/context-bridge/main/context-bridge.md >> CLAUDE.md && echo "✅ Context Bridge installed successfully in CLAUDE.md!"
```

**For Windsurf:**
```bash
curl -sf https://raw.githubusercontent.com/SheedoM/context-bridge/main/context-bridge.md >> .windsurfrules && echo "✅ Context Bridge installed successfully in .windsurfrules!"
```

**For Antigravity / Codex (Generic System Prompt):**
```bash
curl -sf https://raw.githubusercontent.com/SheedoM/context-bridge/main/context-bridge.md >> system.md && echo "✅ Context Bridge installed successfully in system.md!"
```

### Method 2: Manual Installation
If you prefer to review the code before adding it, you can install the skill manually:

1. Open `context-bridge.md` in this repository and copy all the text.
2. Open your project's root AI configuration file (e.g., `.cursorrules`, `CLAUDE.md`, `.windsurfrules`).
3. Paste the text at the very bottom of the file and save.

## ⚡ Triggering the Bridge
When you are nearing your token/usage limit, simply type `/checkpoint` in the chat. The AI will immediately generate a `checkpoint.md` file in your root directory.
