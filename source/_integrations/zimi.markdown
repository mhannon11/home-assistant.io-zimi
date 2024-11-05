---
title: Zimi Cloud Controller
description: Access and control your Zimi Cloud Controller and its connected Zimi-based devices.
featured: false
ha_iot_class: Local Polling
ha_release: "2024.3.0"
ha_codeowners:
  - '@markhannon'
ha_category:
  - Cover
  - Fan
  - Light
  - Sensor
  - Switch
ha_domain: zimi
---

The Zimi integration allows you to connect your Zimi Cloud Controller to Home Assistant.

(See https://zimi.life/ for details of the Zimi portfolio).

The Zimi Cloud Controller can control compatible Zimi-based devices connected to it.

## Supported Devices

The following Zimi devices are supported:

- Zimi Cloud Connect ([links to specifications](https://zimi.life/product/cloud-connect/))

## Available Entities

When you add a supported device, the following entities will be created:

### Zimi Cover Controller

- Cover entity: Basic position control

### Zimi Fan Controller

- Fan entity: Basic on/off and speed control

### Zimi Light Controller

- Light entity: Basic on/off and brightness control

### Zimi Switch Controller

- Switch entity: Basic on/off

## Unsupported Devices

The following Zimi devices are not yet supported:

- Zimi Matter Connect ([links to specifications](https://zimi.life/product/cloud-connect/))

{% include integrations/config_flow.md %}

You will be prompted to configure the gateway through the Home Assistant interface. The configuration process is very simple: when prompted, enter the your Zimi Cloud Controller IP and port, or leave the IP blank for auto-discovery on LAN.

<div class='note'>
If you see an "Unexpected error" message, restart the gateway and try again. Don't forget to assign a permanent IP address to your Zimi Cloud Controller on your router.
</div>


## Troubleshooting

### Missing Zimi devices

If there are missing Zimi devices after the initial integration, you may have to run thee discovery process again.

To do this:

1. Go to **Settings** > **Devices & Services**
2. Click on **Zimi**
3. Click **Add Hub**
This will re-run the discovery process.

### Device Authorization Failure

Due to the authorization lifecycle of the Zimi Cloud Controller, when too many authorization requests are sent in a short period of time the device may
be unable to be connected to. If you are encountering authorization issues, remove the integration, wait a short period, then try again.

To do this:

1. Remove the integration from **Settings** > **Devices & Services** > **Zimi**
2. Wait for approximately 5 minutes
3. Try adding the integration again