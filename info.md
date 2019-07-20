<a href="https://www.buymeacoffee.com/uMhxJCzPS" target="_blank"><img
src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png"
alt="Buy Me A Coffee" style="height: 41px !important;width: 174px
!important;box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5)
!important;-webkit-box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5)
!important;" ></a>

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
`tap_device` | True | string || The device to take the action on. Currently, only lights and light groups are supported.
`tap_colors` | True | string || If `tap_action` is `color`, this is required. Specify a comma separated list of colors to cycle through when the button is tapped.
`hold_action` | True | string || The action to take when the button is held. Can be `toggle`, `brightness`, or `color`.
`hold_device` | True | string || The device to take the action on. Currently, only lights and light groups are supported.
`hold_colors` | True | string || If `hold_action` is `color`, this is required. Specify a comma separated list of colors to cycle through when the button is held.
`double_action` | True | string || The action to take when the button is double-tapped. Can be `toggle`, `brightness`, or `color`.
`double_device` | True | string || The device to take the action on. Currently, only lights and light groups are supported.
`double_colors` | True | string || If `double_action` is `color`, this is required. Specify a comma separated list of colors to cycle through when the button is double-tapped.
