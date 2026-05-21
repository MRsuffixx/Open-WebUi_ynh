# Open WebUI - Post-Installation Guide

## Accessing Open WebUI

After installation, Open WebUI is accessible at:
- **URL**: `https://__DOMAIN____PATH__`

## First-Time Setup

### 1. Access the Application

Open your browser and navigate to the installation URL. You will be automatically authenticated via YunoHost's SSO/LDAP system if you're logged into the YunoHost portal.

### 2. Admin Configuration

The user selected during installation has full admin privileges. As admin, you can:

- Manage users and permissions
- Configure AI model backends
- Adjust application settings
- View system statistics

### 3. Connect AI Models

#### For Ollama (Local Models)

If you have Ollama installed on your server:

1. Go to **Settings** → **Models**
2. Open WebUI should automatically detect Ollama
3. Download models from the interface or use: `ollama pull llama2`

#### For OpenAI API

1. Go to **Settings** → **API Keys**
2. Enter your OpenAI API key
3. Select your preferred model

### 4. Configure Model Backend

Go to **Settings** → **Admin Panel** → **Models**:

- Set the default model
- Configure Ollama URL if using local models
- Adjust inference parameters

## Important Paths

| Path | Description |
|------|-------------|
| `__INSTALL_DIR__` | Installation directory (venv, app code) |
| `__DATA_DIR__` | Data directory (database, models, uploads) |

## Next Steps

1. **Add Users**: Grant access to other YunoHost users via YunoHost permissions
2. **Download Models**: Start by downloading a small model like llama2 or mistral
3. **Configure Ollama**: If using local models, ensure Ollama is running

## Troubleshooting

### "Service unavailable" Error

Wait a few seconds and refresh. Open WebUI takes about 10-15 seconds to start.

### Authentication Not Working

- Ensure you're logged into YunoHost portal
- Check that your user has access to the application

### Models Not Appearing

- Verify Ollama is running: `sudo systemctl status ollama`
- Check model directory permissions: `ls -la /home/yunohost.app/open-webui/models`

## Getting Help

- **Documentation**: https://docs.openwebui.com/
- **Support**: https://github.com/YunoHost-Apps/open-webui_ynh/issues