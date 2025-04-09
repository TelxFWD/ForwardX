# 🚀 Telegram ForwardBot

A robust and feature-rich Telegram bot built with Telethon to forward messages between chats or channels. This bot offers advanced filtering, image blocking, monitoring, and long-term stability features, making it ideal for automating message forwarding with precise control.

---

## ✨ Features

### 🔁 Core Functionality
- **Message Forwarding**: Seamlessly forwards messages from a source chat/channel to a destination chat/channel.
- **Message Editing**: Updates forwarded messages when the original is edited in the source chat.
- **Message Deletion**: Deletes forwarded messages when the original is deleted.
- **Reply Mapping**: Preserves reply relationships between source and destination messages.

### 🛠️ Filtering and Customization
- **Blacklist Words**: Filters messages containing specific words, replacing them with asterisks (`***`).
- **Blocked Sentences**: Prevents forwarding of messages containing specific sentences.
- **URL Filtering**: Removes all URLs or blocks specific blacklisted URLs from messages.
- **Image Blocking**: Blocks specific images based on perceptual hashes, preventing their forwarding or deleting them if edited.
- **Header/Footer Removal**: Strips predefined headers or footers from messages.
- **Custom Header/Footer**: Adds user-defined headers or footers to forwarded messages.
- **Mention Removal**: Optionally removes @mentions and inline user links from messages.
- **Emoji Rendering**: Supports emoji aliases in messages and bot responses for enhanced readability.

### 📊 Management and Monitoring
- **Pair Management**: Create, pause, resume, or clear forwarding pairs using simple commands.
- **Real-Time Monitoring**: View detailed stats for each pair (forwarded, edited, deleted, blocked, queued messages) with the `/monitor` command.
- **Periodic Reports**: Sends 6-hour summary reports of pair activity, automatically split into parts if exceeding Telegram's 4096-character limit.
- **Inactivity Alerts**: Notifies if a forwarding pair has been inactive for over 6 hours.
- **Health Status**: Monitors bot health (memory, CPU, uptime, queue size, connection status) with the `/health` command and hourly checks.

### 🧱 Advanced Stability Features
- **Rate Limiting**: Limits API calls to 30 per minute to avoid Telegram flood wait errors, with automatic retry handling.
- **Database Backup**: Saves channel mappings to `channel_mappings.json` and creates timestamped backups in `backups/`, retaining the last 10 backups.
- **Error Recovery**: Automatically attempts reconnection up to 5 times on connection loss, with notifications for persistent failures.
- **Memory Management**: Cleans up message mappings older than 24 hours hourly to prevent memory leaks.
- **Health Checks**: Runs hourly resource checks, alerting if memory exceeds 500MB or queue nears capacity (80% of 100 messages).
- **Queue Management**: Uses a capped queue (max 100 messages) to handle failed forwards, dropping oldest messages if full.

---

## ⚙️ Setup Instructions

### 📌 Prerequisites
- **Python 3.8+**: Install Python from [python.org](https://www.python.org/downloads/).
- **Telegram Account**: Required to obtain API credentials.
- **API Credentials**: Get your `API_ID` and `API_HASH` from [my.telegram.org](https://my.telegram.org) under "API Development Tools."
- **Dependencies**: Listed in `requirements.txt`.

### 🔧 Installation Steps

1. **Clone or Download the Script**:
   - If using Git:
     ```bash
     git clone <repository-url>
     cd <repository-directory>
     ```
   - Or manually download `main.py`, `requirements.txt`, etc.

2. **Set Up a Virtual Environment** *(Recommended)*:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

   This installs:
   - `telethon`: Telegram API client
   - `emoji`: Emoji rendering
   - `imagehash` and `Pillow`: Image processing for blocking
   - `ratelimit`: API rate limiting
   - `psutil`: System resource monitoring

4. **Configure API Credentials**:
   Open `main.py` in a text editor and replace:
   ```python
   API_ID = 28451755  # Replace with your API ID
   API_HASH = "c888900d408dcd71e8bf31f5aa15ae0e"  # Replace with your API hash
   ```

5. **Run the Bot**:
   ```bash
   python main.py
   ```

6. **Authenticate with Telegram**:
   - Enter your phone number (e.g., `+1234567890`).
   - Input the verification code sent to your Telegram app.
   - A `userbot_session.session` file will be created for future logins.

---

## 🔁 Configure Forwarding Pairs

Interact with the bot in Telegram.

- Set up a forwarding pair:
  ```
  /setpair <name> <source_chat_id> <destination_chat_id> [yes|no]
  ```
  Example:
  ```
  /setpair newsfeed -100123456789 -100987654321 no
  ```

- **Chat IDs**:
  - Forward a message to [@GetIDsBot](https://t.me/getidsbot) to get chat IDs.
  - Chat IDs usually start with `-100` (e.g., `-100123456789`).

- **Permissions**:
  - Read access in the source chat.
  - Write access in the destination chat.
  - Add the bot to both chats if needed.

---

## 🧾 Usage

### ✅ Basic Commands
- `/start` - Confirms the bot is running
- `/commands` - List all available commands
- `/monitor` - Show real-time forwarding stats
- `/health` - Display system resource usage

### 🔁 Pair Management
- `/setpair` - Add a forwarding pair
- `/listpairs` - Show all pairs
- `/pausepair <name>` - Pause forwarding for a pair
- `/startpair <name>` - Resume a paused pair
- `/clearpairs` - Clear all forwarding pairs

### 🔎 Filtering Commands
- `/addblacklist <name> spam,scam`
- `/clearblacklist <name>`
- `/showblacklist <name>`
- `/toggleurlblock <name>`
- `/addurlblacklist <name> example.com,badurl.org`
- `/blocksentence <name> Buy now to get rich`
- `/setheader <name> "Ad:"`
- `/setfooter <name> "Follow us"`
- `/clearheaderfooter <name>`

### 🖼️ Image Blocking
- Reply to a photo with `/blockimage <name>`
- `/clearblockedimages <name>`
- `/showblockedimages <name>`

### 🧩 Custom Text
- `/setcustomheader <name> "News Update:"`
- `/setcustomfooter <name> "Source: NewsFeed"`
- `/clearcustomheaderfooter <name>`

### 📈 Monitoring and Logs
- `/monitor` - Shows real-time stats (split if long)
- **Periodic Reports**: Auto-sent every 6 hours
- **Logs**: Stored in `forward_bot.log`
- **Backups**: Found in `backups/`, base file is `channel_mappings.json`

---

## 📝 Notes
- **Message Length**: Messages over 4096 characters are split.
- **Rate Limits**: Telegram may restrict heavy usage.
- **Resource Alerts**: Memory > 500MB or queue > 80 triggers warning.
- **Session File**: Secure `userbot_session.session`, it stores login.

### 🧰 Troubleshooting
- **Login issues**: Delete `userbot_session.session` and restart.
- **Flood waits**: The bot auto-handles them; reduce message rate.
- **Connection loss**: Auto-reconnects 5 times; check your internet.
- **Missing dependencies**: Run `pip install -r requirements.txt` again.
- **Permission issues**: Ensure proper read/write chat access.

