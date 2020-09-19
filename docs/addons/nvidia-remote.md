# Homekit Infused

Back to [Addon List](../addon_list.md)

# Remote Control (Nvidia SHIELD TV/Android TV)
*HKI Framework 3.1.2 or higher required

![Homekit Infused](../images/remote-control.png)

### Description
This is a predefined remote control solution for your Nvidia SHIELD TV (pro). This has only been tested on a SHIELD however there is a big chance that this will work with any Android TV (e.g. Xiaomi miBox S). Please let me know if you have any of these mediaplayers and if this addon works for you.

*Note: some features might not work properly as this addon is experimental, know issue is that the mute button does not work as intended!

### Configuration
- Configurating this addon is fairly simple and only requires a few properties.

### Advanced

| Properties | Required | Default | Description |
|----------------------------------|-------------|----------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| entity_media_player | yes | none | This MUST be your Android TV entity! |
| entity_media_player_sound | yes | none | You can use this if you use a different media_player to control sound (this MUST be an entity in the media_player domain!). If you don't have a separate media_player for sound you must enter the same entity as above |
||||
| name_volume_down | no | Volume | Change the volume down name |
| label_volume_down | no | Down | Change the volume down label |
| icon_volume_down | no | mdi:volume-minus | Change the default volume down icon |
||||
| name_volume_up | no | Volume | Change the volume up name |
| label_volume_up | no | Down | Change the volume up label |
| icon_volume_up | no | mdi:volume-plus | Change the default volume up icon |
||||
| name_volume_mute | no | Volume | Change the volume mute name |
| label_volume_mute | no | Down | Change the volume mute label |
| icon_volume_mute | no | mdi:volume-mute | Change the default volume mute icon |
||||
| name_preset_button_1 | no | Youtube | Change the name of the first preset button |
| icon_preset_button_1 | no | mdi:youtube | Change the icon of the first preset button |
| icon_color_preset_button_1 | no | red | Change the icon color of the first preset button, this can also be a hex or rgb value |
| source_preset_button_1 | no | YouTube | Change the source of the first preset button, this is usually the app name (case-sensitive), if you need help finding sources check [here](https://community.home-assistant.io/t/native-support-for-android-tv-android-devices/82792/485) |
||||
| name_preset_button_2 | no | Plex | Change the name of the second preset button |
| icon_preset_button_2 | no | mdi:plex | Change the icon of the second preset button |
| icon_color_preset_button_2 | no | gold | Change the icon color of the second preset button, this can also be a hex or rgb value |
| source_preset_button_2 | no | Plex | Change the source of the second preset button, this is usually the app name (case-sensitive), if you need help finding sources check [here](https://community.home-assistant.io/t/native-support-for-android-tv-android-devices/82792/485) |
||||
| name_preset_button_3 | no | Netflix | Change the name of the third preset button |
| icon_preset_button_3 | no | mdi:netflix | Change the icon of the third preset button |
| icon_color_preset_button_3 | no | red | Change the icon color of the third preset button, this can also be a hex or rgb value |
| source_preset_button_3 | no | Netflix | Change the source of the third preset button, this is usually the app name (case-sensitive), if you need help finding sources check [here](https://community.home-assistant.io/t/native-support-for-android-tv-android-devices/82792/485) |
||||
| name_preset_button_4 | no | Spotify | Change the name of the fourth preset button |
| icon_preset_button_4 | no | mdi:spotify | Change the icon of the fourth preset button |
| icon_color_preset_button_4 | no | limegreen | Change the icon color of the fourth preset button, this can also be a hex or rgb value |
| source_preset_button_4 | no | Spotify | Change the source of the fourth preset button, this is usually the app name (case-sensitive), if you need help finding sources check [here](https://community.home-assistant.io/t/native-support-for-android-tv-android-devices/82792/485) |
||||
| grid | no | default-hki-grid | Change the grid of the button, choose from `default-hki-grid`, `light-devices-grid`, `old-hki-grid` or `old-light-devices-grid` |

### Install
- Create a new file inside the folder of the view you want (e.g. /homekit-infused/user/views/frontpage/), you can name the file however you want (e.g. frontpage-buttons.yaml)
- Copy the code below and make changes if needed

```
# example of minimal required config
- type: horizontal-stack
  cards:
    - !include ../../../base/includes/gap.yaml
    - !include
      - '../../../base/templates/other/remote-control.yaml'
      - entity_media_player: media_player.nvidia_s_h_i_e_l_d_tv_pro
        entity_media_player_sound: media_player.samsung_ue65ku6000
    - !include ../../../base/includes/gap.yaml
```
