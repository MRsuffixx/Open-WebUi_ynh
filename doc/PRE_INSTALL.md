# Open WebUI - Pre-Installation Requirements

## System Requirements

### Hardware Requirements

- **CPU**: Modern multi-core processor (recommended for AI inference)
- **RAM**: Minimum 1GB, recommended 4GB+ for model inference
- **Disk Space**: Minimum 2GB for installation, 10GB+ recommended for AI models

### Architecture Support

Open WebUI works on all YunoHost-supported architectures:
- amd64 (Intel/AMD 64-bit)
- i386 (Intel/AMD 32-bit)
- armhf (ARM 32-bit)
- arm64 (ARM 64-bit)

## Prerequisites

### 1. YunoHost Version

- Requires **YunoHost 12.1.17** or higher
- Check your version: `sudo yunohost --version`

### 2. Domain Configuration

- A dedicated domain or subdomain is required
- DNS must be properly configured
- SSL certificate will be auto-provisioned by Let's Encrypt

### 3. Dependencies

The following packages are automatically installed:
- `python3-pip` - Python package manager
- `python3-venv` - Python virtual environment support
- `sqlite3` - SQLite database engine

## Optional: Ollama for Local Models

For local AI model inference, you may want to install Ollama beforehand:

```bash
# Install Ollama (on Debian/Ubuntu)
curl -fsSL https://ollama.com/install.sh | sh

# Start Ollama service
sudo systemctl enable ollama
sudo systemctl start ollama

# Download a model
ollama pull llama2
```

Note: Ollama installation is optional - Open WebUI can also use OpenAI's API.

## Network Requirements

### Ports

- **Internal Port**: Random port (automatically assigned by YunoHost)
- **External Access**: Via Nginx reverse proxy on HTTPS (443)

### WebSocket Support

WebSocket support is automatically configured and required for:
- Real-time chat streaming
- AI model downloads
- Live progress updates

## User Permissions

### Initial Admin User

During installation, you must select:
1. **Domain**: Where Open WebUI will be accessible
2. **Path**: URL path (default: `/webui`)
3. **Admin User**: YunoHost user who will have admin access

### Access Control

- By default, the app is accessible to "visitors" (anyone with domain access)
- Adjust permissions after installation via YunoHost admin panel

## Preparation Checklist

Before installing, ensure you have:

- [ ] YunoHost 12.1.17+ installed and working
- [ ] Domain/subdomain ready with DNS configured
- [ ] Admin user account created in YunoHost
- [ ] Sufficient disk space for models (optional)
- [ ] Ollama installed (if using local models, optional)

## Next Step

Once prerequisites are met, proceed with the installation.