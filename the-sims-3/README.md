# The Sims 3 Setup

## Flatpak Steam

```shell
flatpak install -y flathub com.github.tchx84.Flatseal com.valvesoftware.Steam
```

1. Open _Steam_
2. Click _Steam_
3. Click _Settings_
4. Click _Storage_
5. Click the drop down menu
6. Click _Add Drive_
7. Add `~/.var/app/com.valvesoftware.Steam/Steam` instead of `~/.var/app/com.valvesoftware.Steam/.local/share/Steam`
8. Rename this newly created drive and make default

## The Sims 3

Mount your DVD drive and grant Flatpak Steam access to it as The Sims 3 will read it to verify ownership of the game, i.e.,

```shell
sudo mkdir -p /run/media/$USER/Sims3
sudo mount -o ro /dev/sr0 /run/media/$USER/Sims3
flatpak override --user --filesystem=/run/media/$USER/Sims3:ro com.valvesoftware.Steam
```

Reboot Flatpak Steam, then

1. Navigate to `~/.var/app/com.valvesoftware.Steam/Steam/steamapps/common`
2. Create a folder called `The Sims 3`
3. Move the contents of the loaded DVD into `The Sims 3`
4. Open _Steam_
5. Go to _Library_
6. Click _Add a Game_
7. Click _Add a Non-Steam Game..._
8. Click _Browse..._
9. Select `Sims3Setup.exe` from `~/.var/app/com.valvesoftware.Steam/Steam/steamapps/common/The Sims 3`
10. Right-click `Sims3Setup.exe`
11. Click _Properties..._
12. Click _Compatibility_
13. Check _Force the use of a specific Steam Play compatibility tool_
14. Select _Proton Experimental_
15. Launch `Sims3Setup.exe` and finish setup
16. Navigate to `~/.var/app/com.valvesoftware.Steam/.local/share/Steam/steamapps/compatdata/`
17. Figure out the corresponding folder which holds `The Sims 3`
18. Navigate to `pfx/drive_c/Program Files (x86)/Electronic Arts/The Sims 3/Game/Bin/` in that folder
19. Copy `TS3.exe` to `~/.var/app/com.valvesoftware.Steam/Steam/steamapps/common/The Sims 3/Game/Bin/`, i.e.,

```shell
sudo cp "$HOME/.var/app/com.valvesoftware.Steam/.local/share/Steam/steamapps/compatdata/game_id/pfx/drive_c/Program Files (x86)/Electronic Arts/The Sims 3/Game/Bin/TS3.exe" "$HOME/.var/app/com.valvesoftware.Steam/Steam/steamapps/common/The Sims 3/Game/Bin/"
```

where `game_id` is replaced with your respective id.

20. Return to _Library_
21. Right-click `Sims3Setup.exe`
22. Click _Properties..._
23. In _TARGET_ replace `Sims3Setup.exe` with `Game/Bin/TS3.exe`
24. In _START IN_ replace `The Sims 3/` with `The Sims 3/Game/Bin/`
25. Rename `Sims3Setup.exe` to `The Sims 3`

You are done. :)
