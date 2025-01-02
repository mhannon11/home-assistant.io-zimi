---
title: Zimi Cloud Controller
description: Access and control your Zimi Cloud Controller and its connected Zimi-based devices.
featured: false
ha_iot_class: Local Push
ha_release: "2024.3.0"
ha_codeowners:
  - '@markhannon', '@mhannon11'
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

Home Assistant can then be used to control all Zimi devices connected to the Zimi Cloud Controller.

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
    description: "The MAC address printed on the back of the Zimi Cloud Connect device.   This is a mandatory field and must be entered."
{% endconfiguration_basic %}

It is possible to add multiple Zimi Cloud Connect devices.

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



## Data updates

The integration is pushed updates from the Zimi Cloud Controller instantly via the Zimi API.

## Known limitations

1. Updating the names of entities in the Zimi app after integration requires a HA restart to register the new names


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

Due to the authorization lifecycle of the Zimi Cloud Controller, when too many authorization requests are sent in a short period of time the device may
be unable to be connected to. If you are encountering authorization issues, remove the integration, wait a short period, then try again.

To do this:

1. Remove the integration from **Settings** > **Devices & Services** > **Zimi**
2. Wait for approximately 5 minutes
3. Try adding the integration again