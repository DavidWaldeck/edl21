# edl21
Quick Hack, adding a timeout to homeassistant's edl21 component.

Related to: https://github.com/home-assistant/core/issues/54917

Original integration: https://www.home-assistant.io/integrations/edl21

Installation:
  Add the edl21 folder to your custom_components dir.
  
Configuration:
The original integration configuration has been extended by an optional timeout parameter, which defines the timeout in ms.
If set to 0 (default), the integration should behave like the original one.

CAUTION:
When setting the timeout too low, the integration will get stuck in an infinite reconnection loop!!!
A good value for me is:

timeout: 30000

Implementation:
An extra task triggers a reconnect after no data has been received for \<timeout\>.
