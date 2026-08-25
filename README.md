# Flic Hub

[![GitHub Release][releases-shield]][releases]
[![License][license-shield]](LICENSE)

[![Project Maintenance][maintenance-shield]][user_profile]
[![BuyMeCoffee][buymecoffeebadge]][buymecoffee]

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

## Using the Flic Twist dial

Out of the box, a Flic Twist shows up in Home Assistant the same as any other Flic button — you get its `button` entity with `click_type` (single/double/hold), but **turning the dial does nothing by itself**. The Twist's rotation is a separate mechanism from its click events, and it only sends anything to Home Assistant once it's bound to a **virtual device** in the Flic app. This trips a lot of people up (see #62), so here's the setup:

1. In the Flic app, open the **Twist** you want to configure and find its **Twist / Rotate** action slot (as opposed to Push, Double Push, or Push & Twist — each of the Twist's four actions is configured independently).
2. Choose what the rotation should control — e.g. **Brightness**, **Color**, **Saturation**, **Color Temperature**, or **Volume**.
3. Tap **"add devices"**, then choose **Flic Hub Studio** from the list (as opposed to a direct integration like Philips Hue, Matter, IKEA DIRIGERA, etc.).
4. Choose **"add a virtual device"** and pick **Light** (or Speaker/Blinds depending on what you're controlling). Give it a clear name — this name becomes part of the Home Assistant entity name.
5. Confirm the virtual device is assigned as the target of the Twist's Rotate action.

Once that's set up, turning the dial creates (or updates) a `light.*` entity in Home Assistant named after your Twist and the virtual device (e.g. `light.living_room_twist_ha_lamp_dial`), with its `brightness` (or color/color_temp, depending on what you chose in step 2) attribute tracking the dial in real time. You can then read that entity's state in an automation to drive other entities — for example, mirroring its brightness onto a real light group.

This entity is virtual — it doesn't correspond to a physical light. It exists purely as a bridge so Home Assistant can observe the Twist's rotation through the standard `light` entity model.

## Credits

Original integration by [@JohNan](https://github.com/JohNan).

[buymecoffee]: https://www.buymeacoffee.com/JohNan
[buymecoffeebadge]: https://img.shields.io/badge/buy%20me%20a%20coffee-donate-yellow.svg?style=for-the-badge
[license-shield]: https://img.shields.io/github/license/JohNan/home-assistant-flichub.svg?style=for-the-badge
[maintenance-shield]: https://img.shields.io/badge/maintainer-%40JohNan-blue.svg?style=for-the-badge
[releases-shield]: https://img.shields.io/github/release/JohNan/home-assistant-flichub.svg?style=for-the-badge
[releases]: https://github.com/JohNan/home-assistant-flichub/releases
[user_profile]: https://github.com/JohNan
