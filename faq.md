order: 4
description: Frequently asked questions about the Aureli Wiki
keywords: docs, desktop, equora, quickshell, hyprland, faq, aureli, setup, linux
author: enviction
image: ./assets/aureli.svg
title: FAQ
summary: Frequently asked questions about the Aureli Wiki

/// tab | `Starting Errors`
/// details | I don't know the issue
If you can't pinpoint/see the error you can run `au run --dev` to get the full error message or alternatively run `au log`, then open a issue on [Github](https://github.com/eq-desktop/eqsh/issues) or ask in our [Discord](https://discord.gg/wvTS6jPkJc)
///
/// details | Missing Quickshell Polkit
This issue can be caused by using an outdated version of Quickshell. Please make sure you have the latest version installed, which can be installed with the `quickshell-git` package.
///
/// details | Aureli won't start at all
Make sure Quickshell is installed and accessible in your `$PATH`. Try running `quickshell --version` to verify. If it's missing, follow the install guide for your distro.
///
/// details | Black screen after starting
This is usually caused by a missing or misconfigured Hyprland setup. Make sure you're running Aureli inside a Hyprland session. Also check that your `hyprland.conf` does not have conflicting `exec-once` entries for other bars or shells.
///
/// details | Aureli crashes on startup with a QML error
This typically means a component file is corrupted or a submodule wasn't initialized. Run:
```bash
git submodule update --init --recursive
```
inside the Aureli directory to fix missing submodules.
///
/// details | "au: command not found" after installation
The `au` binary may not be in your `$PATH`. Try running:
```bash
export PATH="$PATH:/usr/local/bin"
```
or add it permanently to your shell config (`~/.bashrc`, `~/.zshrc`, etc.).
///
/// details | Aureli starts but nothing appears on screen
Make sure your monitors are detected by Hyprland. Check `hyprctl monitors` to confirm. Another possibility is that your `hyprland.conf` does not launch Aureli, check if you are missing `/usr/local/bin/au run` in your `exec-once` section.
///
/// details | Polkit agent fails to start
Install the Quickshell polkit agent and make sure no other polkit agent (like `gnome-polkit` or `lxpolkit`) is running at the same time, as they can conflict.
///
///

