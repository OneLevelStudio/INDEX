# INDEX

Convenience script to start a custom SilverBullet instance

```
mkdir -p silverbullet                                                                                               && \
mkdir -p silverbullet/_plug                                                                                         && \
wget -P silverbullet https://raw.githubusercontent.com/OneLevelStudio/INDEX/refs/heads/main/CONFIG.md               && \
wget -P silverbullet/_plug https://raw.githubusercontent.com/OneLevelStudio/INDEX/refs/heads/main/treeview.plug.js  && \
docker run -d \
  --name silverbullet \
  --restart unless-stopped \
  -e SB_HOSTNAME=0.0.0.0 \
  -e SB_USER=admin:admin \
  -p 1234:3000 \
  -v ./silverbullet:/space \
  ghcr.io/silverbulletmd/silverbullet:v2
```