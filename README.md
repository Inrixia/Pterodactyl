# Pterodactyl Blueprint Custom Images

Images with plugins pre-installed

## Building

```bash
docker build -t pterod-panel:latest ./panel
docker build -t pterod-wings:latest ./wings
```

## modpack-installer

Can be downloaded from <https://builtbybit.com/resources/modpack-installer-for-blueprint.40083>

Extract `egg-minecraft--java-edition-modpack-installer.json` from `modpackinstaller.blueprint`, copy it and **modpackinstaller.blueprint** to `panel\plugins`
Copy `wings.patch` to `wings`
