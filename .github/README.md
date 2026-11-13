# Tuya Local (Sam)

A personal fork of [**Tuya Local**](https://github.com/make-all/tuya-local) for Home Assistant, maintained by [@sambarlick](https://github.com/sambarlick).

Tuya Local controls Tuya-based devices directly over your local network, with no cloud round-trip. All of the integration's code is upstream's work. This fork adds device configs for my own hardware and ships a slimmed-down build.

> **Looking for Tuya Local itself?** Use the upstream repository: [make-all/tuya-local](https://github.com/make-all/tuya-local). This fork is tuned to my devices and isn't intended as a general replacement.

## What's different

- **Device-specific configs.** My devices each have their own config (`*_sam_*.yaml`), written from the device's Tuya data model and locked to its product ID. Several fix problems in the generic upstream configs they replace, for example:
  - **Kogan portable aircon:** heat mode now works (the device sends `HEAT`, not `Heat`), and the timer, defrost, tank-full and auto-dry functions are mapped instead of showing as `unknown_*`.
  - **Arlec Grid Connect fan:** only the modes the fan really has, and the full 1–9 h timer.
  - **Kogan fan with oscillation angle:** a new config, with a 30°/60°/90° angle select.
- **Slim release.** The repo stays a full mirror of upstream, but each release zip contains only the configs listed in [`slim-devices.txt`](../slim-devices.txt): my own configs, plus a few generic fallbacks for adding new devices. Upstream configs that my own files replace are excluded.
- **Branded manifest.** Releases install as *Tuya Local (Sam)*, with this repo as the documentation and issue tracker. The internal domain is still `tuya_local`, so it's a drop-in swap for the upstream integration (not side by side).
- **Automatic builds.** Every push to `main` builds a release (`YYYY.M.D.<run>`). Upstream is merged in monthly.

## Installing

1. In HACS, remove the upstream Tuya Local if it's installed. Both use the `tuya_local` domain.
2. Add `https://github.com/sambarlick/tuya-local` as a custom repository (type: Integration).
3. Install **Tuya Local**, then restart Home Assistant.

Release notes list my device configs, newest first.

## Issues

- **Problems with one of my `*_sam_*` configs, or with the slim build:** open an issue [here](https://github.com/sambarlick/tuya-local/issues).
- **Anything else** (the integration itself, other devices): please check [upstream](https://github.com/make-all/tuya-local/issues). Upstream can't support this fork.

## Credit and licence

Tuya Local is created by Nik Rolls and maintained by Jason Rumney ([@make-all](https://github.com/make-all)), with many contributors listed in [ACKNOWLEDGEMENTS.md](../ACKNOWLEDGEMENTS.md). Thank you all: this fork exists only because of your work.

Licensed under the MIT licence, unchanged from upstream. See [LICENSE.md](../LICENSE.md).
