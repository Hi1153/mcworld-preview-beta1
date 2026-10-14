# Minecraft World Viewer 3D

A static GitHub Pages prototype for visualizing Minecraft Bedrock `.mcworld` files in the browser.

## Publish on GitHub Pages

1. Upload `index.html`, `style.css`, `main.js`, and `README.md` to the root of `Hi1153/mcworld-3d-viewer`.
2. Open **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**.
4. Choose branch `main` and folder `/(root)`, then Save.
5. Open `https://hi1153.github.io/mcworld-3d-viewer/` after deployment completes.

## Notes

- Runs in the browser; selected world data is not uploaded to a server by this app.
- Uses `mcbe-leveldb-reader` to read LevelDB keys and Three.js to render blocks.
- Initial prototype supports Bedrock persistent subchunk formats 8 and 9 and renders the Overworld. Legacy formats and some special cases are not supported yet.
- There is no artificial subchunk or rendered-block cap. Very large worlds are limited by the available memory and GPU resources of the device. The viewer builds visible block faces per subchunk rather than drawing full cubes for every block.
- Block colors are approximations based on block names, not the official Minecraft textures.
- External ES modules are loaded from esm.sh, so the browser needs internet access.

## Experimental chunk editor (preview only)

The experimental editor panel lets you enter a chunk-coordinate rectangle, inspect how many parsed chunks exist in the active dimension, temporarily hide those chunks from the in-memory preview, undo that preview change, and download a JSON coordinate plan.

**Important:** this build does not write to the LevelDB database and does not modify or export a changed `.mcworld`. The JSON file is only a reset plan, not a world save. The original uploaded world remains untouched. Do not treat a preview reset as a Minecraft chunk regeneration.

Chunk coordinates are used (one chunk is 16×16 blocks). Resetting the actual world requires a writable LevelDB backend and a validated `.mcworld` export path; that part is not included in this preview build.
