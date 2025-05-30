# Available Variables (Version 0.0.0.2 - Examples)

This is not an exhaustive list. Variables provide dynamic data within your action strings.

**User/Author Context (typically the user who triggered the command/event):**
*   `{user.name}`: Username (e.g., `CoolUser`)
*   `{user.id}`: User's unique ID (e.g., `123456789012345678`)
*   `{user.mention}`: Creates an @mention for the user.
*   `{user.discriminator}`: User's 4-digit tag (e.g., `1234`). (Note: This is becoming less common with Discord's new username system).
*   `{user.nick}`: User's server nickname (falls back to username if no nickname).
*   `{user.display_name}`: User's display name on the server (nickname or username).
*   `{user.avatar_url}`: URL of the user's avatar.
*   `{user.roles_names}`: Comma-separated list of the user's role names (excluding @everyone).
*   `{user.top_role_name}`: Name of the user's highest role on the server.

**Message Context (for commands triggered by messages):**
*   `{message.content}`: The full content of the message that triggered the command.
*   `{message.id}`: The ID of the triggering message.

**Command Argument Variables:**
*   `{args}`: All text that comes after the command trigger. (e.g., in `e!say Hello World`, `{args}` is `Hello World`).
*   `{arg[1]}`, `{arg[2]}`, ... `{arg[N]}`: The Nth argument (word) after the command trigger. (e.g., in `e!greet David`, `{arg[1]}` is `David`).
*   `{argslen}` or `{argscount}`: The number of arguments provided.

**Channel Context (where the command was used or event occurred):**
*   `{channel.name}`: Name of the current channel (e.g., `general`, or `DM Channel` for DMs).
*   `{channel.id}`: ID of the current channel.
*   `{channel.mention}`: Creates a #mention for the channel.

**Server/Guild Context (if applicable):**
*   `{server.name}` or `{guild.name}`: Name of the server.
*   `{server.id}` or `{guild.id}`: ID of the server.
*   `{server.member_count}` or `{guild.member_count}`: Total number of members in the server.
*   `{server.icon_url}`: URL of the server's icon (if any).
*   `{server.owner.id}`: ID of the server owner.
*   `{server.owner.name}`: Name of the server owner.

**Bot Information:**
*   `{bot.name}`: The bot's username.
*   `{bot.id}`: The bot's ID.
*   `{bot.mention}`: Creates an @mention for the bot.
*   `{bot.prefix}`: The primary prefix the bot is configured with.
*   `{bot.latency_ms}`: The bot's network latency to Discord in milliseconds.

**Utility Variables:**
*   `{random[min,max]}`: A random integer between min and max (inclusive). Example: `{random[1,100]}`.
*   `{random[choice1,choice2,...]}`: A random choice from the provided list. Example: `{random[Red,Green,Blue]}`.
*   `{time}`: Current time in HH:MM:SS format.
*   `{date}`: Current date in YYYY-MM-DD format.
*   `{timestamp}`: Current Unix timestamp (seconds since epoch).

**ID Lookup Variables (require server context):**
*   `{roleID[RoleName]}`: Tries to find a role named "RoleName" and returns its ID.
*   `{channelID[channel-name]}`: Tries to find a text channel named "channel-name" and returns its ID.
*   `{userID[Username]}` or `{userID[Username#1234]}`: Tries to find a user by name (or name+tag) and returns their ID.
    *   *Note: User lookups by name can be unreliable with Discord's new username system. ID or mention is preferred for targeting users.*

**Event-Specific Data (using `{event.key}`):**
*   For events not directly tied to a message (e.g., `on_member_join`, `on_message_delete`), data specific to that event can often be accessed via `{event.some_property}`.
*   Example for `on_message_delete`:
    *   `{event.message.content}`: Content of the deleted message.
    *   `{event.message.author.name}`: Author of the deleted message.
*   *(The exact available `event.*` variables depend on the event. Check the `ElythContext` `event_data` population in `bot.py` for advanced insight or future dedicated event docs.)*

*(This list will be expanded as Elyth grows! For the most up-to-date list, please refer to the [source code](https://github.com/ElythHQ/Elyth/blob/main/elyth/context.py) or future dedicated documentation.)*