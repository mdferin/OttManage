# OTT Manager Telegram Bot

A comprehensive Telegram bot for managing OTT (Over-The-Top) service subscriptions with user management, service provisioning, and announcement capabilities.

## Features

### 📺 OTT Service Management
- **Create Services**: Generate new OTT service entries with custom IDs and durations
- **Extend Services**: Extend existing service validity periods
- **Delete Services**: Remove OTT service entries
- **List Services**: View all active services with expiration status indicators
- **Automatic Expiry Notifications**: Daily checks for expiring services with automated user reminders

### 👥 User Management
- **User Registration**: Automatic user registration when they claim services
- **View Users**: List all registered users with their information
- **Delete Users**: Remove user records and their claimed services

### 📢 Announcement System
- **Text Announcements**: Send text messages to all registered users
- **Photo Announcements**: Send photos with captions to all registered users
- **Preview System**: Preview announcements before sending with Cancel/Send options
- **Automatic Cleanup**: Removes both preview and original announcement messages after processing

### 🔐 Security & Access Control
- **Admin-Only Commands**: All management commands restricted to authorized administrators
- **Service Claim Protection**: Prevents duplicate claims and unauthorized access
- **Device Limiting**: Built-in device limit enforcement per service

## Commands

### Admin Commands
- `/create <id> <duration>` - Deploy new OTT service (e.g., `/create rtm-41806 90days`)
- `/extend <id> <duration>` - Extend service validity (e.g., `/extend rtm-41806 30days`)
- `/delete <id>` - Remove OTT service (requires confirmation)
- `/deleteuser <user_id>` - Remove user record
- `/list` - View all active services
- `/users` - View all registered users
- `/announce <message>` - Send announcement to all users (text or photo with caption)

### User Commands
- `/start` - Initialize bot and access services
- `/claim_<id>` - Claim and access OTT services (sent via service links)

## Setup

### Prerequisites
- Python 3.7+
- Telegram Bot Token (obtained from [@BotFather](https://t.me/BotFather))

### Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd ott-manager-bot
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Configure the bot:
   - Set your `BOT_TOKEN` in the code
   - Update `ADMIN_IDS` with your Telegram user IDs
   - Modify `ADMIN_USERNAMES` with corresponding usernames

4. Run the bot:
```bash
python bot.py
```

### Dependencies
- `python-telegram-bot==20.0` - Telegram Bot API wrapper
- `pytz==2023.3` - Timezone handling

## Configuration

### Admin Setup
1. Get your Telegram user ID by messaging [@userinfobot](https://t.me/userinfobot) or using bot commands
2. Add your user ID to the `ADMIN_IDS` list
3. Add your username to the `ADMIN_USERNAMES` dictionary

### Service Configuration
- Services are stored as JSON files in the `database/` directory
- User data is stored as JSON files in the `users/` directory
- Announcements are stored in the `announcements/` directory

## Usage Examples

### Creating a Service
```
/create premium-service-001 90days
```

### Extending a Service
```
/extend premium-service-001 30days
```

### Sending an Announcement
**Text Announcement:**
```
/announce Important update: Server maintenance scheduled for tomorrow.
```

**Photo Announcement:**
Send a photo with the caption:
```
/announce Check out our new premium channels!
```

## Technical Details

### Data Structure
- **Services**: Stored as JSON files with expiration dates, device limits, and playlist information
- **Users**: Stored as JSON files with claimed services, registration dates, and user info
- **Announcements**: Stored as JSON files with message content and delivery metadata

### Automatic Features
- **Daily Expiry Checks**: Runs daily at 09:00 Malaysia time to check for expiring services
- **User Notifications**: Automatically sends reminders to users 7, 3, and 1 day before service expiration
- **Folder Management**: Automatically creates required directories on startup

### Error Handling
- Comprehensive error handling for file operations, network issues, and user input
- Detailed logging for debugging and monitoring
- Graceful degradation when individual operations fail

## Contributing
1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a pull request

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support
For support, contact the administrators listed in the bot's admin panel or open an issue on GitHub.