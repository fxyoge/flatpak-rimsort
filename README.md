# com.fxyoge.RimSort flatpak

Unofficial flatpak for [https://github.com/RimSort/RimSort](RimSort).

## Usage

```sh
flatpak install --user flathub com.fxyoge.RimSort

# If using the normal version of Steam:
flatpak override --user com.fxyoge.RimSort --filesystem "~/.config/unity3d/Ludeon Studios/RimWorld by Ludeon Studios/Config"
flatpak override --user com.fxyoge.RimSort --filesystem "~/.steam/steam/steamapps/common/RimWorld"
flatpak override --user com.fxyoge.RimSort --filesystem "~/.steam/steam/steamapps/workshop/content/294100"

# ...or, if using flatpak Steam:
flatpak override --user com.fxyoge.RimSort --filesystem "~/.var/app/com.valvesoftware.Steam/config/unity3d/Ludeon Studios/RimWorld by Ludeon Studios/Config"
flatpak override --user com.fxyoge.RimSort --filesystem "~/.var/app/com.valvesoftware.Steam/.steam/steam/steamapps/common/RimWorld"
flatpak override --user com.fxyoge.RimSort --filesystem "~/.var/app/com.valvesoftware.Steam/.steam/steam/steamapps/workshop/content/294100"

# ...and any additional libraries you have:
flatpak override --user com.fxyoge.RimSort --filesystem "/path/to/your/steam/library/SteamLibrary/steamapps/common/RimWorld"
flatpak override --user com.fxyoge.RimSort --filesystem "/path/to/your/steam/library/SteamLibrary/steamapps/workshop/content/294100"

# You could instead give access to e.g. all of ~/.steam/steam/steamapps, if you're so inclined. I prefer to only give it what it needs and recommend doing the same.
```

## Known Issues

* The "Browse Workshop" window might not work as expected because RimSort doesn't have access to Steam, and therefore is "Unable to initialize Steamworks API due to exception: SteamNotRunningException". Probably just need to set up the right permissions, but I don't use that feature so I haven't tried fixing it.
* Running the game from RimSort breaks for the same reason - it doesn't have access to Steam.
* RimSort will crash on some machines (e.g. mine, lol) when clicking any button that opens a file browser dialog such as the four game, config, etc. folder selectors, or the git repo configs. This issue appears to happen in the normal version of the app, so I think it's just a plain ol' boring bug. Workaround: directly modify the config at `~/.var/app/com.fxyoge.RimSort/data/RimSort/settings.json`.

## Development

```sh
# Build and install:
flatpak-builder --user --install --force-clean build-dir com.fxyoge.RimSort.yml
```
