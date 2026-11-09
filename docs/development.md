# Сборка и проверки

Распакуйте архивы исходников и дополнения. Установите .NET SDK из `work/RageCoopAdmin/global.json` (**10.0.403**). В этой папке скопируйте `References.example.props` в `References.props` и укажите в `RageCoopClientDir` папку `client/scripts/RageCoop` дополнения, в `RageCoopServerDir` папку `server`, в `LemonUiDll` файл `lib/net48/LemonUI.SHVDN3.dll` из [LemonUI.SHVDN3 2.2.0](https://www.nuget.org/packages/LemonUI.SHVDN3/2.2.0). Затем из `work/RageCoopAdmin`:

```sh
dotnet restore Client/RageCoopAdmin.Client.csproj --locked-mode -p:PublicRelease=true -warnaserror
dotnet build Client/RageCoopAdmin.Client.csproj -c Release --no-restore -p:PublicRelease=true -warnaserror
```

Server, Bootstrap, EarlyClient и Installer собираются так же. Архивы выпуска упаковываются из рабочей копии автора: `tools/prepare_public_release.py` из этого архива исходников не запускается. В нём указаны закреплённые загрузки SHVDN 3.7.0-nightly.188 и .NET Runtime 10.0.14 (win-x64) и их хеши. Из корня исходников `bash tools/check.sh --public-release` запускает публичные сборки и проверки (Windows с Git Bash или macOS с CrossOver и .NET Framework 4.8).
