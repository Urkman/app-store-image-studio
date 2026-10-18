# App Store Image Studio

An agent skill for designing App Store screenshot sets together with you, from app analysis and real screenshots to individual image revisions and final exports.

Works with **Codex, Claude Code, and Grok Build** through the shared `SKILL.md` format. This repository contains instructions for your coding agent, not a standalone image editor or a one-click rendering service.

## Your app. Your direction.

The agent analyzes your app and proposes visual concepts with a recommendation. Choose one, combine ideas, or describe your own direction. Reference images are inspiration, never a mandatory template.

Everything can change:

- Screenshot position, size, orientation, framing, and arrangement.
- Background artwork, a solid color, or a gradient.
- Text amount, wording, typography, and placement.
- Individual images after the first examples, including device and language variants.

## How it works

1. **Clarify inputs.** Ask whether you already have screenshots and which devices need images: iPhone, iPhone Duo, and/or iPad. Resolve orientations, display variants, languages, and important features.
2. **Understand the app.** Inspect its purpose, audience, workflows, design, and existing assets. Ask for missing information rather than inventing product claims.
3. **Propose concepts.** Present suitable directions, example copy, and a proposed image sequence. You can provide your own idea at any time.
4. **Create initial examples.** Reuse suitable supplied screenshots. Capture missing views from the actual app in the simulator when the required tools and app are available.
5. **Revise individual images.** Request changes by image ID. The agent updates the affected compositions and previews while preserving your other choices.
6. **Export and verify.** Produce the full set, inspect the actual images, and check the selected export targets against current Apple requirements.

## Install globally

### With the skills CLI

With Node.js and Git installed, run:

```sh
npx skills add Urkman/app-store-image-studio --global
```

Select the agents you want to use during installation. You can also explicitly select an agent, for example:

```sh
npx skills add Urkman/app-store-image-studio --global --agent claude-code
```

See the [skills.sh directory](https://skills.sh) and [CLI documentation](https://skills.sh/docs/cli) for supported agents and options. The directory tracks installations through the CLI's default anonymous telemetry; directory visibility may take time to update.

### Manual shared installation

You need Git and a coding agent that supports local skills. As an alternative to the CLI, run these commands once to keep one shared installation for all three agents:

```sh
mkdir -p "$HOME/.agents/skills"
git clone https://github.com/Urkman/app-store-image-studio.git \
  "$HOME/.agents/skills/app-store-image-studio"

mkdir -p "$HOME/.codex/skills" "$HOME/.claude/skills" "$HOME/.grok/skills"

ln -s "$HOME/.agents/skills/app-store-image-studio" \
  "$HOME/.codex/skills/app-store-image-studio"
ln -s "$HOME/.agents/skills/app-store-image-studio" \
  "$HOME/.claude/skills/app-store-image-studio"
ln -s "$HOME/.agents/skills/app-store-image-studio" \
  "$HOME/.grok/skills/app-store-image-studio"
```

Only create the links for the agents you use. If the destination already exists, inspect your existing installation first; do not overwrite it. A working link to the shared folder needs no further action. Start a new agent session after installation.

### Update a manual installation

```sh
git -C "$HOME/.agents/skills/app-store-image-studio" pull --ff-only
```

All linked agents use the same updated files. Commit or preserve local modifications before updating.

## Use

Open your app project with the agent, then invoke:

| Agent | Invocation |
| --- | --- |
| Codex | `$app-store-image-studio` |
| Claude Code | `/app-store-image-studio` |
| Grok Build | `/app-store-image-studio` |

For example:

> Analyze this app and help me create App Store images. Ask about existing screenshots and target devices, suggest suitable visual concepts, and let me choose before creating the set.

Already have a direction?

> I have iPhone screenshots in `marketing/screenshots/`. Create English and German images with a warm background, minimal text, and large screenshots. Show initial examples first.

After reviewing the examples:

> Image 02: move the screenshot to the right, shorten the headline, and use a light gradient. Keep the other images as they are.

The agent should respond in your language. You can revise the direction at any stage.

## Requirements and device support

- **Supplied screenshots:** The agent needs access to the image files and tools to inspect and compose them. Simulator access is not required when your screenshots already cover the requested views.
- **New simulator captures:** A Mac with Xcode, the relevant installed simulator runtimes, a buildable app project, and tools to navigate its UI. Login or demo data may require your input.
- **iPhone Duo and iPad:** The app and installed simulator must support the requested display state and orientation. The skill does not invent missing device support or turn a stretched phone capture into a tablet interface.
- **Rendering:** The agent chooses suitable available tooling or reuses your project's renderer. It keeps marketing dependencies separate from your native app.
- **Generated background art:** Optional and dependent on an available image-generation tool. Screenshot UI and typeset text remain separate from generated artwork.
- **Export verification:** Current Apple documentation must be accessible to confirm requirements. Unconfirmed targets are identified as provisional.

This is a workflow skill, so execution capabilities depend on the agent and tools you run it with. Installing it does not provide Xcode, simulator automation, fonts, image generation, or a rendering engine.

## Deliverables

A completed run should provide:

- Ordered image exports for the selected devices, orientations, and languages.
- A shared preview/contact sheet or local gallery with stable image IDs.
- Original screenshot sources and their capture context.
- Editable copy and composition settings, including per-image changes.
- Repeatable rendering sources and a regeneration command.
- A concise validation summary and any remaining blockers.

By default, the agent can use `marketing/app-store/` in the target project, or follow your existing folder convention. Those generated app assets belong in your app project, not in this skill repository.

## Scope

The skill uses real app captures and truthful product messaging. It does not fabricate UI, data, or features. No style, fixed layout, background treatment, or text count is imposed.

Uploading to App Store Connect and submitting a release are outside the default workflow and require a separate request. Local image checks do not imply App Store acceptance.

## Repository structure

```text
app-store-image-studio/
├── SKILL.md                         # Agent workflow and creative contract
├── agents/openai.yaml               # Codex display metadata
└── references/capture-and-export.md  # Simulator and export guidance
```

Read the [skill instructions](SKILL.md) or the [capture and export guide](references/capture-and-export.md) for the full workflow.

## Validation status

The skill's structure, frontmatter, metadata, and local reference links have been validated. A complete run against a second app has not yet been performed. Tool discovery and rendering may need adjustment for your environment.

## Contributing

Issues and pull requests are welcome. For workflow problems, include the agent used, selected devices and languages, available screenshot/capture tools, expected behavior, and what happened. Avoid including credentials or private screenshots.
