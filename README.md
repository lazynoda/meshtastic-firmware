# Nodastic

**Nodastic** is a fork of the [Meshtastic firmware](https://github.com/meshtastic/firmware). It is based on upstream **v2.8.1** ([`8e6a88d`](https://github.com/meshtastic/firmware/commit/8e6a88d06f44cad26f1e8d7cd402939ccacb9b4c), tag `v2.8.1.8e6a88d`) and keeps the changes small:

- **No NodeInfo reply to broadcast requests.** A broadcast NodeInfo with `want_response` no longer makes every node that hears it reply at once. Unicast requests are still answered.
- **No NodeInfo broadcast on app connect.** The client heartbeat ping (`nonce == 1`) no longer triggers a `want_response` NodeInfo broadcast (BLE/serial and TCP/UDP). Plain heartbeats are unchanged.
- **Baked node identity.** New build-time preference `USERPREFS_CONFIG_SECURITY_PRIVATE_KEY` (32-byte X25519 key). Since 2.8 the NodeNum derives from the public key, so baking the private key keeps the same identity across factory resets and reflashes.
- **Documented `USERPREFS_*` keys.** `userPrefs.jsonc` lists, commented out, build-time preferences the firmware already reads but did not document. No behaviour change.

Full diff against upstream: [v2.8.1.8e6a88d...nodastic](https://github.com/meshtastic/firmware/compare/v2.8.1.8e6a88d...lazynoda:meshtastic-firmware:nodastic)

The original README follows.

---

<div align="center" markdown="1">

<img src=".github/meshtastic_logo.png" alt="Meshtastic Logo" width="80"/>
<h1>Meshtastic Firmware</h1>

![GitHub release downloads](https://img.shields.io/github/downloads/meshtastic/firmware/total)
[![CI](https://img.shields.io/github/actions/workflow/status/meshtastic/firmware/main_matrix.yml?branch=master&label=actions&logo=github&color=yellow)](https://github.com/meshtastic/firmware/actions/workflows/ci.yml)
[![CLA assistant](https://cla-assistant.io/readme/badge/meshtastic/firmware)](https://cla-assistant.io/meshtastic/firmware)
[![Fiscal Contributors](https://opencollective.com/meshtastic/tiers/badge.svg?label=Fiscal%20Contributors&color=deeppink)](https://opencollective.com/meshtastic/)
[![Vercel](https://img.shields.io/static/v1?label=Powered%20by&message=Vercel&style=flat&logo=vercel&color=000000)](https://vercel.com?utm_source=meshtastic&utm_campaign=oss)

<a href="https://trendshift.io/repositories/5524" target="_blank"><img src="https://trendshift.io/api/badge/repositories/5524" alt="meshtastic%2Ffirmware | Trendshift" style="width: 250px; height: 55px;" width="250" height="55"/></a>

</div>

</div>

<div align="center">
	<a href="https://meshtastic.org">Website</a>
	-
	<a href="https://meshtastic.org/docs/">Documentation</a>
</div>

## Overview

This repository contains the official device firmware for Meshtastic, an open-source LoRa mesh networking project designed for long-range, low-power communication without relying on internet or cellular infrastructure. The firmware supports various hardware platforms, including ESP32, nRF52, RP2040/RP2350, and Linux-based devices.

Meshtastic enables text messaging, location sharing, and telemetry over a decentralized mesh network, making it ideal for outdoor adventures, emergency preparedness, and remote operations.

### Get Started

- 🔧 **[Building Instructions](https://meshtastic.org/docs/development/firmware/build)** - Learn how to compile the firmware from source.
- ⚡ **[Flashing Instructions](https://meshtastic.org/docs/getting-started/flashing-firmware/)** - Install or update the firmware on your device.

Join our community and help improve Meshtastic! 🚀

## Stats

![Alt](https://repobeats.axiom.co/api/embed/8025e56c482ec63541593cc5bd322c19d5c0bdcf.svg "Repobeats analytics image")
