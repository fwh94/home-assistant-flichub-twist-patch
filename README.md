# Flic Hub

[![GitHub Release][releases-shield]][releases]
[![License][license-shield]](LICENSE)

[![Project Maintenance][maintenance-shield]][user_profile]
[![BuyMeCoffee][buymecoffeebadge]][buymecoffee]

> ## ⚠️ This is a patched fork
>
> This is a fork of [JohNan/home-assistant-flichub](https://github.com/JohNan/home-assistant-flichub), created specifically to fix the **Flic Twist dial (rotation) not working**.
>
> On the upstream integration, turning a Flic Twist that's bound to a Flic Hub Studio virtual device causes the integration to crash while creating the light entity, with `RuntimeError: loop ... is not the running loop` and `coroutine 'async_add_entities' was never awaited`. The rotation events reach Home Assistant, but the virtual-device light entity is never created, so the dial does nothing.
>
> **This fork fixes that** by marshalling the dynamic entity creation onto the Home Assistant event loop, so the Twist's virtual-device light entity is created cleanly and the dial can be used (e.g. to drive brightness). This fork also lets you choose, per Twist, how the dial responds — see "Dial response mode" below.
>
> If/when the crash fix is merged upstream, prefer the original repository.

## Prerequisites

Add the tcp client to Flic Hub found in this repo: https://github.com/JohNan/pyflichub-tcpclient

### Install with HACS (recommended)
Add the url to the repository as a custom integration.

## Installation

1. Using the tool of choice open the directory (folder) for your HA configuration (where you find `configuration.yaml`).
2. If you do not have a `custom_components` directory (folder) there, you need to create it.
3. In the `custom_components` directory (folder) create a new folder called `flichub`.
4. Download _all_ the files from the `custom_components/flichub/` directory (folder) in this repository.
5. Place the files you downloaded in the new directory (folder) you created.
6. Restart Home Assistant
7. In the HA UI go to "Configuration" -> "Integrations" click "+" and search for "Flic Hub"

## Dial response mode

If you have a Flic Twist, each one shows up as its own dropdown in Settings → Devices & Services → Flic Hub LR → Configure. Pick whichever feel matches how you want to use it:

- **Direct** (the default) — turn the dial to a spot, and the light goes to that exact level, every time. Works like a normal dimmer knob on a lamp.
- **Joystick** — turn the dial away from center and hold it there to make the light ramp up or down, the further you turn the faster it ramps; let go and it stops. Works more like a game controller's analog stick than a dimmer knob.

Most people want **Direct**. **Joystick** can feel nicer if you're adjusting several lights at once and want fine, held control rather than picking an exact spot each time.

### DHCP Discovery
Your FlicHub should automatically be discovered as a new integration based on dhcp discovery.
If that doesn't work it can be setup manually by doing step 7 in the installation instructions

[buymecoffee]: https://www.buymeacoffee.com/JohNan
[buymecoffeebadge]: https://img.shields.io/badge/buy%20me%20a%20coffee-donate-yellow.svg?style=for-the-badge
[license-shield]: https://img.shields.io/github/license/JohNan/home-assistant-flichub.svg?style=for-the-badge
[maintenance-shield]: https://img.shields.io/badge/maintainer-%40JohNan-blue.svg?style=for-the-badge
[releases-shield]: https://img.shields.io/github/release/JohNan/home-assistant-flichub.svg?style=for-the-badge
[releases]: https://github.com/JohNan/home-assistant-flichub/releases
[user_profile]: https://github.com/JohNan
