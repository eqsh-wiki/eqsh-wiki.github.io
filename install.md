order: 3
description: Installing eqSh, the Quickshell-based shell for Hyprland
keywords: docs, eqsh, desktop, linux, equora, quickshell, hyprland, install
author: enviction
image: ./assets/eqsh.svg
summary: Installing eqSh has never been easier


You can install eqSh using the [eqSh CLI](https://github.com/eq-desktop/cli).

!!! info "Pre-requisites"
    Don't forget to have python and [Quickshell](https://quickshell.org/docs/v0.2.1/guide/install-setup/) installed on your system.

/// tab | Curl Installation
```bash
$ curl -fsSL https://eqsh-wiki.github.io/get | bash
```
---
///
/// tab | Manual Installation
```bash
$ git clone https://github.com/eq-desktop/cli.git
$ cd cli/
$ ./install.sh
```
Then run the install command:

```bash
$ au install
```
---
///

Afterward, you can launch eqSh using the `au run` command.

Now there's also some other things you can install:

!!! box ""
    - [MacTahoe Icon Theme](https://github.com/vinceliuice/MacTahoe-icon-theme)
    - [MacTahoe GTK Theme](https://github.com/vinceliuice/MacTahoe-gtk-theme)

And some compositor specific ones:

/// tab | Hyprland

- [Hyprland Config](https://github.com/eq-desktop/hyprland-config)
- [Liquid-Glass Plugin](https://github.com/eq-desktop/hyprliquidglass-plugin)
- [Dynamic Cursor Plugin](https://github.com/VirtCode/hypr-dynamic-cursors)
---
///