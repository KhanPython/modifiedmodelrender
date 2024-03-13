## Synopsis

Roblox games often have collectibles - inventories, pets, etc. We need to display them in a menu. ViewportFrames aren't a scalable solution, but authoring pre-rendered icons is time-consuming and finicky. This project automates the whole process.

Icon creation is in 4 distinct stages - rendering, downscaling, uploading, and collection into a JSON file. The [Ninja build system](https://ninja-build.org/) creates a dependency graph, only executing a step if a source file has been changed or added.

This project is not a definitive solution - it's a template, hackable to meet your game's needs.
* You _will_ want to adjust the scene setup in your `template.blend`. Tune the lighting and shading effects to match your game's artstyle.
* You _will likely_ want to modify `blenderScript.py`, to get different camera angles and zooms.
* You _will likely_ want to change the downscaled image size (128x128 by default).

## Prerequisites

- Fill your Roblox details into `.env`. A template is provided at `.env.example`.
- With Python (version >=10), install dependencies; `pip install urllib3 python-dotenv requests Pillow`.
- A [recent version of Blender](https://www.blender.org/download/). Offline installed versions and [Steam](https://store.steampowered.com/app/365670/Blender/) are supported.

## Usage

1. Export models from studio into a folder named `content` inside of this repo. The filenames of your `.obj`s will correspond to the AssetIds within the exported icon data, so ensure they're descriptive.
2. Run `py 0_ninja.py` to re-generate build commands.
3. Copy the exported `out/out.json` into your game's source tree.

Re-generate build commands if you've added or removed models. Re-run the build after regenerating build commands, or to retry a failed build.

## Attribution
This is a modification of an existing repository: https://github.com/OttoHatt/modelrender