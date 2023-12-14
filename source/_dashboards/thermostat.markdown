---
type: card
title: "Thermostat card"
sidebar_label: Thermostat
description: "The thermostat card gives control of your climate entity, allowing you to change the temperature and mode of the entity."
---

The thermostat card gives control of your [climate](/integrations/#climate) entity, allowing you to change the temperature and mode of the entity.

<p class='img'>
  <img src='/images/dashboards/thermostat_card.gif' alt='Screenshot of the thermostat card'>
  Screenshot of the thermostat card.
</p>

{% include dashboard/edit_dashboard.md %}

All options for this card can be configured via the user interface.

## YAML configuration

The following YAML options are available when you use YAML mode or just prefer to use YAML in the code editor in the UI.

{% configuration %}
type:
  required: true
  description: "`thermostat`"
  type: string
entity:
  required: true
  description: Entity ID of `climate` domain.
  type: string
name:
  required: false
  description: Overwrites friendly name.
  type: string
  default: Name of entity.
theme:
  required: false
  description: Override the used theme for this card with any loaded theme. For more information about themes, see the [frontend documentation](/integrations/frontend/).
  type: string
features:
  required: false
  description: Additional widgets to control your entity. See [available features](/dashboards/features). Only climate related features are supported.
  type: list
{% endconfiguration %}

### Example

```yaml
type: thermostat
entity: climate.nest
```
