# Homekit Infused

## Framework Content
- [Introduction](index.md)
- [Framework Documentation](framework.md)
- [Updates](updates.md)
- [Issues & Questions](issues.md)
- [About Me](about.md)
- [Thanks](thanks.md)

## Addons Content
- [Addons Documentation](addons.md)
- [Addon List](https://github.com/jimz011/homekit-infused/blob/master/docs/addon_list.md)

# Homekit Infused Framework
This is the Homekit Infused 3.x.x framework, this is only the framework and will contain unfilled views. The framework contains a set of predefined (empty) views, a beautiful header with embedded alarm management, sensor event monitoring, a greeting and notifications. It also contains a navigation button so that you can easily navigate through the menu's. The Homekit Infused Framework can run standalone, the views can be setup manually.

For the entire Homekit Infused Package you will need to install this first! This is the base of Homekit Infused, without it none of the addons will work.
After the installation of the framework you can go on to install the addons (or create your own cards), the addons will decide the looks and layout of your installation.
All the cards that were previously included in HKI will be available separately on the addons page (warning! at this time not all cards have been converted)

### General Preparation
##### Advice
- Install Home Assistant or create a backup of your current setup. I will advise you to install this on a clean Home Assistant install, though it is not a requirement.
- Add all your known devices to Home Assistant (if integrations are available the prefered way would be to use that instead of putting it in manually.
- Create person entities in the UI go to configuration>persons and create all the persons in your house. Add the device_trackers you have to the person entities.
- Obviously download this project, you can grab the latest release from [here](https://github.com/jimz011/homekit-infused/releases)

##### Requirements
- Create a secrets.yaml file in the root of your HA installation if you do not have it already. Add the following line on any line within that file `alarm_code: 123456`. You can change the code to whatever number you want. DO NOT SKIP THIS PART or HKI will fail to start.
- Install HACS https://hacs.xyz/docs/installation/manual

### HACS
Below is a list of all the addons required to run the framework, you can install all of them through HACS

| Name | Type  | Description |
|----------------------------------|-------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Auto Entities](https://github.com/thomasloven/lovelace-auto-entities) | Frontend | This mod will help with auto filling entities and such |
| [Card Mod](https://github.com/thomasloven/lovelace-card-mod) | Frontend | This mod allows for custom css on any card |
| [Button Card](https://github.com/custom-cards/button-card) | Frontend | This is the button used throughout the entire setup |
| [State Switch](https://github.com/thomasloven/lovelace-state-switch) | Frontend | This is used to make cards appear based on certain conditions, like a conditional-card but better |
| [Mini Graph Card](https://github.com/kalkih/mini-graph-card) | Frontend | Mini Graph Card gives the possibility to create more advanced graphs! |
| [Card Tools](https://github.com/thomasloven/lovelace-card-tools) | Frontend | This is needed for various custom cards to run |
| [Swipe Card](https://github.com/bramkragten/swipe-card) | Frontend | This card is needed for the scrolling notifications, but also for most popups |
| [Browser Mod](https://github.com/thomasloven/hass-browser_mod) | Integration | Browser-mod makes the browser more useful and gives us the opportunity to show/create custom popups and many more! |
| [Lovelace Gen](https://github.com/thomasloven/hass-lovelace_gen) | Integration | This is the MOST important piece of the setup, without this HKI will not work! Don't add this to your `configuration.yaml` file as the included package already does so for you, if you already have `lovelace_gen:` in your `configuration.yaml` please remove or comment that line! |
| [Kiosk Mode](https://github.com/maykar/kiosk-mode) | Frontend | This mod brings back basic functionally from the deprecated custom_header addon. This will hide the header without the need of resorting to hardcoding it inside of the themes with card-mod and makes for a better experience when used in conjunction with other dashboards. |

*Note: Do NOT install layout-card, install the one packaged with HKI!!!! 

### Adding Resources
Resources MUST be added manually which can be done within the Home Assistant configuration panel. Go to the Sidebar > Configuration > Lovelace Dashboards > Resources and add all of the following resources one by one. This makes it possible to use custom resources whenever you might need them and also makes sure you can still use the Home Assistant dashboard you have already created with the UI editor.

NOTE: If you do NOT see a resources tab, please open the sidebar > profile > enable advanced mode. This should make the tab appear.

Add the following resources, nowadays HACS can add resources for you don't add them if they are already in the list, to make it easier on you, I have compiled a list with all used resources that you can easily copy and enter.

```
/hacsfiles/lovelace-auto-entities/auto-entities.js
/hacsfiles/button-card/button-card.js
/hacsfiles/lovelace-card-mod/card-mod.js
/hacsfiles/lovelace-card-tools/card-tools.js
/hacsfiles/lovelace-layout-card/layout-card.js
/hacsfiles/swipe-card/swipe-card.js
/hacsfiles/lovelace-state-switch/state-switch.js
/hacsfiles/mini-graph-card/mini-graph-card-bundle.js
/hacsfiles/kiosk-mode/kiosk-mode.js
``` 

*Note: notice that layout-card was not installed through HACS, layout-card is included in the release and should not be downloaded from HACS, though you must add this to your resources!

### Installation
Copy the following files/folders to the root of your Home Assistant installation

- Copy the `/homekit-infused/` folder to the root of your setup
- Copy the `/themes/` folder to the root of your setup
- Copy the `homekit-infused.yaml` file to the root of your setup
- Copy the `/packages/` folder to the root of your setup
- Copy the `/www/` folder to the root of your setup
- Add the following lines to your `configuration.yaml` file

```
homeassistant:
    packages: !include_dir_named packages/
    
lovelace:
    mode: storage
```

Note: If you have an existing setup and already have packages, you must cut/paste the packages/homekit_infused folder inside your currently exising packages folder! (depending on the way the folder is included within your configuration.yaml file)

The copying process should now be completed and we can move on to the configuration part.

### Configuring
There isn't much to configure from here on out, however you do need to setup a few things.
Go to the menu > hki settings and change the theme to your liking, also set the frontpage welcome message!.

To change names and icons that are shown in the header, please open the `/homekit-infused/user/config/header_config.yaml` file and change any setting you like. You will also need to set your alarm_entity inside of this file.

To make the header sensors work (the three icons on the upper right side), you MUST fill in the `/homekit-infused/user/device_counters.yaml` file!

To create notifications you can open the `/homekit-infused/user/notifications.yaml` file, there are some included examples.

You can change the theme settings by going to the `/themes/` folder, it has a little configuration piece at the top of the file where you can change the border-radius and/or some basic colors and/or font-type/family/size.

### Addons
Addons are the cards to fill the framework with, you are not required to install any of the addons if you don't want to. You can always create your own cards in the exact same way addons work. Please read the addons section of the documentation on how to install or create addons yourself.

If you have created an addon and would like to include this on this repo, you can simply clone the repo to your git, create the documentation (you can copy the format from the existing addons) and then do a merge request. This will get your addon included on this site, you can also push fixes to existing addons if you want (they will be reviewed before merging). Alternatively you can send your documenation and a screenshot of the addon over discord and I will add it to the repo.

### Views
The HKI Framework comes with a preset amount of views that can be manipulated in any way you want (you can even change the names of the views if you so please). Note that the code does NOT allow for path name changes (e.g. you've renamed the lights view to anything else, the path will always remain /lights). The path is only visible in a browser and never in the HA App, so even if you'd rename a view you will most probably not notice it. 

To know which views are available you can simply open the `homekit-infused/user/views/` folder, every view has its own folder and these are the views you can refer to if you need to (the folder name is also the path name, which will make creating navigation buttons easier, if you don't want to use the included menu).

### Extra Information
- Create/edit a `customize.yaml` file, this file is automatically created whenever you edit an entity through the UI configuration>customize. However you can create this file yourself if you don't have it already. Just put the file at the root of your config, you can also download the example customize.yaml file instead.
You might need the following entry in your `configuration.yaml` file

```
homeassistant:
    customize: !include customize.yaml
```

Now if you have created this file we will start and fill it with our own entities.
If you already have items in that file just add them below the last item, else just start typing exactly as in the example below. You do NOT need to do all of your entities. Just do the ones that are going to get shown in the frontend (e.g. lights, switches, sensors, binary_sensors and your vacuum).

```
switch.washingmachine:
    friendly_name: Washing Machine
    icon: mdi:washing-machine
```

NOTE: The customize.yaml file is the only way that you can change the names/icons for buttons that use HKI autofill addons. If you do not intend to use any of the HKI addons and just the framework you can skip doing this, however you will not be able to use any of the features besides the HKI framework itself.

## That's it! You have succesfully installed the Homekit Infused Framework.
To continue on with the addon documentation [click here](addons.md)
