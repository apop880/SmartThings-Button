# SmartThings Button
[![hacs_badge](https://img.shields.io/badge/HACS-Default-orange.svg?style=for-the-badge)](https://github.com/custom-components/hacs)
<a href="https://www.buymeacoffee.com/uMhxJCzPS" target="_blank"><img
src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png"
alt="Buy Me A Coffee" style="height: 41px !important;width: 174px
!important;box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5)
!important;-webkit-box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5)
!important;" ></a>

_An app to handle events from a SmartThings Button._

**As of version 2.0, I am only testing against AppDaemon 4.x. The app will likely continue to work with
AppDaemon 3.x, but if you have an issue and are using AppDaemon 3.x, I will not be able to provide support.**

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

The app works with lights, light groups, input_booleans, and switches.
Feature requests are welcome. One
of three things are possible for each button interaction:

* Toggle: Toggles an entity on/off. For lights, the brightness defaults to 60% and a color temperature of 2700K when turned on.
* Brightness (Lights only): Sets the light brightness to a pre-defined level. If the light's
  brightness is over 50%, the new brightness will be 15%; otherwise the new
  brightness will be 60%. These settings are on the roadmap to be
  user-configurable.
* Color (Lights only): Cycle through a user-defined list of colors.

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
`button_name` | True | string || The name of the button, if using SmartThings integration. One of `device_ieee` or `button_name` must be present.
`tap_action` | True | string || The action to take when the button is tapped. Can be `toggle`, `brightness`, or `color`.
`tap_device` | True | string || The device to take the action on. Currently, only lights, light groups, groups, switches, and input_booleans are supported.
`tap_colors` | True | string || If `tap_action` is `color`, this is required. Specify a comma separated list of colors to cycle through when the button is tapped.
`hold_action` | True | string || The action to take when the button is held. Can be `toggle`, `brightness`, or `color`.
`hold_device` | True | string || The device to take the action on. Currently, only lights, light groups, groups, switches, and input_booleans are supported.
`hold_colors` | True | string || If `hold_action` is `color`, this is required. Specify a comma separated list of colors to cycle through when the button is held.
`double_action` | True | string || The action to take when the button is double-tapped. Can be `toggle`, `brightness`, or `color`.
`double_device` | True | string || The device to take the action on. Currently, only lights, light groups, groups, switches, and input_booleans are supported.
`double_colors` | True | string || If `double_action` is `color`, this is required. Specify a comma separated list of colors to cycle through when the button is double-tapped.

## Issues/Feature Requests

Feel free to log any issues or feature requests. For example, if you are getting
your buttons into Home Assistant a different way (for example, via Zigbee2MQTT),
I would be happy to work with you to add support for that method to this app.