---
title: Zimi Cloud Controller
description: Access and control your Zimi Cloud Controller and its connected Zimi-based devices.
featured: false
ha_iot_class: Local Push
ha_release: "2024.3.0"
ha_codeowners:
  - '@markhannon'
  - '@mhannon11'
ha_category:
  - Cover
  - Fan
  - Light
  - Sensor
  - Switch
ha_domain: zimi
---

The Zimi integration allows you to connect your Zimi Cloud Controller to Home Assistant and via this integration control all of the local devices connected to the Zimi mesh.

(See [Zimi's website](https://zimi.life/) for details of the Zimi portfolio).

## Supported Devices

The following Zimi devices are supported:

- Zimi Cloud Connect ([links to specifications](https://zimi.life/product/cloud-connect/))

## Unsupported Devices

The following Zimi devices are not yet supported:

- Zimi Matter Connect ([links to specifications](https://zimi.life/product/cloud-connect/))

## Prerequisites

A configured Zimi Cloud Connect and internet connection is needed for this integration to work.

1. Open the app store and install the Zimi app.
2. Open the Zimi app and configure a Zimi network by adding and naming all Zimi devices.
3. Open the Zimi app and configure a Zimi Cloud Connect device.
4. Take a note of the Zimi Cloud Connect IP address and MAC address.
5. Configure the Zimi integration using standard configuration flow.

{% include integrations/config_flow.md %}

You will be prompted to configure the Zimi Cloud Connect through the Home Assistant interface.

{% configuration_basic %}
host:
    description: "The IP address of your Zimi Cloud Connect. You can find it via your router admin interface.    If no IP address is entered the integration will attempt to discover a Zimi Cloud Connect via a broadcast message on the local LAN."
port:
    description: "The port number used to connect to your Zimi Cloud Connect.   If no port number is entered the integration will use the default port.   (The default port will be correct in almost all deployment scenarios)"
mac:
    description: "The MAC address printed on the back of the Zimi Cloud Connect device (required)."
{% endconfiguration_basic %}

It is possible to add multiple Zimi Cloud Connect devices.

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



## Data updates

The integration is pushed updates from the Zimi Cloud Controller instantly via the Zimi API.

## Known limitations

1. Entity name changes made in the Zimi app will not be reflected in Home Assistant until after a restart. This is because entity names are only read during integration setup and Home Assistant startup.

## Removing the integration

This integration follows standard integration removal. No extra steps are required.

{% include integrations/remove_device_service.md %}

## Troubleshooting

### Missing Zimi devices

If there are missing Zimi devices after the initial integration, you may have to run the discovery process again.

To do this:

1. Go to **Settings** > **Devices & Services**
2. Click on **Zimi**
3. Click **Add Hub**
This will re-run the discovery process.

### Device Authorization Failure

Due to the authorization lifecycle of the Zimi Cloud Controller, the device implements rate limiting on authorization requests. If you exceed these limits
(typically more than 3-5 requests within a few minutes), the device will temporarily reject new connection attempts. If you encounter this issue, you'll
need to wait for the rate limit to reset.

To do this:

1. Remove the integration from **Settings** > **Devices & Services** > **Zimi**
2. Wait for approximately 5 minutes
3. Try adding the integration again
