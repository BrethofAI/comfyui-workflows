# Flux.1 [dev] baseline workflow

> Sane-defaults image generation with Flux.1 [dev]. No frills, just a workflow that works.

🚧 **Coming next:** workflow.json, sample outputs, exact pin list.

## What this is

A no-surprise starter for Flux. Reasonable sampler, scheduler, and CFG.
Includes:
- Model loader for [black-forest-labs/FLUX.1-dev](https://huggingface.co/black-forest-labs/FLUX.1-dev)
- T5 + CLIP encoders
- Single KSampler at default settings that look good
- VAE decode + save

No upscaler, no ControlNet, no IPAdapter — keep it simple. If you want
those, fork the workflow.

## Licence note

⚠️ Flux.1 [dev] is **non-commercial only** — see
[awesome-ai-mine](https://github.com/BrethofAI/awesome-ai-mine) for the
exact clause. Use [Flux.1 [schnell]](https://huggingface.co/black-forest-labs/FLUX.1-schnell)
(Apache 2.0) if you need commercial use of open weights.
