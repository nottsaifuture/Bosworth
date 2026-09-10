# The Bosworth — Field Farm

An interactive 3D tour of The Bosworth, a four-bedroom detached home: orbit the
exterior, cut away either floor, jump to a room viewpoint, open doors, and walk
through the inside in first person.

**Everything is in one file: `index.html`.** Open it from any web server and it runs.

## Publishing on GitHub Pages

1. Create a repository and upload `index.html`, `README.md` and `THIRD-PARTY-LICENSES.md`.
2. In the repository, open **Settings → Pages**.
3. Under *Build and deployment*, set **Source** to *Deploy from a branch*, pick
   the `main` branch and the `/ (root)` folder, then **Save**.
4. After a minute the tour is live at `https://<your-username>.github.io/<repository>/`.

Share that address with anyone. Nothing needs to be installed at their end.

## Viewing it on your own machine

Opening `index.html` by double-clicking will **not** work — browsers block
modules loaded from `file://`. Serve the folder instead:

```sh
python3 -m http.server 8000
```

Then open <http://localhost:8000>.

## Controls

- **Viewer:** drag to orbit, scroll or pinch to zoom, right-drag to pan, click a room or a door.
- **Floor tabs:** show the ground or first floor; *Whole House* restores the exterior.
- **Room viewpoints:** smoothly frames an individual room.
- **Walk Inside:** enters the hall. Click the scene for mouse look; WASD or the arrow
  keys move; Shift walks faster; E operates the door under the reticle within 2 metres.
  Escape releases the mouse, and *Exit Walkthrough* returns to orbit.
- **Touch (iPhone and iPad):** the left joystick moves, dragging the right side looks, and
  the door under the reticle gets its own button. No keyboard is needed.

## Internet connection

The 3D libraries (three.js and Rapier) are pulled from the jsDelivr CDN at pinned
versions, which is what keeps this to a single small file. A viewer therefore needs
to be online. To make it work offline instead, download those two libraries next to
`index.html` and point the `importmap` in the `<head>` at the local copies.

## How this file is produced

It is generated from the React source in the `Bosworth` project by
`standalone/build.mjs`. The 3D model, interiors, physics and engine code is used
unchanged; only the interface is rewritten without React. To rebuild after editing
the source:

```sh
node standalone/build.mjs
```

## Accuracy

This is an architectural interpretation of a low-resolution marketing plan, not
surveyed CAD. Door positions and swings, the stair opening, storage, the garage
placement, ceiling heights, finishes and furniture are inferred. The quoted
1,066 sq ft is the brochure's approximate area.
