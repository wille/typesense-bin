# typesense-bin

Arch Linux AUR package for [Typesense](https://typesense.org/), a fast, typo-tolerant search engine.

## Post-Installation

After installing, you **must** update the configuration file before starting the service:

```bash
sudo nano /etc/typesense/typesense-server.ini
```

Change the `api-key` from the default value to a secure key:

```ini
api-key = your-secure-api-key-here
```

You can generate a secure key with:

```bash
openssl rand -hex 32
```

## Starting the Service

Once configured, enable and start the service:

```bash
sudo systemctl enable --now typesense-server
```

## Configuration

The configuration file is located at `/etc/typesense/typesense-server.ini`. See the [Typesense documentation](https://typesense.org/docs/latest/api/server-configuration.html) for all available options.

Default settings:
- **Data directory**: `/var/lib/typesense`
- **API address**: `127.0.0.1` (localhost only)
- **API port**: `8108`