/// tab | `Installation`
/// details | How do I install Aureli?
The easiest way is via the install script:
```bash
curl -fsSL https://eqsh-wiki.github.io/get | bash
au run
```
For a manual install, see the [Install Guide](https://eqsh-wiki.github.io/install).
///
/// details | Which distros are supported?
Aureli works on any distro that can run Hyprland and Quickshell. Arch Linux is the most tested and recommended. NixOS, Fedora, and Guix are also supported via their respective Quickshell packages.
///
/// details | Do I need to install anything before Aureli?
Yes — you need [Hyprland](https://hypr.land) and [Quickshell](https://quickshell.org) installed first. Optionally, install the recommended icon and GTK themes for the full look.
///
/// details | How do I install the default wallpapers?
```bash
git clone https://github.com/eq-desktop/wallpapers.git ~/.local/share/equora/wallpapers
```
///
/// details | How do I update Aureli?
Simply run:
```bash
au update aureli
```
Then restart with `au restart`.
///
/// details | Can I install Aureli without Git?
Git is required for the manual install and updates. The curl install script handles everything for you, but Git is still used under the hood.
///
/// details | Where is Aureli installed?
By default, Aureli is installed to `~/.local/share/equora/eqsh/`.
///
/// details | How do I uninstall Aureli?
Remove the install directory and the `au` binary:
```bash
rm -rf ~/.local/share/equora/eqsh
sudo rm /usr/local/bin/au
```
///
///

/// tab | `Settings`
/// details | How to change the Wallpaper(s)?
You can change your Wallpaper inside the [system settings]^[`CTRL+Super+R` or run `au settings`] under the wallpaper section
///
/// details | Can I use my own wallpaper folder?
Yes! You can change the wallpaper folder using `au set wallpaper.folder /home/yourName/wallpapers`
///
/// details | How do I set the wallpaper using the terminal?
By running `au set wallpaper.path /home/yourName/wallpapers`
To get your current one run `au get wallpaper.path`
///
/// details | I installed the default wallpapers, where are they located?
The default wallpapers are located at `~/.local/share/equora/wallpapers/`
///
/// details | How do I open the settings app?
Press `CTRL+Super+R` or run `au settings` from a terminal.
///
/// details | Where is the settings file stored?
The user settings file is stored as JSON at `~/.config/aureli/config.json`. You can edit it manually or use `au set` and `au get` from the terminal.
///
/// details | How do I reset settings to default?
You can do that by using the cli:
```bash
au reset [setting e.g. wallpaper.folder]
au restart # Very important
```
///
/// details | How do I change the accent color?
Open the Settings app (`CTRL+Super+R`) and navigate to the Appearance section, where you can pick a custom accent color.
///
/// details | Can I disable the dock?
Yes, open Settings > Dock and toggle it off, or run:
```bash
au set dock.enabled false
```
///
/// details | Can I move the panel to the bottom?
As of now we don't support that. :(
///
///

/// tab | `Features`
/// details | How do I open the App Drawer / Launchpad?
You can open the Launchpad from the cli `au launchpad` or by pressing the configured keybind (default: `CTRL+Super+P`).
///
/// details | How do I use the Sigrid AI Chatbot?
Click the Sigrid icon in the panel to open the AI chatbot panel. Sigrid uses a local or configured AI backend to answer questions directly from your desktop.
///
/// details | How do I take a screenshot?
Use the built-in screenshot tool via the keybind `Super+Shift+5`, or use the cli `au msg screenshot open`.
///
/// details | How do I use Desktop Widgets?
Open the Widget Picker from the desktop and drag widgets onto your desktop. Widgets can be repositioned and resized freely.
///
/// details | How do I manage notifications?
Notifications appear as popups and are collected in the notification center. Click the date and time to view the center.
///
/// details | What is the notch?
The notch is a macOS-inspired interactive element at the top center of your screen. It houses quick controls, app shortcuts, media info, and more. Click or hover it to expand.
///
/// details | How do I use IPC popups?
Aureli exposes an IPC interface for launching popups from scripts or other apps. go to [Development > Popup](/development/popup).
///
/// details | Does Aureli support multiple monitors?
Yes. Aureli renders the panel and notch on each connected monitor.
///
/// details | How do I configure the System Tray?
The system tray lives in the panel and auto-discovers tray icons from running apps via the StatusNotifierItem protocol. No manual configuration is needed.
///
///

/// tab | `Plugins & Kavo`
/// details | What is Kavo?
Kavo (`.kvo`) is the declarative, hierarchical format used for Aureli plugins. It lets you define components, properties, event handlers, and widgets in a human-readable structure.
///
/// details | Where do I put my plugins?
Place your `.kvo` plugin files in `~/.config/aureli/plugins/`. Aureli will detect and load them on the next restart.
///
/// details | How do I write a basic plugin?
A minimal plugin defines a metadata section and at least one widget or event handler in Kavo format. See the [Plugin documentation](https://eqsh-wiki.github.io/plugins/plugin) for more.
///
/// details | Can plugins access system information?
Yes. Plugins can use built-in Kavo functions and event hooks to read system state such as battery level, network status, and running processes.
///
/// details | How do I reload plugins without restarting?
Run `au plugin reload` to hot-reload plugins without a full restart. Note that some plugin types may still require a full restart.
///
/// details | Can I share plugins with others?
Yes — plugins are self-contained `.kvo` files. You can share them directly or publish them to the community repository.
///
///

/// tab | `Theming`
/// details | What icon theme is recommended?
[MacTahoe Icon Theme](https://github.com/vinceliuice/MacTahoe-icon-theme) is the recommended icon theme for the full Apple-inspired look.
///
/// details | What GTK theme is recommended?
[MacTahoe GTK Theme](https://github.com/vinceliuice/MacTahoe-gtk-theme) pairs perfectly with Aureli's visual style.
///
/// details | How do I apply a GTK theme?
You can set the GTK theme using `gsettings`:
```bash
gsettings set org.gnome.desktop.interface gtk-theme "MacTahoe"
```
///
/// details | Does Aureli support light mode?
Yes. Toggle between light and dark mode in Settings > Appearance, or run:
```bash
au set general.darkMode false
```
///
///

/// tab | `Keybinds`
/// details | What are the default keybinds?
Some common defaults:  

- `CTRL+Super+R` — Open Settings  
- `CTRL+Super+P` — Open App Drawer  
- `CTRL+Super+Q` — Lock screen  
- `Super+Shift+5` — Screenshot tool  

///
/// details | How do I change keybinds?
Edit the relevant entry in `~/.config/hypr/Keys/customkeys.conf`.
///
/// details | How do I lock the screen?
Press `CTRL+Super+Q` or run `au lock` from the terminal.
///
///

/// tab | `General`
/// details | What is Aureli?
Aureli is a next-generation desktop shell for Hyprland — providing a panel, notch, lockscreen, wallpaper engine, app drawer, notifications, widgets, AI chatbot, and more, all in one polished package.
///
/// details | Is Aureli free and open source?
Yes. Aureli is released under the Apache 2.0 License. You are free to use, modify, and distribute it as long as changes remain open source.
///
/// details | What is Quickshell?
[Quickshell](https://quickshell.org) is the QML-based shell toolkit that Aureli is built on top of. It handles rendering and IPC.
///
/// details | Is Aureli affiliated with Apple?
No. Aureli is an independent open-source project. The Apple-inspired aesthetic is a design choice only — there is no affiliation with Apple Inc.
///
/// details | Where can I get help?
- Open an issue on [GitHub](https://github.com/eq-desktop/eqsh/issues)
- Join the [Discord](https://discord.gg/wvTS6jPkJc)
- Read the [Wiki](https://eqsh-wiki.github.io/)
///
/// details | How do I contribute?
Fork the repository, make your changes, and open a pull request on [GitHub](https://github.com/eq-desktop/eqsh). Contributions of all kinds — code, docs, themes, plugins — are welcome.
///
/// details | Does Aureli work on Wayland only?
Yes. Aureli is built specifically for Hyprland, which is a Wayland compositor. X11 is not supported.
///
/// details | Will Aureli ever support other compositors?
Yes. We already support Hyprland and Niri, but some features are not yet supported in Niri.
///
///