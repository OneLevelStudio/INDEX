# INDEX

Convenience script to start custom docker instances

## SilverBullet

```
mkdir -p DATA_SILVERBULLET/_plug                                                                                         && \
wget -P DATA_SILVERBULLET https://raw.githubusercontent.com/OneLevelStudio/INDEX/refs/heads/main/CONFIG.md               && \
wget -P DATA_SILVERBULLET/_plug https://raw.githubusercontent.com/OneLevelStudio/INDEX/refs/heads/main/treeview.plug.js  && \
docker run -d \
  --name silverbullet \
  --restart unless-stopped \
  -e SB_HOSTNAME=0.0.0.0 \
  -e SB_USER=admin:admin \
  -p 1234:3000 \
  -v ./DATA_SILVERBULLET:/space \
  ghcr.io/silverbulletmd/silverbullet:v2
```

## Nextcloud

```
docker run -d \
  --name nextcloud \
  --restart unless-stopped \
  -p 9000:80 \
  -p 9001:443 \
  -v ./DATA_NEXTCLOUD:/var/www/html \
  nextcloud:31.0
```
