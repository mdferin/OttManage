# 🎬 OTT Manager Telegram Bot

A comprehensive 🤖 Telegram bot for managing OTT (Over-The-Top) streaming services. This bot allows administrators to create, extend, and delete OTT service entries, while users can claim and access these services for streaming content.

## 📚 Table of Contents
- [✨ Features](#-features)
- [📋 Prerequisites](#-prerequisites)
- [💾 Installation](#-installation)
- [⚙️ Configuration](#️-configuration)
- [🎮 Usage](#-usage)
- [⌨️ Commands](#-commands)
- [📁 File Structure](#-file-structure)
- [🔒 Security Considerations](#-security-considerations)
- [📄 License](#-license)

## ✨ Features

- **👥 Admin Management**: Create, extend, and delete OTT service entries
- **🎁 User Claims**: Users can claim OTT services via unique links
- **⏰ Expiration Tracking**: Automatic tracking and notification of expiring services
- **👤 User Management**: Admins can view all users and delete user records
- **📢 Announcement System**: Send announcements to all registered users (text or photo)
- **🌍 Timezone Support**: Uses Malaysia timezone (Asia/Kuala_Lumpur) for all dates
- **🚫 Duplicate Prevention**: Prevents multiple claims of the same OTT ID
- **🔔 Reminder System**: Automated reminders sent before service expiration (7, 3, and 1 day warnings)

## 📋 Prerequisites

- 🐍 Python 3.8 or higher
- 🤖 Telegram Bot Token (obtained from @BotFather)
- 📚 Required Python libraries (see Installation)

## 💾 Installation

1. 📁 Clone the repository or download the bot.py file
2. 📦 Install the required dependencies:

```bash
pip install python-telegram-bot pytz
```

3. ✅ Make sure you have the required Python libraries installed

## ⚙️ Configuration

Before running the bot, you need to configure the following:

1. **🤖 Bot Token**: Replace the `BOT_TOKEN` in the code with your actual bot token
2. **👥 Admin IDs**: Update the `ADMIN_IDS` list with the Telegram user IDs of administrators
3. **👤 Admin Usernames**: Update the `ADMIN_USERNAMES` dictionary with admin usernames for support contact

Example configuration:
```python
BOT_TOKEN = "YOUR_ACTUAL_BOT_TOKEN_HERE"
ADMIN_IDS = ["123456789", "987654321"]  # Replace with actual Telegram user IDs
ADMIN_USERNAMES = {
    "123456789": "admin_username",
    "987654321": "another_admin"
}
```

## 🎮 Usage

### 🚀 Starting the Bot

Run the bot with:
```bash
python bot.py
```

### 🙋 For Users

1. 🎯 Start the bot with `/start` command
2. 🔗 Use claim links (e.g., `https://t.me/yourbot?start=claim_ott-id`) to claim OTT services
3. 📺 Access your claimed services with the provided URLs

### 👮‍♂️ For Administrators

After starting the bot, you'll see the admin control panel with the following commands:

#### 🛠️ Management Commands
- `/create <ott_id> <duration>` - Create a new OTT service entry
- `/extend <ott_id> <duration>` - Extend an existing OTT service
- `/delete <ott_id>` - Delete an OTT service entry
- `/deleteuser <user_id>` - Remove a user's record
- `/list` - View all active services
- `/users` - View all registered users
- `/announce <message>` - Send announcement to all users

#### ➕ Creating an OTT Service

To create a new OTT service:
```
/create rtm-41806 90days
```

This will create an OTT service with ID "rtm-41806" that expires in 90 days. The bot will generate a claim link that users can use to access the service.

#### 🔁 Extending an OTT Service

To extend an existing OTT service:
```
/extend rtm-41806 30days
```

This will add 30 days to the current expiration date of the service.

#### ❌ Deleting an OTT Service

To delete an OTT service:
```
/delete rtm-41806
```

You'll be prompted to confirm the deletion to prevent accidental removals.

## ⌨️ Commands Reference

### 👤 User Commands
- `/start` - Start the bot and receive welcome message

### 👮 Admin Commands
- `/create <id> <duration>` - Deploy new OTT service
- `/extend <id> <duration>` - Extend service validity
- `/delete <id>` - Remove OTT service
- `/deleteuser <user_id>` - Remove user record
- `/list` - View all active services
- `/users` - View all registered users
- `/announce <message>` - Send announcement to all users (with preview)

### 💡 Example Usage
```
/create myservice-001 30days
/extend myservice-001 15days
/delete myservice-001
/deleteuser 123456789
/list
/users
/announce Hello, there's a maintenance window tomorrow!
```

## 📁 File Structure

The bot automatically creates the following directories:

- `📁 database/` - Stores OTT service entries as JSON files
- `📁 users/` - Stores user records as JSON files
- `📁 announcements/` - Stores announcement logs

Each OTT service is stored as a JSON file named after its ID (e.g., `rtm-41806.json`) containing:
- 📅 Expiration timestamp
- 📆 Expiration description
- 📱 Device limit
- 📺 Playlist type
- 👷 Creator information
- 📋 Device list

Each user record is stored as a JSON file named after their user ID containing:
- 👤 User information (ID, username, first name, last name)
- 🎁 List of claimed OTT services
- 📅 Registration date
- 🔔 Reminders sent tracking

## ⚙️ How It Works

### 👤 For Users:
1. 👮 Admin creates an OTT service using `/create`
2. 🤖 Bot generates a unique claim link (e.g., `https://t.me/yourbot?start=claim_service-id`)
3. 👤 User clicks the link to claim the service
4. 🤖 Bot verifies the OTT ID exists and hasn't been claimed
5. 🎫 Service is linked to the user's account
6. 🤖 Bot provides access URL and instructions

### 👮 For Admins:
1. 🛠️ Access management commands through the control panel
2. ➕ ➖ 🔁 Create, extend, or delete services as needed
3. 📊 Monitor active services and users
4. 📢 Send announcements to all users

### ⏰ Expiration Management:
1. 🤖 Bot checks for expiring services every minute
2. 🔔 Sends warnings 7, 3, and 1 day before expiration
3. 🚫 Prevents duplicate reminders to the same user on the same day

## 🔒 Security Considerations

1. **🔑 Token Security**: Ensure your bot token remains secret and is not shared in public repositories
2. **👥 Admin Access**: Only trusted users should be added to ADMIN_IDS
3. **👤 User Data**: User information is stored in JSON files locally
4. **🚫 Unique Claims**: Each OTT ID can only be claimed by one user
5. **✅ Input Validation**: The bot validates inputs to prevent errors
6. **⏳ Rate Limiting**: Small delays are implemented when sending bulk messages

## 🆘 Support

For assistance with the bot, contact the administrators listed in the configuration. 📞

## 📄 License

This project is developed for educational and personal use. Modify according to your needs. 📝
