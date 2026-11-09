# Installation and server

[Русский](installation.md)

## Install

You need **GTA V Legacy 1.0.3889** on Windows. Enhanced is not supported. RageCoop is included in the download.

1. Start Story Mode once and close GTA. Turn off BattlEye for Story Mode in the Rockstar Games Launcher, or use the official `-nobattleye` launch option on Steam or Epic ([Rockstar's guide](https://support.rockstargames.com/articles/1nenwhZlVrJY6CTFeSS2Fx/grand-theft-auto-online-battleye-faq)).
2. Download `OGCoop-Addon.zip`, extract it (right-click, Extract All) and run **Install.exe**. If Windows says "Windows protected your PC", click More info, then Run anyway.
3. The installer finds the game, checks its version, puts everything next to `GTA5.exe` and checks Visual C++ and .NET Framework 4.8. If it cannot find the game, drag `GTA5.exe` into its window. When it asks for ScriptHookV, click Download on [its author's page](https://www.dev-c.com/gtav/scripthookv/) and leave the ZIP in Downloads.
4. Start GTA, open Story Mode, press **F9** and enter the host's address. Press **J** for the menu.

**Updating:** the required steps depend on your previous version. Follow the [update section](#updates); Install.exe replaces only changed files and keeps your settings.

On VK Play, do all of this inside the cloud PC, on its persistent game drive. If the installer cannot run there, copy everything from the `client` folder next to `GTA5.exe`, together with `ScriptHookV.dll` and `dinput8.dll` from ScriptHookV. Updating from Coop Control (v0.3.x)? Delete `scripts\CoopControl.EarlyClient.dll` in the game folder and `Resources\Client\CoopControl` in the server folder, otherwise two menus load.

## Host a server

1. Extract `OGCoop-Addon.zip` and put its `server` folder anywhere you can write to. GTA is not needed on that PC.
2. Windows: double-click **Start server**, .NET is included. Linux or macOS: run `sh start-server.sh` with the x64 [.NET 10 Runtime](https://dotnet.microsoft.com/en-us/download/dotnet/10.0) installed. On a Mac with Apple silicon take the macOS x64 installer: it needs Rosetta, and the script finds it on its own.
3. The first start creates `Settings.xml` and listens on UDP **4499**. The window shows the addresses to give friends, see [connecting players](#connecting-players). The server is not listed publicly. Play with people you trust: everyone connected can use the shared tools.
4. To stop it, use **Stop server**, `sh stop-server.sh` or Ctrl+C in its window. Garages, characters, yachts and homes are saved on every change.

**Updating the server:** stop it and copy the new `server` folder over the old one. `Settings.xml` and player data stay. Use the RageCoop **1.5.12.15** files from this release: another nightly with the same number is not necessarily compatible.

### Connecting players

| Where the friend plays | What the host does | Address the friend enters |
| --- | --- | --- |
| On the server PC | Nothing | `127.0.0.1:4499` |
| On the same home network | Nothing | The server PC's local address, e.g. `192.168.1.20:4499` |
| Elsewhere, the host has a public IP | Forwards UDP 4499 on the router | The host's public address, e.g. `203.0.113.5:4499` |
| Elsewhere, no public IP | Sets up a virtual network or a tunnel | The address that app shows |

### Internet connections

**Does the host have a public IP?** Compare the "Internet" or "WAN" address on the router's status page with the one any "what is my IP" site shows. If they match, the IP is public. If the router shows `100.64.x.x` to `100.127.x.x`, `10.x.x.x` or `192.168.x.x`, the provider shares one address between customers (CGNAT) and port forwarding will not work.

**Port forwarding.** In the router settings, forward UDP 4499 to the server PC's local address, port 4499. Give that PC a fixed local address (DHCP reservation) and allow UDP 4499 in its firewall. A VPN that sends all of the host's traffic through itself can block incoming players: exclude the server or turn the VPN off.

**Virtual network.** Everyone installs the same app and joins one network, then the friend enters the server's address in that network with `:4499`. [Tailscale](https://tailscale.com/) and [ZeroTier](https://www.zerotier.com/) work on Windows, macOS and Linux. [Radmin VPN](https://www.radmin-vpn.com/) is free and popular, but Windows only.

**Tunnel.** A service such as [playit.gg](https://playit.gg/) runs a small agent on the server PC and gives a public address for local UDP port 4499, so friends install nothing. Handy when a friend plays on a cloud PC. Free plans change over time, and the extra hop can add a little delay.



## Updates

The installer and server announce newer versions: the host sees a notice in the server window, and each joining player receives a chat line. `OG_COOP_UPDATE_CHECK=0` disables server checks. For release emails, use GitHub **Watch > Custom > Releases**.

The host first stops the server, copies the new `server` folder over the old one and starts it again, preserving `Settings.xml` and player data. From v0.4.2 to v0.4.3, players need no installation: the menu updates on their next join. Use the latest Install.exe for a new installation or migration from v0.3.x. Remove the old Coop Control files manually as described above; an old-format menu settings file starts with defaults.

## Optional components

**ReShade.** [ReShade](https://reshade.me) makes the picture a little brighter and sharper, on your screen only. Skip it on a weak PC. Run its setup, choose `GTA5.exe` and DirectX 10/11/12, and when it asks for a preset, pick `OGCoop.ini` from the `reshade` folder of the download. Home opens the ReShade menu in game. In multiplayer ReShade turns off depth-based effects itself, so the preset uses only colour and sharpness.

**Add-on cars.** Each player installs add-on car models separately, and everyone needs the same files. Spawn one by its model name: Transport > Enter spawn code. The models and their authors' permissions are not covered by this project's MIT licence.

## Report a problem

[Open an issue](https://github.com/vkupyansky/og-coop/issues/new/choose) and choose "Ошибка / Problem". Describe your steps and the result, then attach reviewed logs: `install-log.txt` next to Install.exe, `scripts/RageCoop/Data/RageCoop.Client.log` in the GTA folder, or text from the server window. Remove private information before sending. Questions and ideas: Telegram [@skibidessa](https://t.me/skibidessa).
