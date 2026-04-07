order: 2
description: Developer-focused documentation for the Aureli CLI, IPC bridge, runtime control, and configuration tooling.
keywords: docs, cli, aureli, eqsh, quickshell, hyprland, linux, ipc
author: enviction
image: ../assets/eqsh.svg
summary: Developer-focused CLI Documentation

# Command Line Interface

This page documents the **Aureli CLI tool** (`aureli`).
It acts as a **runtime controller**, **Msg bridge**, and **configuration editor** for the Aureli desktop.

The CLI is designed for:

* Developers scripting Aureli behavior
* Runtime control & debugging
* JSON config mutation
* Launching internal UI components
* Managing Aureli lifecycle
* Managing Aureli Plugins

The CLI communicates with Aureli through:

* **Quickshell execution**
* **Runtime IPC commands**
* **Direct JSON config edits**

---

## Binary

```bash
au [command] [options]
```

You can override the Aureli installation path:

```bash
au -l /custom/path run
```

Default:

```text
~/.local/share/equora/eqsh
```

---

## Runtime Paths

| Path                           | Purpose                              |
| ------------------------------ | ------------------------------------ |
| `~/.local/share/equora/eqsh`   | Aureli installation                  |
| `~/.config/aureli/config.json` | Runtime config                       |
| `~/.config/aureli/runtime`     | Running instance metadata (PID etc.) |

# Core Commands

## `run` (`r`)

Start Aureli.

```bash
au run # or au r
```

| Option  | Description                   |
| ------- | ----------------------------- |
| `--dev` | Runs in foreground (dev mode) |

Behavior:

* Prevents double launch
* Executes eqSh via Quickshell
* Detached by default

## `plugin`

| Command      | Alias      | Description                   |
| ------------- | ---------- | ----------------------------- |
| install      | i          | Install a plugin                |
| uninstall    | rm         | Uninstall a plugin              |
| list        | l          | List installed plugins          |
| meta        | m          | Get plugin meta                 |
| update      | u          | Update a plugin                |
| new        | n          | Create a new plugin              |
| load        |            | Load a plugin from a directory    |
| compile    | c          | Compile a plugin                |

```bash
au plugin [command] [options]
```

## `quit`

```bash
au quit
```

Force kills Aureli using SIGKILL.

---

## `restart`

```bash
au restart
```

Sequence:

1. Kill running instance
2. Relaunch eqSh

---

## `lock`

```bash
au lock
```

Locks the screen.

---

## `update`

```bash
au update [cli|aureli]
```

Git pulls eqSh repo.

---

## `install`

Installs Aureli from GitHub.

```bash
au install
```

## Plugin

## `install-wallpapers`

Installs the default Aureli Wallpapers.

```bash
au install-wallpapers
```

## Configuration Commands

## `set`

```bash
au set bar.height 40
```

Supports automatic type casting:

| Input        | Stored As |
| ------------ | --------- |
| `42`         | int       |
| `3.14`       | float     |
| `true/false` | bool      |
| other        | string    |

Nested paths use dot notation:

```bash
aureli set appearance.accentColor "#ff00ff"
```

Hot-reload occurs via eqSh file watchers.

## `get`

```bash
au get bar.height
```

Special:

```bash
au get all
```

Lists top-level sections.

---

## `reset`

Delete a config key.

```bash
au reset bar.height
```

Reset everything:

```bash
au reset --all
```

⚠ Requires restart.

# UI Control Commands

These toggle or spawn UI systems.

| Command               | IPC Target          |
| --------------------- | ------------------- |
| `settings`            | Settings window     |
| `launchpad`           | App grid            |
| `notification-center` | Notification center |

---

## Dialogs

Create system dialog:

```bash
au dialog <app> <icon> <title> <desc> <accept> <decline> <cmdA> <cmdD> <style>
```

Bridges to:

```text
systemDialogs.newDialog
```

---

## Notch Apps

### Create

```bash
au new-notch-app MyApp.qml "Music"
```

### Destroy

```bash
au destroy-notch-app
```

---

# Msg Bridge

## Generic Msg

```bash
au msg <command> <method> [args...]
```

Example:

```bash
au msg lock lock
```

## Show Msg Commands

```bash
au msg
```

Lists exposed IPC endpoints.