# Open WebUI - Pre-Upgrade Notes

## Before Upgrading

### Backup Recommendation

Before upgrading Open WebUI, it is recommended to:

1. **Create a full backup**:
   ```bash
   sudo yunohost backup create --apps open-webui
   ```

2. **Note important settings**: If you've customized the `.env` file, document your customizations.

### Check Current Version

```bash
sudo yunohost app info open-webui
```

## Upgrade Process

### What Happens During Upgrade

1. **Service Stop**: The Open WebUI service is stopped
2. **Single-Worker Migration**: Database migrations run with 1 worker (prevents SQLite corruption)
3. **Package Update**: Python packages are upgraded via pip
4. **Service Restart**: Service restarts with 4 workers
5. **Health Check**: Service is verified to be responding

### Expected Duration

- **Typical upgrade**: 2-5 minutes
- **First-time upgrade** (from older version): May take longer due to initial setup

## Potential Issues

### Service Doesn't Start After Upgrade

If the service fails to start:

1. Check logs: `sudo tail -f /var/log/open-webui/open-webui.log`
2. Check system logs: `journalctl -u open-webui -n 50`
3. Verify permissions: `ls -la /opt/open-webui/`
4. Check database: `sqlite3 /home/yunohost.app/open-webui/webui.db "PRAGMA integrity_check;"`

### Database Corruption

If database corruption is detected:

1. Stop the service
2. Restore from backup: `sudo yunohost backup restore <backup_name> --apps open-webui`

### Configuration Reset

If your `.env` customizations are lost:

1. Edit the new `.env`: `sudo nano /opt/open-webui/.env`
2. Re-apply your custom settings
3. Restart: `sudo yunohost service restart open-webui`

## Rollback

If the upgrade fails and you need to rollback:

```bash
# List backups
sudo yunohost backup list

# Restore previous backup
sudo yunohost backup restore <backup_name> --apps open-webui
```

## Changelog

Check the [Open WebUI GitHub releases](https://github.com/open-webui/open-webui/releases) for version-specific notes.