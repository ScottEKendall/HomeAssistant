## Snapmaker U1 Dashboard ##

When I had my Bambu A1 Mini printer, someone had a Home Assistant plugin that showed all kinds of status information about my printer.  Since then, I have upgraded to the Snapmaker U1 printer and I was longing for a good HA plugin, that would give me (almost) the same information that my Bambu did.

![Desktop Screen](./Desktop%20–%20Home%20Assistant.png)

![Mobile Screen](./iPhone%20View%20–%20Home%20Assistant.png)

### Required Items ###

Home Assistant: <https://www.home-assistant.io>

HACS: https://www.hacs.xyz

Moonraker HACS plugin: <https://github.com/marcolivierarsenault/moonraker-home-assistant>

mushroom plugin: <https://github.com/piitaya/lovelace-mushroom>

### Optional ###

> Warning: Installing custom firmware may void warranty and could potentially damage your device. Use at your own risk.
    
If you want to mod your firmware for high resolution RTSP camera feeds you will need the following:

Snapmaker Extended Firmware mod: https://github.com/paxx12/SnapmakerU1-Extended-Firmware

Advanced Camera Card: https://github.com/dermotduffy/advanced-camera-card


### Installation Steps ###

1.  Make sure HA is installed and up and running
2.  If you haven't already installed HACS, you will need that installed prior to doing this
3.  Go into HACS and search & install the following:

    a.  "Moonraker"

    b.  "Mushroom"

    c.  (Optional). "Advanced camera card"

    
4.  You will probably have to restart HA after you install these addons
5.  Go into Settings > Devices & Services and click on "Add integration in the lower right corner"
6.  Search for moonraker and install it (following the instructions for the addon).  _NOTE: Your printer does NOT have to be in local LAN mode, it will work either way_
7. Once Moonraker is installed, you should see:
![](./Moonraker%20Integration.png)
Click on the device it should show all of the Klipper integration settings:
![](Moonraker%20Settings.png)

### Creating a dashboard ###

1.  From the moonraker plugin, scroll to the very bottom of the settings card and click on "Add to dashboard" and choose what type of card you want the information to be displayed in.
2. After the card is added with all of the info, you can edit the dashboard and remove/edit items that you don't want to use

### Camera Feed ###

If you did not choose the optioal firmware update, you can choose the "Case" feed for the camera feed

If you DID choose to install the optional firmware, your camera feed will be in the "advanced camera card"

My YAML code is as follows to setup my card:

```
type: custom:advanced-camera-card
cameras:
  - camera_entity: camera.robinson3d_case
profiles:
  - casting
view:
  default: live
menu:
  style: hover
  position: left
  alignment: left
status_bar:
  style: hover-card
dimensions:
  aspect_ratio_mode: dynamic
  height: "500"
```
