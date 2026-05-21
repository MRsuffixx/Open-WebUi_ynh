# Open WebUI - Administrator Documentation

## Installation Directory

- **Install Directory**: `/opt/open-webui`
- **Virtual Environment**: `/opt/open-webui/venv`
- **Configuration File**: `/opt/open-webui/.env`

## Data Directories

- **Data Directory**: `/home/yunohost.app/open-webui`
- **Database**: `/home/yunohost.app/open-webui/webui.db` (SQLite)
- **Models Cache**: `/home/yunohost.app/open-webui/models`
- **File Uploads**: `/home/yunohost.app/open-webui/uploads`

## Logs

- **Application Log**: `/var/log/open-webui/open-webui.log`
- **Error Log**: `/var/log/open-webui/open-webui.err.log`

View logs in real-time:
```bash
tail -f /var/log/open-webui/open-webui.log
```

## Service Management

### Start/Stop/Restart
```bash
sudo yunohost service start open-webui
sudo yunohost service stop open-webui
sudo yunohost service restart open-webui
```

### Check Status
```bash
sudo yunohost service status open-webui
```

### View Service Logs
```bash
sudo yunohost service log open-webui
```

## Configuration

### Environment Variables

Edit the `.env` file to configure Open WebUI:
```bash
sudo nano /opt/open-webui/.env
```

Key settings:
- `GLOBAL_LOG_LEVEL`: Logging verbosity (DEBUG, INFO, WARNING, ERROR)
- `WEBUI_AUTH`: Enable/disable authentication
- `OLLAMA_BASE_URL`: Ollama endpoint (default: http://localhost:11434)
- `OPENAI_API_KEY`: Your OpenAI API key
- `DATA_DIR`: Data directory path

After editing `.env`, restart the service:
```bash
sudo yunohost service restart open-webui
```

## Users and Authentication

### SSO/LDAP Authentication

Open WebUI uses YunoHost's SSOwat/LDAP for authentication. Users must:
1. Be logged into YunoHost portal
2. Have access to the Open WebUI application (via permissions)

### Admin Access

The admin user selected during installation has full admin access to Open WebUI.

## Ollama Integration

To use local AI models with Ollama:

1. Install Ollama on your server
2. Configure Ollama to listen on localhost:11434
3. Download models: `ollama pull llama2`
4. Open WebUI will automatically detect Ollama models

## Troubleshooting

### Service Won't Start

Check the logs:
```bash
journalctl -u open-webui -n 100
tail -f /var/log/open-webui/open-webui.log
```

### Database Issues

The SQLite database is at `/home/yunohost.app/open-webui/webui.db`. If corrupted:

1. Stop the service: `sudo yunohost service stop open-webui`
2. Remove the database: `sudo rm /home/yunohost.app/open-webui/webui.db`
3. Restart the service: `sudo yunohost service start open-webui`

Note: This will reset all user data and settings.

### WebSocket Connection Issues

Ensure Nginx is properly configured with WebSocket support. Check:
```bash
sudo nginx -t
sudo systemctl reload nginx
```

### High Memory Usage

AI model inference requires significant RAM. Monitor with:
```bash
htop
```

Consider using smaller models or limiting concurrent requests.