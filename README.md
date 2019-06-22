# SmartThings Button

_An app to handle events from a SmartThings Button._

## Installation

This app is best installed using
[HACS](https://github.com/custom-components/hacs), so that you can easily track
and download updates.

Alternatively, you can download the `stbutton` directory from inside the `apps` directory here to your
local `apps` directory, then add the configuration to enable the `stbutton`
module.

## How it works

You can define an instance of the app in your apps.yaml file for every
SmartThings button that you have. See the example below for configuration for
one button. Buttons connected via ZHA or the SmartThings Hub integration are
supported, but configuration is slightly different in each case.

The app currently only works with lights, but additional domains (switches,
covers, media players) are on the roadmap, and feature requests are welcome. One
of three things are possible for each button interaction:

* Toggle: Toggles a light on/off.
* Brightness: Sets the light brightness to a pre-defined level. If the light's
  brightness is over 50%, the new brightness will be 15%; otherwise the new
  brightness will be 60%. These settings are on the roadmap to be
  user-configurable.
* Color: Cycle through a user-defined list of colors.

## App configuration

Define the app once for every button you have, giving it a unique name each time.

```yaml
stairs_button:
  module: stbutton
  class: STButton
  device_ieee: "00:00:00:00:00:00:00"
  tap_action: toggle
  tap_device: light.bar
  hold_action: brightness
  hold_device: light.bar
  double_action: color
  double_device: light.bar
  double_colors: white,blue,red,green
```

key | optional | type | default | description
-- | -- | -- | -- | --
`module` | False | string | | `stbutton`
`class` | False | string | | `STButton`
`device_ieee` | True | string || The device_ieee of the button, if using ZHA.
`button_name` | True | string || The button_name of the button, if using SmartThings integration. One of `device_ieee` or `button_name` must be present.
`tap_action` | True | string || The action to take when the button is tapped. Can be `toggle`, `brightness`, or `color`.
`tap_device` | True | string || The device to take the action on. Currently, only lights and light groups are supported.
`tap_colors` | True | string || If `tap_action` is `color`, this is required. Specify a comma separated list of colors to cycle through when the button is tapped.
`hold_action` | True | string || The action to take when the button is held. Can be `toggle`, `brightness`, or `color`.
`hold_device` | True | string || The device to take the action on. Currently, only lights and light groups are supported.
`hold_colors` | True | string || If `hold_action` is `color`, this is required. Specify a comma separated list of colors to cycle through when the button is held.
`double_action` | True | string || The action to take when the button is double-tapped. Can be `toggle`, `brightness`, or `color`.
`double_device` | True | string || The device to take the action on. Currently, only lights and light groups are supported.
`double_colors` | True | string || If `double_action` is `color`, this is required. Specify a comma separated list of colors to cycle through when the button is double-tapped.

## Issues/Feature Requests

Feel free to log any issues or feature requests. For example, if you are getting
your buttons into Home Assistant a different way (for example, via Zigbee2MQTT),
I would be happy to work with you to add support for that method to this app.