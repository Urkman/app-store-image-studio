# Simulator captures and export verification

Read when acquiring missing screenshots or preparing final exports. Discover installed tool capabilities rather than assuming a particular MCP server, simulator model, SDK, or renderer is available.

## Capture from the actual app

Start with the agreed image list from the app analysis and user discussion. Map each required screenshot to an image ID, exact app view/state, device/display context, orientation, and locale. Reuse matching supplied captures; take every missing required capture and update the list with its path/status. Suitable screenshots of unrelated screens do not fulfill an agreed image. Keep blocked captures explicit instead of substituting different features without the user's decision.

1. Read the target project's `AGENTS.md` and its build/run guidance. Determine project/workspace, scheme, bundle ID, supported devices, and any existing screenshot/demo mode. Follow repository-specific build settings; do not copy paths, bundle IDs, or schemes from another project.
2. Inspect installed Xcode and simulator inventory. Shell discovery can use `xcodebuild -list`, `xcrun simctl list devices available`, and `xcrun simctl list runtimes`; first confirm the tools exist. If available, use purpose-built simulator build and interaction tools according to their documented API.
3. Build for the selected simulator using an isolated build-output directory. Boot the selected device, install and launch the app, and navigate with available simulator UI tools. Use an explicit simulator UDID throughout instead of an ambiguous `booted` target when multiple simulators are running.
4. Prefer existing supported demo data or screenshot fixtures. If login or populated data is required, identify what the user must provide. Do not make real purchases, send commands to physical devices, or mutate production records just to stage a screen. Avoid silently changing app capabilities, supported device families, or release behavior to obtain a marketing capture. Discuss necessary app changes if no suitable supported capture route exists.
5. Wait for the view to be fully rendered. Capture using the simulator screenshot tool or `xcrun simctl io <UDID> screenshot <output.png>`, then inspect the image. Prefer coherent, suitable status-bar contents when the simulator supports overrides; preserve any prior override configuration you change so it can be restored.
6. Store capture provenance: source filename, device/model or explicit display context, OS, orientation, locale, app view, and whether demo data was used. Inspect for private information before using a capture in deliverables; prefer suitable sample data or recapture when needed.

Do not overwrite user-provided originals. If no interaction tools exist for a required navigation step, explain that step and ask the user to navigate or provide a capture; continue the parts that do not depend on it.

## Device distinctions

- **iPhone:** Establish the requested display category and orientation rather than assuming the first available simulator.
- **iPad:** Capture a real supported iPad layout for the chosen orientation. Enlarging a phone screenshot does not establish iPad support. Native source captures can be placed proportionally in a larger marketing canvas, but record what device was actually captured and verify the intended App Store category.
- **iPhone Duo:** Inspect installed SDK/simulator support and current authoritative requirements. Confirm outer/closed versus inner/open display context and orientation from actual tools and captures. Do not invent display dimensions, fold-state commands, frames, or App Store upload categories. If a required state is unavailable, identify the missing capture precisely; a changed canvas size is not a substitute.

The final marketing canvas may differ from the source capture dimensions. Preserve the UI aspect ratio. Screenshot positioning, deliberate clipping, rotation, framing, or multiple captures are creative choices; preview them clearly and ensure they do not fabricate functionality or obscure the intended message. For official device artwork, check its current usage rules before transforming it; a neutral graphic frame is another option.

## Rendering without imposing a design

Reuse an existing renderer when suitable; otherwise choose the simplest available repeatable compositor. A local HTML/CSS composition or an image compositor can both work. Do not scaffold a full web application just to export images.

Keep each image's text, source paths, device target, background, and composition properties in editable state. Support both screenshot-free and screenshot-based compositions in the same renderer: a hero does not require a dummy screenshot, frame, or simulator session. Keep artwork, logo, headline, supporting details/icons, and optional screenshot/frame as separate layers. Expose screenshot placement, scale, angle/perspective, text positions, and background treatment as per-image settings so ordinary feedback needs only a settings edit and rerender. Use separate layout parameters for portrait and landscape where needed, instead of stretching one finished poster. Escape user-supplied text appropriately for the rendering format and wait for all fonts/images to load before capture or export.

If the user chooses generated background or hero artwork, use available image-generation tools for those visual layers. A screenshot-free opener can use an app-relevant subject, illustration, or abstract visual alongside the real app name/logo and a few verified benefits. Preserve supplied brand assets rather than regenerating their lettering. Keep screenshot pixels and typeset copy separate from generated art; never generate the app UI inside a device mockup. Solid colors and gradients need no generated asset. Reuse chosen artwork across a set when suitable instead of generating an entirely new image for each revision. Do not import a reference app's background or preset palette unless the user chose it.

Use tools already available in the project or the workspace runtime. In Codex desktop, `load_workspace_dependencies` can locate bundled Node/Python libraries; use the returned paths rather than hardcoded machine-specific runtime directories. Keep marketing tooling separate from the native app's dependencies.

## Confirm current output requirements

At export time, consult Apple's current primary documentation:

- [Screenshot specifications](https://developer.apple.com/help/app-store-connect/reference/app-information/screenshot-specifications/)
- [Upload app previews and screenshots](https://developer.apple.com/help/app-store-connect/manage-app-information/upload-app-previews-and-screenshots/)

Verify the selected display category's accepted dimensions/orientations, image formats, color/alpha requirements, and set limits. Confirm new device categories from official documentation or actual App Store Connect UI evidence. If authoritative requirements for a requested device cannot be confirmed, label exports as provisional for that target and explain what remains unverified.

For each final image:

- Inspect encoded width/height, file type, color mode, and alpha with an image metadata tool; an extension or filename is not proof.
- Open the actual rendered result at full size and check thumbnail legibility. Check localized wrapping, asset loading, bounds, proportional UI, and agreement with the user's latest changes.
- Keep ordered filenames using stable numeric IDs and locale/device/orientation folders. Distinguish contact sheets and review images from upload files.
- Save the exact regeneration command, dependency prerequisites, and requirements URL/date alongside the editable rendering sources. Ensure rerendering reads the saved per-image edits.

Do not declare a set uploaded or accepted by App Store Connect after local validation alone.
