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

⚠️ The Flux.1 [dev] **weights** are under the
[FLUX.1 [dev] Non-Commercial License](https://github.com/black-forest-labs/flux/blob/main/model_licenses/LICENSE-FLUX1-dev):
no commercial use of the model itself. The licence does let you use
the **outputs** for any purpose, including commercial, except to train
a competing model. Use [Flux.1 [schnell]](https://huggingface.co/black-forest-labs/FLUX.1-schnell)
(Apache 2.0) if you need commercial use of open weights.

Both repos are gated on Hugging Face: you need an account and must
accept the conditions before the files download.
