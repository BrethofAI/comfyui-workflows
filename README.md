# comfyui-workflows

> Reproducible [ComfyUI](https://github.com/Comfy-Org/ComfyUI) workflows, pinned to specific ComfyUI commits + custom-node versions. **No workflows are published yet.**

Maintained by [Brethof AI](https://brethof.ai). Companion to
[awesome-local-ai](https://github.com/BrethofAI/awesome-local-ai),
where ComfyUI is listed as the dominant local-AI image / video
pipeline.

## Status

This repo is a small placeholder. What is here today:

- `_template/README.md` — the README format every workflow must follow.
- `image/flux-dev-baseline/` and `video/ltx-chunked-loop/` — short
  READMEs describing two workflows we scoped. Neither has a
  `workflow.json`, sample outputs or a pin list.

We are not promising a date. Local image and video models move fast,
and a workflow that is stale on arrival is exactly the problem this
repo exists to avoid.

## Why this list exists

ComfyUI workflows posted on Civitai, Reddit, and YouTube are notorious
for being broken on download. The reasons:

- **Custom nodes drift.** A node that existed when the workflow was
  saved may have been renamed, removed, or replaced by a different
  author's fork.
- **Model paths are absolute.** The original creator's
  `models/checkpoints/...` path doesn't exist on your machine.
- **Required models are vague.** "You need this LoRA" with no link, no
  hash, and possibly no longer-public source.
- **Workflows are hidden inside .png exports** that some sites strip
  EXIF / metadata from.

Any workflow published here must ship with:

1. The `.json` file — committed plain text, diffable.
2. A README listing **exact** custom node URLs + commit SHAs known to
   work, model files with Hugging Face links and SHA256, and a tested
   ComfyUI commit.
3. A sample output (image / video) generated with that exact setup,
   so you can verify visual parity after install.
4. An optional `.png` workflow export with embedded metadata for
   drag-and-drop loading.

## How to use a workflow (once one is published)

1. Clone this repo. Each workflow is a self-contained directory.
2. Open `<workflow>/README.md` and check the ComfyUI commit, the custom
   nodes with their commit SHAs, and the model files with Hugging Face
   URL + SHA256.
3. Install custom nodes with ComfyUI-Manager or `git clone` them
   directly into `ComfyUI/custom_nodes/`. In current ComfyUI the
   Manager ships with core: `pip install -r manager_requirements.txt`,
   then start ComfyUI with `python main.py --enable-manager`.
4. Place models in their canonical paths (`models/checkpoints/`,
   `models/loras/`, `models/clip/`, etc.).
5. Drag the `workflow.png` (or load the `.json`) into ComfyUI.
6. Compare your output to `samples/` — visual parity confirms
   environment is correct.

## What we don't ship

- **Model weights.** Models live on Hugging Face / Civitai / their
  origins. We link, you download.
- **Paywalled custom nodes.** If the node requires a Patreon
  subscription to install, the workflow is excluded.
- **One-shot art.** This list is for *reproducible workflows*, not for
  showcasing finished images. Civitai is better for that.

## Related work

- **[awesome-local-ai](https://github.com/BrethofAI/awesome-local-ai)** — ComfyUI listed under Image / Video Generation.
- **[awesome-ai-minefield](https://github.com/BrethofAI/awesome-ai-minefield)** — Licence clauses for several of the underlying models (FLUX.2, SD3, LTX-2, Wan 2.2).
- **[awesome-llms-txt](https://github.com/BrethofAI/awesome-llms-txt)** — Tools doing AI-agent discovery right.
- **[awesome-private-ai](https://github.com/BrethofAI/awesome-private-ai)** — Privacy-respecting AI architectures.
- **[awesome-linux-for-ai](https://github.com/BrethofAI/awesome-linux-for-ai)** — Linux distros for local AI work.
- **ComfyUI core repo:** [github.com/Comfy-Org/ComfyUI](https://github.com/Comfy-Org/ComfyUI)
- **ComfyUI-Manager:** [github.com/Comfy-Org/ComfyUI-Manager](https://github.com/Comfy-Org/ComfyUI-Manager) — install custom nodes from inside ComfyUI itself.

## Contributing

Open an issue or PR with:

- The workflow `.json` file.
- A `README.md` following [`_template/`](_template/README.md).
- The exact custom-node commits and model file SHA256s your workflow
  uses.
- A reference output in `samples/` so others can verify their
  environment matches.

We will not accept workflows that depend on private models, gated
LoRAs, or "DM me for the .safetensors". Reproducibility is the point.

## License

[MIT](LICENSE) for the workflow JSONs and accompanying text. Models
linked from each workflow have their own licenses — check each model
card, and see
[awesome-ai-minefield](https://github.com/BrethofAI/awesome-ai-minefield)
for the ones it covers.

---

Maintained by **[Brethof AI](https://brethof.ai)** — AI tools built for
people who take their data seriously.
