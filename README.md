# [TF2] Anti Donor Abuse
A simple plugin that prevents donors from abusing their powers while on the server. Originally made for my unusual trading server, I have decided to release it publicly.

When a player joins and does things, it checks certain conditions and prevents some actions from being taken to prevent abuse. See below for the full list of features.

This plugin will only run in TF2 due to game-specific features.

## Features
* Player cannot do damage (to buildings or players) while resized, in God mode, or in a kart
* Players cannot sap buildings while resized or in God mode
* Players cannot airblast while resized or in God mode
* Players cannot heal other players while resized or in God mode

## Configuration
The above settings can all be configured. Here is the default configuration file which is placed in `tf/cfg/sourcemod/plugin.anti_donor_abuse.cfg`. It is automatically generated on first run and does not need to be created manually.

Each configuration setting (one for each feature in [Features](#features)) is configured via a bit string. The comments explain what the different values are. Multiple "options" are configured by adding the numeric values together.

For example, to prevent damage to players while someone is in a kart or resized, the value of `ada_damage` should be set to 1 (resized) + 2 (kart) + 8 (players) which is 11.

The plugin default is to have all options enabled.

```
// Bitstring to prevent players from damaging other things
// 0=Disabled
// 1=No damage while resized
// 2=No damage while in a kart
// 4=No damage in god mode (some God mode plugins may handle this already)
// 8=Apply to players
// 16=Apply to buildings
// -
// Default: "31"
// Minimum: "0.000000"
// Maximum: "31.000000"
ada_damage "31"

// Bitstring to prevent healing
// 0=Disabled
// 1=No healing while in god mode
// 2=No healing while resized
// -
// Default: "3"
// Minimum: "0.000000"
// Maximum: "3.000000"
ada_healing "3"

// Bitstring to prevent players from using the sapper
// 0=Disabled
// 1=No sapper while resized
// 2=No sapper while god mode
// -
// Default: "3"
// Minimum: "0.000000"
// Maximum: "3.000000"
ada_sapper "3"

// Bitstring to prevent players from airblasting other players
// 0=Disabled
// 1=No airblast while resized
// 2=No airblast in god mode
// -
// Default: "3"
// Minimum: "0.000000"
// Maximum: "3.000000"
ada_airblast "3"
```

## New Features/Contributing
If there are any features that you would like to see added to the plugin, create an issue or pull request.

Follow the current code style of the plugin when making a pull request. All pull requests must be tested.

## Changelog
v2.0.0 (2023-02-24)
* Do not allow players to damage or sap buildings (thanks to Sreaper)
* No airblasting
* Improve heal check performance
* Add cvar configuration for settings

v1.1.0 (2022-02-27)
* Add feature to prevent players from healing in God mode

v1.0.1 (2021-08-08 )
* Fix issue where resized players cannot rocket jump (i.e. cannot damage themselves)

v1.0.0 (2021-03-24)
* Initial release
