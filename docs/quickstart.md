# Quick Start Guide

This guide will help you set up your first Elyth bot.

1.  **Installation:**
    ```bash
    pip install elyth
    ```
    (Ensure Python 3.8+ is installed).

2.  **Discord Bot Setup:**
    *   Get your bot token from the [Discord Developer Portal](https://discord.com/developers/applications).
    *   Enable `SERVER MEMBERS INTENT`, `MESSAGE CONTENT INTENT`, and `GUILDS` intents.

3.  **Your First Bot Script:**
    ```python
    from elyth import ElythBot
    import os

    TOKEN = os.getenv("DISCORD_BOT_TOKEN")
    if not TOKEN:
        print("Error: DISCORD_BOT_TOKEN environment variable not set!")
        exit()

    bot = ElythBot(token=TOKEN, prefix="!")

    @bot.event("on_ready", "PRINT: My bot is online!")
    @bot.command("test", "REPLY: It works, {user.mention}!")

    bot.run()
    ```
4.  **Run:** `python your_bot_file.py`

For more details on commands and variables, see [Common Action Verbs](actions.md) and [Available Variables](variables.md).