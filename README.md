# Side Quests — Life Organizer

A static, single-page life organizer. The app entry point is `index.html`; its
seasonal artwork is stored under `assets/`.

## Publish with GitHub Pages

1. Upload the repository contents, including `index.html` and the complete
   `assets/` directory.
2. In the repository, open **Settings → Pages**.
3. Choose **Deploy from a branch**, select the branch you uploaded (usually
   `main`) and the `/ (root)` folder, then save.
4. Open the Pages URL shown in the Pages settings when deployment completes.

Keep these paths unchanged so the seasonal icons and wallpaper load:

- `assets/halloween/`
- `assets/christmas/`

`source-assets/` contains original artwork kept for reference; the published
app does not need it. Opening `index.html` with the GitHub file viewer does not
run the app; use the GitHub Pages URL instead.

## Performance notes

The app renders the active view on data refresh and rebuilds a view when it is
opened, rather than keeping every view's cards mounted at once. Leaving a view
releases its rendered cards and any object URLs used by image previews. Large
resource-card grids defer offscreen layout and painting, and poster images load
lazily with asynchronous decoding. Drag-and-drop cards request a compositor
layer only while being dragged.

The app is a single static page with no build pipeline or server. Browser tab
suspension is left to the browser, and worker-based processing or virtualized
drag-and-drop lists are not used because they add complexity without a measured
need for this personal organizer.
