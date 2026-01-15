# Mod Uploader
[![Python](https://img.shields.io/badge/Python-3.7+-blue.svg)](https://www.python.org/downloads/)
[![Rich](https://img.shields.io/badge/Rich-13.0+-green.svg)](https://rich.readthedocs.io/)



A lightweight console tool to inspect, summarize and upload mods into Minecraft modpacks. Designed for quick local workflows: discover modpacks, preview contents (mods, resourcepacks, datapacks, config), detect Minecraft version and pack metadata, and copy selected \`.jar\` mods into a target modpack.

## Key features

- Discover modpacks for supported launchers and list them with clear summaries.
- Show counts and previews for:
    - Mods (\`.jar\`)
    - Resource packs (\`.zip`, \`.mcpack`, etc.)
    - Datapacks
    - Config entries
- Display total modpack size (human-readable).
- Extract Minecraft/modpack metadata from:
    - `manifest.json` (CurseForge style)
    - `pack.mcmeta`
    - Common instance files (`instance.cfg`, `version.json`, `eula.txt`)
- Interactive flow:
    - Choose launcher (TLauncher or CurseForge)
    - Confirm or set base directory
    - Scan and select a modpack
    - Pick local \`.jar\` mods to upload
    - Upload copies into the modpack’s `mods` folder
- Saves last-used settings to `~/.moduploader_config.json` for faster repeat runs.

## Installation

1. Ensure Python 3.8+ is installed.
2. Clone the repository and run the main script:
    - `python src/com/emanuelplays/main/main.py`

No external dependencies are required beyond the Python standard library.

## Usage

Run the script and follow prompts:

- Select the launcher.
- Confirm or provide the base directory where instances/modpacks are stored.
- The tool scans and lists found modpacks with:
    - Mods count and a short preview of filenames
    - Resourcepacks count and preview
    - Datapacks count and preview
    - Config count (if any)
    - Total size (e.g., `1.4G`)
    - Detected Minecraft version and manifest name/description if available


Select a modpack, then choose a local folder with \`.jar\` files and pick which mods to copy into the modpack's `mods` folder.

Example snippet of displayed summary:

    MyModpack
        mods: 12 files - example1.jar, example2.jar, ...
        resourcepacks: 3 files - rp1.zip, ...
        datapacks: 2 items - dp1, dp2
        size: 1.4G
        minecraft version: 1.16.5

## Configuration

- Persistent configuration is stored at `~/.moduploader_config.json`.
- The tool records:
    - Last used launcher
    - Base directory per launcher
    - Last mods folder used (to speed up uploads)

## Supported launchers

- TLauncher (default detection path under `~/.minecraft/versions`)
- CurseForge (default detection path under `~/curseforge/minecraft/Instances`)

Paths can be customized at runtime.

## Internals (high level)

- Scans directories to discover modpack folders.
- Summarizes folders using suffix patterns to identify mods and resourcepacks.
- Calculates folder size recursively.
- Reads common metadata files to infer Minecraft version and pack descriptions.
- Simple interactive UI with typing/spinner effects for a friendly console experience.
- Copies selected \`.jar\` files into the target modpack `mods` folder.

## Contributing

- Open issues and PRs for improvements.
- Keep changes focused on usability and robust filesystem handling.


