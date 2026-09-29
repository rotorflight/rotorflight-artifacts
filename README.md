# rotorflight-artifacts

Copies of Rotorflight firmware builds, for the web version of the
[Rotorflight Configurator](https://rotorflight.github.io/rotorflight-configurator/).

GitHub release downloads don't send CORS headers, so a browser page can't
fetch firmware straight from
[rotorflight-firmware's releases](https://github.com/rotorflight/rotorflight-firmware/releases).
This repo holds the same `.hex` files, which the configurator fetches through
jsDelivr instead:

```
https://cdn.jsdelivr.net/gh/rotorflight/rotorflight-artifacts@master/firmware/<tag>/<file>
```

for example `firmware/release/4.6.0/rotorflight_4.6.0_STM32F405.hex`.

## How it is kept up to date

[`sync-firmware.yml`](.github/workflows/sync-firmware.yml) runs every hour
(and can be run by hand from the Actions tab). It mirrors every release and
snapshot of `rotorflight-firmware` from 4.3.0 onwards, the oldest version the
configurator supports, and removes copies of releases that were deleted.

Don't edit `firmware/` by hand: the next sync overwrites it. The desktop
configurator doesn't use this repo; it downloads from the releases directly.
