# Enc - Telegram Video Encoder Bot

## Overview
A Telegram bot for video encoding, downloading, and processing. Uses Telethon and Pyrogram to interact with Telegram, MongoDB for persistent storage, and ffmpeg for video encoding.

## Recent Changes
- 2026-02-09: Initial Replit setup
  - Fixed syntax error in `bot/workers/handlers/queue.py` (unterminated f-string)
  - Changed `DATABASE_URL` to `MONGO_DATABASE_URL` in config to avoid conflict with Replit's managed PostgreSQL `DATABASE_URL`
  - Installed system dependencies: ffmpeg, aria2, libmediainfo, tzdata
  - Set TZ environment variable to UTC

## Project Architecture
- **Language**: Python 3.12
- **Entry point**: `python3 -m bot` (runs `bot/__main__.py`)
- **Database**: MongoDB (external, via `MONGO_DATABASE_URL` env var)
- **Telegram Libraries**: Telethon + Pyrogram
- **Key directories**:
  - `bot/` - Main bot package
  - `bot/config.py` - Configuration from environment variables
  - `bot/startup/` - Bot startup logic
  - `bot/utils/` - Utility modules
  - `bot/workers/` - Worker modules for encoding, downloading, etc.
  - `bot/fun/` - Fun commands (quotes, emojis, etc.)
  - `filters/` - Text filter files
  - `fonts/` - Font files for image processing
  - `scripts/` - Shell scripts

## Environment Variables (Required)
- `APP_ID` - Telegram API ID
- `API_HASH` - Telegram API Hash
- `BOT_TOKEN` - Telegram Bot Token (must be valid/active)
- `OWNER` - Telegram user ID of the bot owner
- `MONGO_DATABASE_URL` - MongoDB connection string (renamed from DATABASE_URL to avoid Replit conflict)

## Running
The bot runs via the "Telegram Bot" workflow: `python3 -m bot`

## Notes
- The `update.py` script attempts to pull from upstream GitHub repo - skipped in Replit workflow to avoid overwriting local changes
- The `.env` file contains the original config but Replit env vars take precedence
- Bot token from original import is expired; user needs to provide a valid one
