# 🤖 Telegram Video Processor Bot

## What this bot does
- When you send a video, it adds your custom thumbnail
- Replaces any `@username` in the caption with YOUR username
- If no username in caption, automatically adds: `Extracted by :- @YourUsername`
- Optionally keeps or removes links (URLs) from captions
- Configured through a simple step-by-step setup

---

## 📁 Files
```
telegram_bot/
├── bot.py            ← Main bot file
├── requirements.txt  ← Dependencies
└── thumbnails/       ← Auto-created folder for thumbnails
```

---

## 🚀 How to run (Step-by-step)

### Step 1: Get a Bot Token
1. Open Telegram → search `@BotFather`
2. Send `/newbot`
3. Follow instructions, copy the **API Token**

### Step 2: Install Python & dependencies
```bash
pip install -r requirements.txt
```

### Step 3: Set your Bot Token
**Windows:**
```cmd
set BOT_TOKEN=your_token_here
python bot.py
```

**Linux/Mac:**
```bash
export BOT_TOKEN=your_token_here
python bot.py
```

**Or create a `.env` file** (optional):
```
BOT_TOKEN=your_token_here
```
And run:
```bash
python bot.py
```

---

## 💬 Bot Commands
| Command | Description |
|---------|-------------|
| `/start` | Show bot status |
| `/setup` | Configure username, links, thumbnail |
| `/setthumb` | Change only the thumbnail |
| `/settings` | View current settings |
| `/cancel` | Cancel current action |

---

## ⚙️ Setup Flow (inside Telegram)
1. Send `/setup` to your bot
2. Enter your username (e.g. `Coursesbuying`)
3. Choose: keep links ✅ or remove links ❌
4. Send a thumbnail image OR skip
5. Done! Now send any video 🎬

---

## 📝 Caption Examples

**Input caption:**
```
Best Python Course 2024
Download here: https://t.me/xyz
@SomeOtherChannel
```

**Output caption (username replaced, links kept):**
```
Best Python Course 2024
Download here: https://t.me/xyz
@Coursesbuying

Extracted by :- @Coursesbuying
```

---

## 🌐 Hosting on a Server (24/7)

### Using screen (Linux VPS):
```bash
screen -S bot
export BOT_TOKEN=your_token_here
python bot.py
# Press Ctrl+A then D to detach
```

### Using systemd service:
Create `/etc/systemd/system/telegrambot.service`:
```ini
[Unit]
Description=Telegram Video Bot
After=network.target

[Service]
User=ubuntu
WorkingDirectory=/path/to/telegram_bot
Environment="BOT_TOKEN=your_token_here"
ExecStart=/usr/bin/python3 bot.py
Restart=always

[Install]
WantedBy=multi-user.target
```
Then:
```bash
sudo systemctl enable telegrambot
sudo systemctl start telegrambot
```

---

## ❓ Troubleshooting
- **Bot not responding**: Check BOT_TOKEN is set correctly
- **Video fails**: Telegram has 50MB limit for bots. Large files may fail
- **Thumbnail not showing**: Send a clear JPG/PNG image during setup
