# Folio Fonts

Downloadable reading fonts for [Folio Reader](https://github.com/folio-etc/folio),
distributed as `.cpfont` files.

## Layout

```
sd-fonts.yaml    # the font catalog: families, sizes, sources, descriptions
```

The build engine (`build-sd-fonts.py`, `fontconvert_sdcard.py`,
`generate-font-manifest.py`) lives in the firmware repo, so the release workflow
checks it out rather than vendoring it here. Adding or changing a font is a
single edit to `sd-fonts.yaml`.

## Releases

The [Build & Publish SD Card Fonts](.github/workflows/release-fonts.yml)
workflow (`workflow_dispatch`) builds every family in `sd-fonts.yaml`, generates
`fonts.json`, and publishes them as Release assets. The device downloads from
the stable `sd-fonts-m<manifest>-b<cpfont>` tag.

No secrets required: the build engine is checked out from the public firmware
repo with the default `GITHUB_TOKEN`, and releases are published to this same
repo via the workflow's `contents: write` permission.

## Installing fonts on your device

### From the device (recommended)

1. Go to **Settings > System > Manage Fonts**
2. Connect to WiFi when prompted
3. Browse available fonts and select one to download
4. The font appears in **Settings > Reader > Font Family**

### Manual SD card copy

Download `.cpfont` files from the latest
[release](https://github.com/folio-etc/folio-fonts/releases) and copy them into
a family folder on the SD card:

```
SD Card Root/
└── fonts/
    └── Literata/
        ├── Literata_12.cpfont
        ├── Literata_14.cpfont
        ├── Literata_16.cpfont
        └── Literata_18.cpfont
```
