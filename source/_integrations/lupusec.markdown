---
title: Lupus Electronics LUPUSEC
description: Instructions on integrating Lupusec home security with Home Assistant.
ha_category:
  - Alarm
  - Binary sensor
  - Hub
  - Switch
ha_release: 0.83
ha_iot_class: Local Polling
ha_codeowners:
  - '@majuss'
ha_domain: lupusec
ha_platforms:
  - alarm_control_panel
  - binary_sensor
  - switch
ha_integration_type: integration
---

The `lupusec` integration allows the user to integrate their Lupusec alarm control panel and ultimately all connected sensors and other devices. For more information about the LUPUS-Electronics security system please visit their [website](https://www.lupus-electronics.de).

Supported units:

- Lupusec XT1
- Lupusec XT2 Plus

The following devices are supported by the underlying `lupupy` Python library and integrated into Home Assistant.

- **Alarm control panel**: Displays the alarm status and controls arming, disarming and home modus.
- **Binary sensor**: Displays the status of binary sensors. Door, window, water, and smoke sensors are supported.
- **Switch**: Turn off and on your Lupus power switches.

## Configuration

To use Lupusec devices in your installation, add the following `lupusec` section to your `configuration.yaml` file:

```yaml
# Example configuration.yaml entry
lupusec:
  username: YOUR_USERNAME
  password: YOUR_PASSWORD
  ip_address: YOUR_IP_ADDRESS
```

{% configuration %}
username:
  description: The login username of your Lupusec alarm panel.
  required: true
  type: string
password:
  description: The login password of your Lupusec alarm panel.
  required: true
  type: string
ip_address:
  description: The IP address of your Lupusec alarm panel.
  required: true
  type: string
name:
  description: Name for your Lupusec panel.
  required: false
  type: string
{% endconfiguration %}
