# 🌉 Context Bridge

The Context Bridge skill prevents context loss when hitting AI usage limits mid-development. By typing `/checkpoint`, your local AI agent acts as an emergency brake, instantly saving a noise-free snapshot of your workspace—including active file trees, data shapes, and immediate next steps—into a structured `checkpoint.md` file. Drop this artifact into any fresh AI model to resume complex development seamlessly.

## 🚀 How to Use (Tool-Specific Setup)
Copy the contents of `context-bridge.md` and paste it into your project's root configuration file based on the tool you are using:
* **Cursor:** Paste into your project's `.cursorrules` file.
* **Windsurf:** Paste into your `.windsurfrules` file.
* **Claude Code:** Paste into your `CLAUDE.md` file.
* **Antigravity / Codex:** Paste into your root system prompt file (e.g., `system.md` or `.prompt`).
* **Standard Web UIs (ChatGPT/Claude):** Paste into the "Custom Instructions" or "Project Knowledge" section.

## ⚡ Triggering the Bridge
When you are nearing your token/usage limit, simply type `/checkpoint` in the chat. The AI will immediately generate a `checkpoint.md` file in your root directory.
