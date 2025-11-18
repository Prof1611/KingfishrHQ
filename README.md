# Template Bot

A generic Discord bot template featuring welcome messaging, event scraping, configurable presence rotation, and moderation utilities. Follow the checklist below to configure the bot for your server.

## Getting started

1. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```
2. **Create your Discord application**
   - Visit the [Discord Developer Portal](https://discord.com/developers/applications), create an application, and add a bot user.
   - Enable the privileged intents you plan to use (at minimum Server Members for welcome and autorole functionality).
   - Copy the bot token and add it to your environment or hosting platform.
3. **Grant the bot access to your server**
   - Use the OAuth2 URL generator to create an invite link with the required scopes (`bot` and `applications.commands`).
   - Select the permissions you need (Manage Roles, Manage Events, Moderate Members, etc.), invite the bot, and ensure its role is above any roles it must manage.

## Configure `config.yaml`

Each section of `config.yaml` documents the values you need to supply:

- **`bot.statuses`** – Rotating presence text shown in the client. Replace the example phrases with ones relevant to your community.
- **`bot.dm_forward_channel_id`** – Channel ID that receives DMs sent to the bot. Set to `null` to disable forwarding.
- **`channels`** – IDs for welcome, moderation log, and optional introduction channels. All IDs are integers obtained with Discord's developer mode.
- **`features`** – Toggle individual modules and fill in feature specific options:
  - `welcome_messages` – Enable/disable welcome embeds.
  - `autorole` – Role ID to assign on join and whether to include bots.
  - `member_stats` – Naming format for the member count voice channel.
  - `live_events.page_url` – Source URL for the live event scraper.
  - `giveaways` – Defaults, labels, and manager role IDs for the giveaway cog.
  - `songlink` – API configuration for the `/track` command.
- **`appearance.colours`** – Hex strings that control the success, information, and error embed colours used across every cog.

After updating the configuration, restart the bot to reload the settings.

## Running the bot locally

```bash
python main.py
```

The bot will load all cogs defined in the `cogs` directory. Review the console output for any configuration warnings.
