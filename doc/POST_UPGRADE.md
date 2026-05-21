# Open WebUI - Post-Upgrade Guide

## Verification

After upgrading, verify the service is running:

```bash
sudo yunohost service status open-webui
```

Check the logs:
```bash
sudo tail -20 /var/log/open-webui/open-webui.log
```

## Access the Application

Your installation URL remains the same:
- **URL**: `https://__DOMAIN____PATH__`

## What's New

Check the [Open WebUI releases](https://github.com/open-webui/open-webui/releases) for new features in this version.

## Configuration Changes

### New Environment Variables

The upgrade may add new environment variables to the `.env` file. Check for any new settings in:
```bash
cat /opt/open-webui/.env
```

### Restart May Be Needed

If you notice any issues:
```bash
sudo yunohost service restart open-webui
```

## Data Preservation

Your data is safe:
- Database: `/home/yunohost.app/open-webui/webui.db` ✅ Preserved
- Models: `/home/yunohost.app/open-webui/models` ✅ Preserved
- Uploads: `/home/yunohost.app/open-webui/uploads` ✅ Preserved

## Common Post-Upgrade Tasks

### Clear Browser Cache (if experiencing issues)

Modern browsers may cache old JavaScript. Clear cache or use incognito mode.

### Verify WebSocket Connection

Test that WebSocket connections work:
1. Start a chat conversation
2. Verify responses stream in real-time

### Check Model Availability

Models should still be available. If models are missing:
- Go to Settings → Models
- Re-scan for models if needed

## Troubleshooting

### "Service unavailable" After Upgrade

1. Wait 30 seconds and refresh
2. Check service status: `sudo yunohost service status open-webui`
3. View logs: `journalctl -u open-webui -n 50`

### Slow Response Times

After upgrade, first requests may be slower as the system re-initializes. This is normal and should resolve within a few minutes.

### Missing Settings

If custom settings were lost, re-apply them to `/opt/open-webui/.env` and restart the service.

## Support

If issues persist:
- **Documentation**: https://docs.openwebui.com/
- **Issues**: https://github.com/YunoHost-Apps/open-webui_ynh/issues