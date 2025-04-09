# 🚀 Telegram ForwardBot

![ForwardBot Banner](https://images.unsplash.com/photo-1614332287897-cdc485fa562d?ixlib=rb-4.0.3&auto=format&fit=crop&w=1350&q=80)  
*A sleek Telegram bot for forwarding messages with power-packed features!*

---

Welcome to **Telegram ForwardBot** – a feature-rich, reliable bot built with Telethon to automate message forwarding between chats or channels. Whether you're managing news feeds, moderating content, or organizing messages, this bot has you covered with advanced filtering, monitoring, and stability features.

---

## ✨ Features

### 🔑 Core Features
- **Message Forwarding**  
  Seamlessly forward messages from source to destination chats.  
  ![Forwarding](https://images.unsplash.com/photo-1521747116042-5a810fda9664?ixlib=rb-4.0.3&auto=format&fit=crop&w=300&q=80)
- **Edit & Delete Sync**  
  Updates or removes forwarded messages when originals are edited or deleted.
- **Reply Mapping**  
  Keeps reply threads intact between chats.

### 🛡️ Filtering & Customization
- **Word Blacklist**  
  Replace unwanted words with `***`.  
- **Sentence Blocking**  
  Stop messages with specific phrases.  
- **URL Control**  
  Remove all URLs or block specific ones.  
- **Image Blocking**  
  Block specific images using perceptual hashes.  
  ![Image Blocking](https://images.unsplash.com/photo-1620712943543-bcc4688e5255?ixlib=rb-4.0.3&auto=format&fit=crop&w=300&q=80)  
- **Header/Footer Magic**  
  Strip or add custom headers/footers.  
- **Mention Cleanup**  
  Optionally remove @mentions.  
- **Emoji Power**  
  Render emoji aliases everywhere! 🌟

### 📊 Management & Monitoring
- **Pair Control**  
  Create, pause, resume, or clear forwarding pairs.  
- **Live Stats**  
  Check pair stats with `/monitor` – forwarded, edited, blocked, and more!  
- **Periodic Reports**  
  Get 6-hour summaries, split into parts for big reports.  
  ![Monitoring](https://images.unsplash.com/photo-1460925895917-afdab8276844?ixlib=rb-4.0.3&auto=format&fit=crop&w=300&q=80)  
- **Inactivity Alerts**  
  Warns if a pair’s quiet for 6+ hours.  
- **Health Check**  
  Monitor bot vitals with `/health`.

### ⚙️ Advanced Stability
- **Rate Limiting**  
  Caps API calls at 30/min to dodge flood waits.  
- **Backups**  
  Saves mappings with timestamped backups (last 10 kept).  
- **Auto-Reconnect**  
  Retries connection 5 times on drops.  
- **Memory Care**  
  Cleans old mappings hourly.  
- **Health Alerts**  
  Notifies if memory > 500MB or queue > 80 messages.

---

## 🛠️ Setup Guide

### What You’ll Need
- **Python 3.8+** – [Download here](https://www.python.org/downloads/).  
- **Telegram Account** – For API credentials.  
- **API Keys** – Grab from [my.telegram.org](https://my.telegram.org).  

### Step-by-Step
1. **Get the Code**  
   Clone or download:  
   ```bash
   git clone <repository-url>
   cd <repository-directory>

Set Up Environment  
bash

python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

Install Goodies  
bash

pip install -r requirements.txt

Add Your Keys
Edit main.py:  
python

API_ID = 28451755  # Your API ID
API_HASH = "c888900d408dcd71e8bf31f5aa15ae0e"  # Your API Hash

Launch It!  
bash

python main.py

Sign In  
Enter your phone number (e.g., +1234567890).  

Type the code Telegram sends you.  

A userbot_session.session file will save your login.

Set Up a Pair
In a chat with the bot:  

/setpair newsfeed -100123456789 -100987654321 no

Chat IDs 101
Use @GetIDsBot to find chat IDs (e.g., -100123456789).  

Add the bot to source (read) and destination (write) chats.

 How to Use
Kick Things Off
/start – " ForwardBot Running!"  

/commands – See all tricks up its sleeve.

Manage Pairs
Add: /setpair newsfeed -100123456789 -100987654321 no  

List: /listpairs  

Pause: /pausepair newsfeed  

Resume: /startpair newsfeed  

Clear: /clearpairs

Filter Like a Pro
Words: /addblacklist newsfeed spam,scam  

URLs: /toggleurlblock newsfeed or /addurlblacklist newsfeed bad.com  

Sentences: /blocksentence newsfeed "Click here now"  

Images: Reply to a photo with /blockimage newsfeed
Block Image Demo  

Custom Text: /setcustomheader newsfeed "Hot News:"

Monitor & Debug
Stats: /monitor  

Health: /health  

Logs: Check forward_bot.log.

 Quick Tips
Long Reports: Split into parts if > 4096 chars.  

Permissions: Read in source, write in destination.  

Backups: Stored in backups/ – recover if needed!  

Support: Hit us up on Telegram at @fsl_support.

 Troubleshooting
Login Fails: Delete userbot_session.session and retry.  

Flood Waits: Bot pauses automatically – reduce load if frequent.  

No Forwarding: Check chat IDs and permissions.  

Errors: See forward_bot.log or contact @fsl_support.

 Contact Us
Got questions? Need help? Reach out on Telegram:
 @fsl_support
We’re here to make your bot experience awesome!
 Contribute
Love the bot? Fork it, tweak it, PR it! Issues and ideas welcome.
 License
MIT License – Free to use, share, and modify.
Happy Forwarding! 

Powered by Telegram ForwardBot

