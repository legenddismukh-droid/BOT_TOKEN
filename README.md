# Telegram Bot — GitHub + Render

## Files
- `main.py`: bot code configured to read secrets from environment variables.
- `requirements.txt`: Python dependencies.
- `render.yaml`: Render Background Worker configuration with a persistent disk.

## Before deploying
1. Revoke the exposed old Telegram bot token in @BotFather and generate a new token.
2. Upload these files to a GitHub repository.
3. In Render, create a new Blueprint from that repository (or create a Background Worker manually).
4. Set Environment Variables:
   - `BOT_TOKEN`: the NEW token from @BotFather
   - `BOT_USERNAME`: bot username without `@`
   - `ADMIN_ID`: your numeric Telegram user ID
   - `ADMIN_CONTACT`: admin Telegram username without `@`
   - `FAMGATEWAY_API_KEY`: your FamGateway key, only if you use that payment gateway
5. Deploy and check the Render Logs.

## Database note
The Render configuration mounts a persistent disk at `/var/data` and stores the SQLite DB at `/var/data/Pikachu.db`.
Persistent disks are available on paid Render services; if the selected plan doesn't support disks, use a supported persistent database/storage option or the database may be lost on redeploy/restart.

## Important
- Never commit your bot token or payment API key to GitHub.
- Do not run two copies of the same bot token with polling at the same time.
- 
