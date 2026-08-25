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
> **This fork fixes that** by marshalling the dynamic entity creation onto the Home Assistant event loop, so the Twist's virtual-device light entity is created cleanly and the dial can be used (e.g. to drive brightness). This fork also maps the dial directly and proportionally to brightness, with no ramping or centering behavior.
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
