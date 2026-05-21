# Open WebUI for YunoHost

[![Integration level](https://dash.yunohost.org/integration/open-webui.svg)](https://dash.yunohost.org/appci/app/open-webui) ![Working status](https://ci-apps.yunohost.org/ci/badges/open-webui.status.svg) ![Maintenance status](https://ci-apps.yunohost.org/ci/badges/open-webui.maintain.svg)<br>
[![Install Open WebUI with YunoHost](https://install-app.yunohost.org/install-with-yunohost.svg)](https://install-app.yunohost.org/?app=open-webui)

*[Read this readme in français.](./README_fr.md)*

> *This package allows you to install Open WebUI quickly and simply on a YunoHost server.
> If you don't have YunoHost, please consult [the guide](https://doc.yunohost.org/admin/get_started/install_on/) to learn how to install it.*

## Overview

Open WebUI is an extensible, self-hosted AI interface featuring OpenAI API support with a ChatGPT-like UI for complete autonomy. It provides a modern web interface for interacting with AI models, supporting both local (Ollama) and remote (OpenAI-compatible) model backends.

### Features

- **ChatGPT-like Interface**: Modern, intuitive web UI for AI conversations
- **SSO/LDAP Authentication**: Integrated with YunoHost's authentication system
- **WebSocket Support**: Real-time streaming responses for smooth interactions
- **Multi-Model Support**: Connect to Ollama, OpenAI, and other OpenAI-compatible APIs
- **Model Management**: Download and manage AI models directly from the interface
- **File Upload**: Support for document uploads (PDF, TXT, DOCX, etc.)
- **Admin Panel**: Full admin controls for user and settings management
- **Self-Hosted**: Complete control over your AI infrastructure

**Shipped version:** 0.3.31~ynh1

**Demo:** https://sentencebook.com

## Screenshots

![Screenshot of Open WebUI](./doc/screenshots/open-webui.png)

## Disclaimers / Important Information

### Authentication

- Open WebUI uses YunoHost's SSOwat/LDAP for authentication
- Users are automatically logged in when accessing via the YunoHost portal
- Admin access is granted to the user selected during installation

### System Requirements

- **Disk Space**: Minimum 2GB for installation, more for AI models
- **RAM**: Minimum 1GB runtime, more recommended for model inference
- **Architecture**: Works on all YunoHost-supported architectures (amd64, i386, armhf, arm64)

### WebSocket Support

- AI model downloads and chat streams require WebSocket support
- This is automatically configured by the package
- Timeouts are set to 24 hours for long-running AI operations

### Model Storage

- Models are stored in `/home/yunohost.app/open-webui/models`
- Downloads can use significant disk space
- File uploads are stored in `/home/yunohost.app/open-webui/uploads` (10GB limit)

### Upgrade Process

- Upgrades run migrations with a single worker to prevent SQLite database corruption
- The service is briefly stopped during upgrades (typically under 2 minutes)
- No data loss occurs as the data directory is preserved

## Documentation and Resources

* Official app website: <https://openwebui.com>
* Official user documentation: <https://docs.openwebui.com/>
* Official admin documentation: <https://docs.openwebui.com/>
* Upstream app code repository: <https://github.com/open-webui/open-webui>
* YunoHost documentation for this app: <https://yunohost.org/app_open-webui>
* Report a bug: <https://github.com/YunoHost-Apps/open-webui_ynh/issues>

## Developer Info

Please send your pull requests to the [testing branch](https://github.com/YunoHost-Apps/open-webui_ynh/tree/testing).

To try the testing branch, please proceed like this:

```bash
sudo yunohost app install https://github.com/YunoHost-Apps/open-webui_ynh/tree/testing --debug
```

or

```bash
sudo yunohost app upgrade open-webui -u https://github.com/YunoHost-Apps/open-webui_ynh/tree/testing --debug
```

**More info regarding app packaging:** <https://doc.yunohost.org/dev/packaging/>

## License

This package is published under the MIT license. See the [LICENSE](./LICENSE) file for details.