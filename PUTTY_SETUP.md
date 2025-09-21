# Setting up OTT Bot with Systemd using PuTTY

This guide will help you set up your OTT Telegram bot on a VPS using systemd for automatic startup and management, using PuTTY for Windows.

## Prerequisites

1. PuTTY installed on your Windows machine
2. Access to a VPS running Ubuntu/Debian
3. Your bot files ready for upload

## Setup Steps

### 1. Connect to your VPS using PuTTY

1. Open PuTTY
2. Enter your VPS IP address in the "Host Name" field
3. Make sure port is set to 22 (or your custom SSH port)
4. Click "Open" and log in with your credentials

### 2. Install required packages

```bash
sudo apt update
sudo apt install -y python3 python3-pip nginx git
```

### 3. Create the project directory

```bash
sudo mkdir -p /var/www/ott
sudo chown $USER:$USER /var/www/ott
```

### 4. Upload your bot files to the VPS

There are several ways to upload files using PuTTY:

#### Option A: Using PSCP (PuTTY Secure Copy Client)

1. Open a new Command Prompt on your Windows machine (not in PuTTY)
2. Navigate to the directory containing your bot files
3. Use PSCP to copy files to your VPS:
   ```cmd
   pscp -r * username@your_vps_ip:/var/www/ott/
   ```

#### Option B: Using PSFTP (PuTTY SFTP Client)

1. Open PSFTP from your Windows machine
2. Connect to your VPS:
   ```cmd
   psftp username@your_vps_ip
   ```
3. Upload files:
   ```cmd
   put -r *
   ```

#### Option C: Using WinSCP

For easier file transfers, you might want to use WinSCP, which has a graphical interface.

### 5. Set proper permissions

```bash
sudo chown -R $USER:$USER /var/www/ott
sudo chmod +x /var/www/ott/bot.py
```

### 6. Install Python dependencies

```bash
cd /var/www/ott
pip3 install -r requirements.txt
```

### 7. Set up the systemd service

Copy the service file to the systemd directory:

```bash
sudo cp /var/www/ott/ott.service /etc/systemd/system/ott.service
```

### 8. Reload systemd and start the service

```bash
sudo systemctl daemon-reload
sudo systemctl enable ott
sudo systemctl start ott
```

### 9. Check the service status

```bash
sudo systemctl status ott
```

If everything is set up correctly, you should see the service running.

## Managing the Service

- **Start the service**: `sudo systemctl start ott`
- **Stop the service**: `sudo systemctl stop ott`
- **Restart the service**: `sudo systemctl restart ott`
- **Check status**: `sudo systemctl status ott`
- **View logs**: `sudo journalctl -u ott -f`

## Updating the Bot

When you need to update your bot:

1. Stop the service: `sudo systemctl stop ott`
2. Upload your new files to `/var/www/ott/` (using PSCP, PSFTP, or WinSCP)
3. Restart the service: `sudo systemctl start ott`

## Troubleshooting

If the service fails to start:

1. Check the logs: `sudo journalctl -u ott -f`
2. Verify file permissions: `ls -la /var/www/ott/`
3. Check that all dependencies are installed: `pip3 list | grep -E "(python-telegram-bot|pytz)"`
4. Make sure the bot token in your bot.py is correct