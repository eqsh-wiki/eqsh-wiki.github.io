order: 3
description: Communication with Aureli
keywords: docs, desktop, equora, quickshell, hyprland, eqsh, msg, ipc, linux
author: enviction
new: true
image: ../assets/eqsh.svg
title: Msg
sidebar_title: Msg
summary: Communication with Aureli

!!! info ""
    **Note:**
    This page is in replacement of the IPC page.

## Message Commands

You can use `au msg` to see all available commands.

If you want to send a command, use `au msg <command> <method> <args>`

!!! note "Example:"
    `au msg lock lock`

!!! info ""
    **Note:**
    Some of these commands need further explanation. At the bottom of this page, you can find information about them.

### Message Commands

| Target | Function | Description |
| --- | --- | --- |
audio | setVolume(volume) | Set the audio volume |
audio | louder() | Make the audio louder |
audio | quieter() | Make the audio quieter |
lock | lock() | Lock the screen |
lock | unlock() | Unlock the screen |
lock | isLocked() | Get the current lock state |
spotlight | toggle() | Toggle spotlight |
spotlight | set(visible) | Show or hide the spotlight |
menubar | toggle() | Toggle the menubar |
menubar | set(visible) | Show or hide the menubar |
settings | toggle() | Toggle settings |
modal | instance(appName, title, description, actionsJsonPath, iconPath, useIcon) | Create a new modal instance |
display | brighter(by) | Make the display brighter |
display | dimmer(by) | Make the display darker |
launchpad | toggle() | Toggle launchpad |
notch | instance(code) | Create a new notch instance |
notch | closeAllInstances() | Close all notch instances |
notch | activateInstance() | Activate the currently open notch instance |
notch | informInstance() | Activate the Inform Mode of the currently open notch instance |
notch | closeInstance() | Close the currently open notch instance |
music | getData() | Get the current music data |
music | previous() | Go to the previous music track |
music | togglePlay() | Toggle the music playback |
music | next() | Go to the next music track |
systemDialogs | newDialog(appName, icon_path, title, description, accept, decline, commandAccept, commandDecline, customStyle) | Create a new dialog |
controlCenter | openBluetooth() | Open the bluetooth settings |
controlCenter | close() | Close the control center |
controlCenter | openWifi() | Open the wifi settings |
controlCenter | open() | Open the control center |
ai | toggle() | Toggle ai |
ai | set(visible) | Show or hide the ai |
widgets | toggleEditMode() | Toggle edit mode for widgets |
notificationCenter | toggle() | Toggle notification center |
popup | openPopup(iconPath, app, title, description, timeout, aargs) | Open a new popup |
screenshot | screen() | Take a screenshot of the entire screen |
screenshot | open() | Open the screenshot app |
screenshot | region() | Take a screenshot of a specific region |
plugins | reload() | Reload all plugins |
doNotDisturb | toggle() | Toggle do not disturb |
doNotDisturb | disable() | Disable do not disturb |
doNotDisturb | enable() | Enable do not disturb |
wallpaper | change(path) | Change the wallpaper |

## Advanced IPC Calls

- [Modal](../01_development/modal.md)
    - Create Dialogs, yes/no questions, User Input, and more
- [Notch](../01_development/notch.md)
    - Useful information and shell extensions without distracting the user
- [Popups](../01_development/popup.md)
    - Banner and Toast Notifications that don't distract the user but still get their attention