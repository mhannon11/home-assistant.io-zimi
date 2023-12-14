---
title: "Assist - custom sentences"
---

You may add your own sentences to the intent recognizer by either extending an [existing intent](https://developers.home-assistant.io/docs/intent_builtin/) or creating a new one. You may also [customize responses](#customizing-responses) for existing intents.

## Adding a custom sentence to trigger an automation

This is the easiest method to get started with custom sentences for automations.

### Prerequisites

If you have not set up voice control yet, set up the hardware first. For instructions, refer to one of the following tutorials:

- [World's most private voice assistant](/voice_control/worlds-most-private-voice-assistant/): Using a classic landline phone
- [$13 voice assistant for Home Assistant](/voice_control/thirteen-usd-voice-remote/): Using a button with speaker and mic
- [Assist for Apple](/voice_control/apple/): Using your iPhone, Mac, or Apple watch
- [Assist for Android](/voice_control/android/): Using your Android phone, tablet, or a Wear OS watch

### To add a custom sentence to trigger an automation

1. Under **{% my automations title="Settings > Automations & Scenes" %}**, in the bottom right corner, select **Create automation**.
2. In the **Trigger** drop-down menu, select **Sentence**.
3. Enter one or more sentences that you would like to trigger an automation.
   - Do not use punctuation.
   - You can add multiple sentences. They will then all trigger that automation.
   ![Add a custom sentence](/images/assist/sentence_trigger_01.png)
4. To test the automation, go to **Overview** and in the top right corner, open Assist.
   - Enter one of the sentences.
5. If it did not work out, checkout the [troubleshooting](/voice_control/troubleshooting/) section.
   - One of the causes could be that the device you're targeting has not been exposed to Assist.
6. Pick up your voice control device and speak the custom sentence.
   - Your automation should now be triggered.

## Setting up custom sentences in configuration.yaml

Intents and sentences may be added in the [`conversation`](/integrations/conversation/) config in your `configuration.yaml` file:

{% raw %}

```yaml
# Example configuration.yaml
conversation:
  intents:
    HassTurnOn:
      - "activate [the] {name}"
```

{% endraw %}

This extends the default English sentences for the `HassTurnOn` intent, allowing you to say "activate the kitchen lights" as well as "turn on the kitchen lights".

New intents can also be added, with their responses and actions defined using the [`intent_script`](/integrations/intent_script/) integration:

{% raw %}

```yaml
# Example configuration.yaml
conversation:
  intents:
    YearOfVoice:
      - "how is the year of voice going"
      
intent_script:
  YearOfVoice:
    speech:
      text: "Great! We're at over 40 languages and counting."
```

{% endraw %}

Besides a text response, `intent_script` can trigger any `action` available in Home Assistant, such as calling a service or firing an event.

## Setting up sentences in the config directory

More advanced customization can be done in Home Assistant's `config` directory. YAML files in `config/custom_sentences/en`, for example, will be loaded when English sentences (language code `en`) are requested.

The following example creates a new `SetVolume` intent that changes the volume on one of two media players:

{% raw %}

```yaml
# Example config/custom_sentences/en/media.yaml
language: "en"
intents:
  SetVolume:
    data:
      - sentences:
          - "(set|change) {media_player} volume to {volume} [percent]"
          - "(set|change) [the] volume for {media_player} to {volume} [percent]"
lists:
  media_player:
    values:
      - in: "living room"
        out: "media_player.living_room"
      - in: "bedroom"
        out: "media_player.bedroom"
  volume:
    range:
      from: 0
      to: 100
```

{% endraw %}

As mentioned above, you can then use the `intent_script` integration to implement an action and provide a response for `SetVolume`:

{% raw %}

```yaml
# Example configuration.yaml
intent_script:
  SetVolume:
    action:
      service: "media_player.volume_set"
      data:
        entity_id: "{{ media_player }}"
        volume_level: "{{ volume / 100.0 }}"
    speech:
      text: "Volume changed to {{ volume }}"
```

{% endraw %}

## Customizing responses

Responses for existing intents can be customized as well in `config/custom_sentences/<language>`:

{% raw %}

```yaml
# Example config/custom_sentences/en/responses.yaml
language: "en"
responses:
  intents:
    HassTurnOn:
      default: "I have turned on the {{ slots.name }}"
```

{% endraw %}


## Related topics

- [View existing intents](https://developers.home-assistant.io/docs/intent_builtin/)
- [Create aliases](/voice_control/aliases/)
- [$13 voice assistant for Home Assistant](/voice_control/thirteen-usd-voice-remote/)
- [Assist for Apple](/voice_control/apple/)
- [Assist for Android](/voice_control/android/)