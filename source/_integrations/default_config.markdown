---
title: Default Config
description: The default configuration integration will initiate a default configuration for Home Assistant.
ha_category:
  - Other
ha_release: 0.88
ha_domain: default_config
ha_quality_scale: internal
ha_codeowners:
  - '@home-assistant/core'
ha_integration_type: system
---

This {% term integration %} is a meta-component and configures a default set of integrations for Home Assistant to load. The integrations that will be loaded are:

- [Automation](/integrations/automation/) (`automation`)
- [Assist pipeline](/integrations/assist_pipeline/) (`assist_pipeline`)
- [Backup](/integrations/backup/) (`backup`)
- [Bluetooth](/integrations/bluetooth/) (`bluetooth`)
- [Configuration](/integrations/config/) (`config`)
- [Conversation](/integrations/conversation/) (`conversation`)
- [Counter](/integrations/counter/) (`counter`)
- [DHCP discovery](/integrations/dhcp/) (`dhcp`)
- [Energy](/integrations/energy/) (`energy`)
- [Frontend](/integrations/frontend/) (`frontend`)
- [Hardware](/integrations/hardware/) (`hardware`)
- [History](/integrations/history/) (`history`)
- [Home Assistant Alerts](/integrations/homeassistant_alerts) (`homeassistant_alerts`)
- [Home Assistant Cloud](/integrations/cloud/) (`cloud`)
- [Image upload](/integrations/image_upload/) (`image_upload`)
- [Input boolean](/integrations/input_boolean/) (`input_boolean`)
- [Input button](/integrations/input_button/) (`input_button`)
- [Input datetime](/integrations/input_datetime/) (`input_datetime`)
- [Input number](/integrations/input_number/) (`input_number`)
- [Input select](/integrations/input_select/) (`input_select`)
- [Input text](/integrations/input_text/) (`input_text`)
- [Logbook](/integrations/logbook/) (`logbook`)
- [Logger](/integrations/logger/) (`logger`)
- [Map](/integrations/map/) (`map`)
- [Media source](/integrations/media_source/) (`media_source`)
- [Mobile app support](/integrations/mobile_app/) (`mobile_app`)
- [My Home Assistant](/integrations/my/) (`my`)
- [Network](/integrations/network/) (`network`)
- [Person](/integrations/person/) (`person`)
- [Schedule](/integrations/schedule/) (`schedule`)
- [Scene](/integrations/scene/) (`scene`)
- [Scripts](/integrations/script/) (`script`)
- [Simple Service Discovery Protocol (SSDP)](/integrations/ssdp/) (`ssdp`)
- [Stream](/integrations/stream/) (`stream`)
- [Sun](/integrations/sun/) (`sun`)
- [System health](/integrations/system_health/) (`system_health`)
- [Tag](/integrations/tag/) (`tag`)
- [Timer](/integrations/timer/) (`timer`)
- [USB](/integrations/usb/) (`usb`)
- [Webhooks](/integrations/webhook) (`webhook`)
- [Zero-configuration networking (zeroconf)](/integrations/zeroconf/) (`zeroconf`)
- [Zone](/integrations/zone/) (`zone`)

## Configuration

To integrate this into Home Assistant, add the following section to your `configuration.yaml` file:

```yaml
# Example configuration.yaml entry
default_config:
```
