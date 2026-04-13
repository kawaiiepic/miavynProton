# miavynProton

A modified version of [GE-Proton](https://github.com/GloriousEggroll/proton-ge-custom) that automatically runs [wine-discord-ipc-bridge](https://github.com/0e4ef622/wine-discord-ipc-bridge) alongside every game, enabling seamless Discord Rich Presence support out of the box.

## What is this?

By default, Discord Rich Presence doesn't work for most games running through Proton/Wine on Linux, because the IPC socket Discord uses isn't bridged into the Wine environment. miavynProton fixes this by patching the Proton launch script to automatically start `wine-discord-ipc-bridge` whenever you launch a game — no per-game setup required.

## Features

- Based on GE-Proton (includes all its patches, fixes, and media codec support)
- Automatically starts `wine-discord-ipc-bridge` on game launch
- Discord Rich Presence works for **every** game without any manual configuration
- Drop-in replacement for GE-Proton in Steam

## Requirements

- Linux
- Steam
- Discord (running before launching a game)
- `wine-discord-ipc-bridge` installed on your system

## Installation

1. Clone the repository into your Steam compatibility tools folder:
   ```bash
   mkdir -p ~/.local/share/Steam/compatibilitytools.d
   git clone https://github.com/kawaiiepic/miavynProton ~/.local/share/Steam/compatibilitytools.d/miavynProton
   ```

2. Restart Steam.

4. In Steam, right-click a game → **Properties** → **Compatibility** → check **"Force the use of a specific Steam Play compatibility tool"** → select **miavynProton**.

## Usage

Just launch your game as normal. As long as Discord is open, Rich Presence will work automatically — no extra steps needed.

## How it works

The Proton launch script (`proton`) is modified to spawn `wine-discord-ipc-bridge` in the background before the game starts. This bridges Discord's Unix socket into the Wine/Proton environment, allowing games to communicate with your running Discord client.

## Based on

- [GE-Proton](https://github.com/GloriousEggroll/proton-ge-custom) by GloriousEggroll
- [wine-discord-ipc-bridge](https://github.com/0e4ef622/wine-discord-ipc-bridge)

## License

Follows the same licensing as GE-Proton. See [LICENSE](LICENSE) for details.
