# OG Coop

GTA Online interiors, your own character, yacht, home and a menu for playing GTA V Legacy with friends through [RageCoop](https://ragecoop.com/). The installer sets up the game; the server sends the menu to joining players while keeping RageCoop's files unchanged.

[Русский](README.md) · **[Download OGCoop-Addon.zip](https://github.com/vkupyansky/og-coop/releases/latest)** · [Install](#install-and-run) · [Controls](#usage) · [Report a problem](https://github.com/vkupyansky/og-coop/issues/new/choose)

[![Release](https://img.shields.io/github/v/release/vkupyansky/og-coop?include_prereleases&label=release&color=2A9D8F)](https://github.com/vkupyansky/og-coop/releases/latest)
![GTA V Legacy 1.0.3889](https://img.shields.io/badge/GTA%20V%20Legacy-1.0.3889-F4A261)
![RageCoop 1.5.12.15](https://img.shields.io/badge/RageCoop-1.5.12.15-2A9D8F)
[![MIT](https://img.shields.io/badge/license-MIT-F4A261)](LICENSE)

![The OG Coop menu while playing with a friend](screenshots/01-main-menu.jpg)

## Features

- **Pause your own game.** Esc freezes you and hides your character from friends; resume from the same spot, even in mid-flight.
- **GTA Online interiors.** 82 interiors behind 158 street doors, each with its Online map icon: the Diamond Casino and its penthouse, apartments, houses and mansions, CEO offices, biker clubhouses, bunkers, nightclubs, the LS Car Meet and its test track, the Kortz Center halls, El Rubio's mansion on Cayo Perico and many more. Walk into the orange circle at a door to go in. The way out is a circle where you appear, however you got inside.
- **People inside**, as in GTA Online: guards, cashiers, bartenders, dancers and guests in the same spots, doing the same things. And a beach party on Cayo Perico.
- **Your character.** A creator like the one in GTA Online: heritage, face, hair, make-up, every Online outfit and tattoo. It opens the first time you join, is kept on the server under your name, and friends see you exactly as you made yourself.
- **Your yacht.** A Galaxy Super Yacht at one of 35 berths along the coast, with your choice of model, colour, railings, lights and flag. Its captain moves it to another berth.
- **Your home.** Pick a penthouse, apartment, house or mansion: you appear there when you join, and Go home brings you back from anywhere.
- **Vehicles.** Spawn any GTA vehicle and get straight behind the wheel, keep favourites and a garage of up to 64 tuned cars on the server, tune at Los Santos Customs and everyone sees the result. Repair, flip, and hold O for a boost. Installed add-on cars spawn by their model name.
- **Drive through traffic.** A shared switch that lets cars, bikes, quads and bicycles pass through NPC traffic.
- **Special places.** Cayo Perico, North Yankton, the aircraft carriers, yachts and a cargo ship, with map icons.
- **Shared world.** One waypoint, weather and time of day for everyone, and snow on the ground with tyre and foot tracks.
- **Clean free roam.** No mission markers, random events, side jobs or phone calls in the way.
- **Playing together.** Teleport to a friend or straight into a free seat in their car, hold N for voice chat, respawn next to your partner instead of at a hospital.
- **GTA Online radio stations and weapon attachments**, Mk II included.
- **Fixes for RageCoop.** Hangs, races, repeating rockets and wreck explosions, drifting name tags, a stuck microphone and more, fixed while the game runs. The full list is in [engine changes](docs/engine-changes.md).

## Screenshots

| Transport | Teleports |
| --- | --- |
| ![Transport](screenshots/02-transport.jpg) | ![Teleports](screenshots/03-teleports.jpg) |
| Partners | Character |
| ![Partners](screenshots/04-partners.jpg) | ![Character](screenshots/05-character.jpg) |
| Character creator | Weapons |
| ![Character creator](screenshots/06-appearance.jpg) | ![Weapons](screenshots/07-weapons.jpg) |

![Settings: the menu supports English and Russian](screenshots/08-settings.jpg)

## Install and run

Requires **GTA V Legacy 1.0.3889 on Windows**. Enhanced is unsupported; RageCoop **1.5.12.15** is included. The menu works with a keyboard or gamepad.

1. Start Story Mode once and close GTA. Disable BattlEye for Story Mode in Rockstar Games Launcher, or use the official `-nobattleye` option on Steam/Epic ([Rockstar's guide](https://support.rockstargames.com/articles/1nenwhZlVrJY6CTFeSS2Fx/grand-theft-auto-online-battleye-faq)).
2. Download and extract `OGCoop-Addon.zip`, then run **Install.exe**. If SmartScreen warns, use More info and Run anyway.
3. The installer checks the game, Visual C++ and .NET Framework 4.8. Drag `GTA5.exe` into the window if it cannot find GTA. When requested, download the ScriptHookV ZIP from [its author](https://www.dev-c.com/gtav/scripthookv/) and leave it in Downloads.
4. Open Story Mode in GTA, press **F9** and enter the server address. **J** opens the menu.

To host, put the archive's `server` folder somewhere writable. On Windows use **Start server** and **Stop server**. Linux/macOS use `sh start-server.sh` and `sh stop-server.sh` with the x64 [.NET 10 Runtime](https://dotnet.microsoft.com/en-us/download/dotnet/10.0). Apple silicon also needs Rosetta and the macOS x64 Runtime. GTA is not required on the server.

First launch creates `Settings.xml` and listens on UDP **4499**. On the server PC connect to `127.0.0.1:4499`; within one LAN use its local address. Remote players need UDP forwarding, a virtual network or a tunnel. See [connection, VK Play, updates and migration from Coop Control](docs/installation-en.md).

## Usage

| Action | Keyboard | Xbox |
| --- | --- | --- |
| OG Coop menu | J | Hold LB + RB, press Down |
| Repair | K | Hold LB + RB, press Up |
| Select / back | Enter / Esc | A / B |
| Navigate | Arrow keys | D-pad |
| Boost | Hold O | Hold A while driving (duck still works) |
| Voice chat | Hold N | |
| GTA pause and map | Esc | Menu / Start |

Language: Settings > Language. Each player picks their own. Esc pauses only your own game: while you are in the pause menu, your character disappears for others and the traffic your game controls stands still.

The server is not publicly listed. Shared tools are available to everyone connected, so play with people you trust. Characters, garages of up to 64 cars, yachts and homes are saved on the server on every change.

When updating, stop the server, replace its files and restart while keeping `Settings.xml` and player data. From v0.4.2 to v0.4.3, players need no installation: the menu arrives on their next join. Use the latest Install.exe for new installations; older-version differences are in the [update guide](docs/installation-en.md#updates).

## Checks

Prepare source dependencies using the [developer guide](docs/development.md), then run from the source root:

```bash
bash tools/check.sh --public-release
```

The complete check needs Windows with Git Bash, or macOS with CrossOver and .NET Framework 4.8. Screenshots do not replace testing a new gameplay session.

## Limitations

- Interiors are places to visit together. GTA Online activities inside them (casino games, business production, buying property) are not included.
- Your look changes only in the creator, J > Character > Appearance. Clothes shops, barbers, tattoo parlours and the safehouse wardrobe are closed on the server, and switching between Michael, Franklin and Trevor is off.
- The yacht comes without a helicopter, jet skis or yacht services.
- The radio station is shared, the exact song position and personal music are not.
- Parked cars, boats and planes are shared, one copy each. Shop clerks and other NPCs at fixed spots are separate for each player. See also the [known issues](docs/engine-changes.md#известные-проблемы).

## Documentation

- [Installation, hosting, updates and optional components](docs/installation-en.md).
- [Source builds and checks](docs/development.md), in Russian.
- [RageCoop changes and known issues](docs/engine-changes.md), in Russian.
- Problems: [GitHub Issues](https://github.com/vkupyansky/og-coop/issues/new/choose); questions and ideas: Telegram [@skibidessa](https://t.me/skibidessa).

## License

Our code is [MIT](LICENSE), © 2026 Vladislav Kupyansky (vkupyansky). RageCoop and other components keep the licences and credits in [THIRD_PARTY.txt](THIRD_PARTY.txt). ScriptHookV and ReShade are downloaded from their authors separately.
