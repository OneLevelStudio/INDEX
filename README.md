# INDEX

Convenience script to start custom docker instances

## SilverBullet

```
mkdir -p data_silverbullet/_plug                                                                                         && \
wget -P data_silverbullet https://raw.githubusercontent.com/OneLevelStudio/INDEX/refs/heads/main/CONFIG.md               && \
wget -P data_silverbullet/_plug https://raw.githubusercontent.com/OneLevelStudio/INDEX/refs/heads/main/treeview.plug.js  && \
docker run -d \
  --name silverbullet \
  --restart unless-stopped \
  -e SB_HOSTNAME=0.0.0.0 \
  -e SB_USER=admin:admin \
  -p 1234:3000 \
  -v ./data_silverbullet:/space \
  ghcr.io/silverbulletmd/silverbullet:v2
```

## Nextcloud

```
docker run -d \
  --name nextcloud \
  --restart unless-stopped \
  -p 9000:80 \
  -p 9001:443 \
  -v ./data_nextcloud:/var/www/html \
  nextcloud:31.0
```
