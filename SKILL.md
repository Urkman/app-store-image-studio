---
name: app-store-image-studio
description: "Create and revise App Store marketing screenshot sets for iPhone, iPhone Duo, and iPad. Analyze an app, ask about existing screenshots and target devices, propose visual concepts or follow the user's own idea, capture missing simulator screenshots, and iterate on individual images before exporting."
---

# App Store Image Studio

Create a reusable, app-specific set of App Store images collaboratively. Communicate in the user's language. Work in the target app's project or the user's chosen asset folder; this skill does not depend on any particular repository.

## Creative contract

- No visual element is mandatory. Screenshot position, size, orientation, framing, cropping, background image, solid color, gradient, text amount, typography, and text position are all choices the user can change, including after seeing examples.
- Existing marketing images, when supplied or found in a project, are inspiration only. Do not inherit their theme, palette, background, layout, copy, or device treatment by default.
- Base recommendations on the target app and the user's intent. Offer alternatives and explain your recommendation; let the user decide or describe a different idea. Do not force a preset or treat the first choice as permanent.
- When a composition shows app UI, use real app screenshots. A screenshot-free opening image is a supported composition, not a missing capture. Do not generate, redraw, or invent UI, app data, capabilities, or testimonials. Generated background or hero artwork stays separate from app UI and typeset text.

## 1. Establish inputs and devices

Inspect project instructions and look for existing marketing assets, screenshot sources, capture tooling, renderers, and saved image-set state. Reuse relevant work without silently adopting its design.

Explicitly establish both of these before producing the set, unless the user has already answered:

1. **Existing screenshots:** Does the user already have screenshots, and where are they? They can attach them or point to local files. Ask whether suitable supplied captures should be reused; capture only missing or unwanted views. Do not start by assuming simulator capture is necessary.
2. **Target devices:** Which of **iPhone, iPhone Duo, and/or iPad** need images? Resolve the required display sizes and orientations for the selected devices. For Duo, establish which outer/closed and inner/open views are needed, each with its own orientation. Do not silently select all devices or infer targets solely from the available simulator.

Also establish languages, desired image count or important features, and any personal visual idea or references. Ask only what is missing, in small useful groups. Offer a recommendation when the user delegates a choice. Do not ask for information already present in the conversation or project.

Inspect supplied screenshots visually, check their actual dimensions, language, device context, useful content, and obvious loading/error states. Report gaps and propose how to fill them. A source screenshot's dimensions and the final marketing canvas dimensions are separate facts.

## 2. Analyze the app

Understand the app's main purpose, audience, core workflows, distinguishing features, existing visual identity, and supported layouts. Use project materials and the running app when available. Distinguish observed facts from assumptions; ask if a missing product fact changes the message. Do not pretend to have run an app when only source or assets were inspected.

## 3. Agree which images to create

After the analysis, propose a concrete ordered image list, not just a visual style. Explain which feature, app view, or benefit each image should show and why it belongs in the set. Include the screenshot-free opener as a proposal. Explicitly invite the user to add their own ideas, replace suggestions, remove images, or change the order. Agree the list before starting captures or production; if the user delegates the selection, state your proposed list and proceed within that delegation.

Save the agreed list with stable image IDs. For each image record its purpose, the exact app screen(s) and UI/data state needed (or no screenshot for the opener), target devices/display states, orientations and languages, and whether a suitable existing capture is available or a new one is required. A compact table is useful for reviewing this with the user.

Treat this list as the capture plan. Capture the screens and states needed for the agreed images, including the user's own ideas. Do not replace a requested feature with an easier-to-capture screen, silently drop it, or choose the final set solely from whichever screenshots happen to be available. When a requested capture cannot be obtained, name the affected image and blocker, ask how to resolve it, and keep the item visible as pending. User changes update the agreed list and its capture requirements.

## 4. Propose the visual direction

Propose a manageable set of distinct directions, usually two or three, with:

- Why each direction fits this particular app, and which you recommend.
- Example imagery/background treatment, palette, text amount and placement, and screenshot arrangement.
- Truthful benefit-led copy for the agreed images in the requested language; discuss changes to the agreed feature sequence rather than silently replacing it.

Plan an opening attention-grabber without an app screenshot: app name or supplied logo, a strong app-relevant visual, a short value proposition, and a few useful app-specific details or benefits. Derive these from the app analysis; do not reuse another app's subject matter or claims. Present this opening image with the initial examples, rather than making the user ask for it separately. The user can change, replace, or omit it like any other image.

