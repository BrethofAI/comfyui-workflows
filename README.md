# comfyui-workflows

> Curated, tested, actually-working [ComfyUI](https://github.com/comfyanonymous/ComfyUI) workflows. Pinned to specific ComfyUI commits + custom-node versions. Real outputs, no broken nodes, no paywalled .safetensors links you don't have access to.

> 🚧 **Repo status (2026-04):** In preparation. Directory layout is
> live but workflow `.json` files and sample outputs are landing
> throughout May 2026 as the GPU is freed up between Brethof Voice Pro
> LoRA training runs. **[Star the repo](https://github.com/BrethofAI/comfyui-workflows)**
> to be notified when the first hero workflow (LTX chunked-loop) ships.

Maintained by [Brethof AI](https://brethof.com). Companion to
[awesome-local-ai](https://github.com/BrethofAI/awesome-local-ai),
where ComfyUI is listed as the dominant local-AI image / video
pipeline.

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

Every workflow in this repo ships with:

1. The `.json` file — committed plain text, diffable.
2. A README listing **exact** custom node URLs + commit SHAs known to
   work, model files with HuggingFace links and SHA256, and a tested
   ComfyUI commit.
3. A sample output (image / video) generated with that exact setup,
   so you can verify visual parity after install.
4. An optional `.png` workflow export with embedded metadata for
   drag-and-drop loading.

## Repo layout

```
comfyui-workflows/
├── image/
│   ├── flux-dev-baseline/
│   │   ├── workflow.json
│   │   ├── workflow.png         # drag-and-drop variant
│   │   ├── README.md            # nodes + models + samples
│   │   └── samples/             # reference outputs
│   └── ...
├── video/
│   ├── ltx-chunked-loop/        # ← hero workflow
│   ├── wan22-i2v/
│   └── ...
├── voice/
├── training/
└── utility/
```

## Hero workflows (read these first)

### 🎬 LTX chunked-loop video — arbitrary-length video from LTX-2

**Path:** `video/ltx-chunked-loop/`
**Status:** 🚧 in preparation — workflow JSON + README landing this week.

LTX-2 is a fantastic open-weights video model but its native context
window caps generations at a few seconds. The chunked-loop pattern in
this workflow generates long-form video by:

- Producing the first chunk normally.
- Re-feeding the **last N frames** of the previous chunk as the
  starting context for the next chunk.
- Maintaining a global motion / style lock via reference frames + a
  prompt-template that re-establishes context per chunk.
- Stitching with a smooth crossfade so the chunk boundaries are
  invisible.

This is a flagship Brethof AI workflow. We use it for the
[Nova YouTube channel](https://brethof.com)'s b-roll and intend to
keep it updated as LTX models evolve.

### `[stub]` 🖼️ Flux Dev baseline — sane defaults for SOTA image generation

**Path:** `image/flux-dev-baseline/`
**Status:** 🚧 stub. Workflow + sample outputs landing soon.

A no-frills Flux.1 [dev] starter — model loading, sane sampler config,
upscaler, ESRGAN refinement — that just works on consumer GPUs (16 GB
VRAM with quantisation, 24 GB unquantised).

### `[stub]` 🎨 Wan2.2 image-to-video

**Path:** `video/wan22-i2v/`
**Status:** 🚧 stub.

Take a still image, feed it to Wan2.2, get a cinematic 5-second clip.

## Categories planned

### Image (`image/`)

- Flux family — `[dev]` baseline, `[schnell]` fast-mode, ControlNet variants
- SDXL — base + refiner, LoRA training pipelines
- SD3 / SD3 Medium — community-license-aware setup
- Qwen-Image — image-gen + image-edit workflows
- Inpainting / outpainting templates

### Video (`video/`)

- **LTX chunked-loop** (hero)
- Wan2.2 — text-to-video, image-to-video, video-to-video
- Hunyuan-Video — long-form generation
- AnimateDiff classic SD-based animation
- Frame-interpolation post-processing

### Voice (`voice/`)

- Whisper transcription as a ComfyUI node graph (yes, it works)
- Bark / StyleTTS2 voice generation chained with image outputs
- Voice cloning workflows where weights permit

### Training (`training/`)

- Flux-dev LoRA training pipeline (paired with Ostris ai-toolkit)
- SDXL LoRA training
- Dataset prep + caption generation

### Utility (`utility/`)

- Upscaling chains (ESRGAN-NMKD, RealESRGAN, ultrasharp)
- Watermark removal — read the licence first
- Format converters
- Batch processors

## How to use a workflow

1. Clone this repo. Each workflow is a self-contained directory.
2. Open `<workflow>/README.md` and check:
   - The ComfyUI commit it was tested on (use `git checkout <sha>` in
     your ComfyUI clone if you want exact parity).
   - The list of custom nodes required, with the **specific commit
     SHAs** known to work.
   - The model files needed, with HuggingFace URL + SHA256.
3. Install custom nodes via ComfyUI Manager or `git clone` directly
   into `ComfyUI/custom_nodes/`.
4. Place models in their canonical paths (`models/checkpoints/`,
   `models/loras/`, `models/clip/`, etc.).
5. Drag the `workflow.png` (or load the `.json`) into ComfyUI.
6. Compare your output to `samples/` — visual parity confirms
   environment is correct.

## What we don't ship

- **Model weights.** Models live on HuggingFace / Civitai / their
  origins. We link, you download.
- **Paywalled custom nodes.** If the node requires a Patreon
  subscription to install, the workflow is excluded.
- **One-shot art.** This list is for *reproducible workflows*, not for
  showcasing finished images. Civitai is better for that.

## Hardware reality

We test workflows on:

- **NVIDIA RTX 5090 (32 GB)** — primary test rig for video and
  high-VRAM image work.
- **NVIDIA RTX 4060 Ti (16 GB)** — secondary test for "does this run
  on consumer hardware".
- Any workflow that won't run in 16 GB without quantisation gets a
  prominent "VRAM ≥ 24 GB" tag.

For AMD / Intel GPU testing we welcome PRs documenting compatibility.

## Related work

- **[awesome-local-ai](https://github.com/BrethofAI/awesome-local-ai)** — ComfyUI listed under Image / Video Generation.
- **[awesome-ai-mine](https://github.com/BrethofAI/awesome-ai-mine)** — License clauses for the underlying models (Flux, SDXL, LTX, Wan).
- **ComfyUI core repo:** [github.com/comfyanonymous/ComfyUI](https://github.com/comfyanonymous/ComfyUI)
- **ComfyUI-Manager:** [github.com/ltdrdata/ComfyUI-Manager](https://github.com/ltdrdata/ComfyUI-Manager) — install custom nodes from inside ComfyUI itself.

## Contributing

Open an issue or PR with:

- The workflow `.json` file.
- A `README.md` per the template (see `_template/` directory once it
  lands).
- The exact custom-node commits and model file SHA256s your workflow
  uses.
- A reference output in `samples/` so others can verify their
  environment matches.

We will not accept workflows that depend on private models, gated
LoRAs, or "DM me for the .safetensors". Reproducibility is the point.

## License

[MIT](LICENSE) for the workflow JSONs and accompanying text. Models
linked from each workflow have their own licenses — see
[awesome-ai-mine](https://github.com/BrethofAI/awesome-ai-mine).

---

Maintained by **[Brethof AI](https://brethof.com)** — AI tools built for
people who take their data seriously.
