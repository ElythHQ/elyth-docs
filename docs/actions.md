# Common Action Verbs (Version 0.0.0.2)

Elyth simplifies bot creation through **Action Strings**. An action string typically consists of a `VERB` followed by arguments and can utilize dynamic `{variables}`.

*   `REPLY: <message>`
    *   Replies to the command-issuing message.
    *   Mentions the user by default.
    *   Example: `REPLY: Got it, {user.nick}!`
*   `SAY: <message>`
    *   Sends a message to the current channel.
    *   Does *not* mention the triggering user by default.
    *   Example: `SAY: The current time is {time}.`
*   `SEND <#channel_name_or_id_or_var>: <message>`
    *   Sends a message to a specific channel.
    *   Target can be a channel name (e.g., `#announcements`), a channel ID (e.g., `1234567890`), or a variable resolving to one (e.g., `{channel.id}`).
    *   Example: `SEND #logs: User {user.name} used the {message.content.split()[0]} command.`
*   `ADDROLE <user_id_or_mention_or_name_or_var> <role_id_or_name_or_var>: [optional_reason]`
    *   Adds a role to a user. Bot needs "Manage Roles" permission and its highest role must be above the role being added.
    *   User/Role can be ID, name, @mention (for user), or a variable.
    *   Example: `ADDROLE {user.id} {roleID[Verified]}: User verified.`
*   `PRINT: <message>`
    *   Prints a message to the bot's console. Useful for `on_ready` or debugging.
    *   Example: `PRINT: Bot initialization sequence complete at {timestamp}.`

*(More verbs are planned for future versions!)*