For the following feature images, make compositions such as large straight or tilted screenshots, a headline with short supporting copy, and small icon/callout groups straightforward options. They can share a cohesive visual language without requiring identical arrangements. Keep these as editable choices, not a fixed template or minimum text count.

Invite the user's own idea explicitly. They can select, combine, modify, or replace every proposal. If they already supplied a clear direction, develop it instead of requiring an unnecessary style vote. If they delegate the choice, state your recommendation and proceed within that authorization.

Show representative visual examples when that helps the decision. Mark exploratory mock UI as illustrative; do not pass it off as a real capture or use it in deliverables. Do not create a new interactive editor application unless requested; a gallery and repeatable renderer are enough.

## 5. Capture and create initial examples

For missing screenshots, read [references/capture-and-export.md](references/capture-and-export.md). Work through the agreed image list and its required screen/device/state combinations. Build and run the target app using its repository's instructions, discover the available simulator tools, navigate to the specified views and states, and capture them. Follow that project's scheme and build settings rather than copying them from a reference app. Check each capture visually against its planned image and record the resulting source path and capture status.

Use existing suitable captures first. If required source, simulator, login, or app support is unavailable, explain the exact gap and ask for the missing input; continue independent design work without inventing captures. Never stretch a phone screenshot into a tablet or Duo interface.

Create a small representative batch before producing the whole set: the screenshot-free opener and at least one feature image, unless the user chose a different sequence. Include different aspect ratios when their layouts need separate review. Missing simulator captures should not prevent creating the opener from available app materials. Keep compositions and copy editable in structured project state plus a repeatable local renderer. Prefer existing tools and bundled dependencies; do not add rendering dependencies to the native app.

Keep production lightweight: use one shared renderer with per-image settings, reusable background assets, and optional screenshot layers. A simple color/gradient or existing artwork can produce an initial example immediately; use image generation when the selected concept calls for bespoke artwork. Do not require a separate application, elaborate setup, or new capture for a text/background-only revision.

Give every image a stable ID and show it in the preview. Explain which concept each example illustrates. Ask for feedback on the examples, including individual images. Let the user describe changes in their own words.

## 6. Revise per image

Accept requests such as "Bild 02: Screenshot rechts, weniger Text und einen hellen Verlauf" without reopening the entire questionnaire.

- Resolve the requested image IDs, locales, and device variants from the conversation and saved state; ask only if the target is ambiguous.
- Update the relevant image's settings and regenerate affected previews. Do not apply a local edit across the set unless requested. For a global request, update the selected scope consistently.
- Keep unmentioned choices and source captures intact. Preserve previous exports or a recoverable prior version before replacing them.
- Show the updated image with its ID and briefly explain the changes. Continue iteration as requested; the concept can still change at this stage or after export.

Persist edits in the rendering source as well as the output so later regeneration does not lose feedback.

## 7. Complete, verify, and deliver

Once the examples establish the chosen direction, create the remaining images. Before calling exports App Store ready, verify current Apple requirements for the selected display categories using official documentation, as described in the reference. Do not rely on old sizes copied from a reference project.

Reconcile the exports with the agreed image list: every selected image and requested variant must have an output, be explicitly removed by the user, or be reported as blocked. Check that each screenshot shows the agreed feature and state. Do not call the set complete while required captures or images are silently missing.

Inspect every full-size export and a thumbnail/contact sheet for text clipping, legibility, contrast, screenshot framing, missing assets, empty outputs, and unintended changes to the captured UI. Verify actual encoded dimensions, format, color mode, and alpha against the selected export requirements. Recheck affected variants after an edit.

Deliver ordered image files, a combined preview or local gallery, original capture sources, editable composition/copy state, and a working regeneration command. A practical default is a dedicated `marketing/app-store/` folder with `raw/`, `exports/`, `preview/`, and rendering sources; use an existing project convention when present.

The saved state should record each stable image ID, composition type (screenshot-free opener or feature image), feature/message, source capture when used, artwork/logo assets, locale, device/display, orientation, output dimensions and path, copy, layout/background choices, and per-image overrides. Screenshot-free images have no required capture source. Record the capture context and the Apple requirements source/date so future runs can distinguish confirmed targets from assumptions.

End with links to the images and preview, a short validation summary, and any actual blockers. Invite further edits to individual images. Uploading to App Store Connect or submitting a release is outside this skill's default scope and needs a separate user request.
