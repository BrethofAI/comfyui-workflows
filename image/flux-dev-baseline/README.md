# Flux.1 [dev] baseline workflow

> Sane-defaults image generation with Flux.1 [dev]. **Scoped, not published:** no `workflow.json`, sample outputs or pin list yet, and no date.

## What it would be

A no-surprise starter for Flux. Reasonable sampler, scheduler, and CFG.
Planned graph:
- Model loader for [black-forest-labs/FLUX.1-dev](https://huggingface.co/black-forest-labs/FLUX.1-dev)
- T5 + CLIP encoders
- Single KSampler at default settings that look good
- VAE decode + save

No upscaler, no ControlNet, no IPAdapter — keep it simple.

Flux.1 [dev] is no longer Black Forest Labs' newest open-weights model
([FLUX.2 [dev]](https://huggingface.co/black-forest-labs/FLUX.2-dev)
followed in Nov 2025), so check the scope still makes sense before
building on this.

## Licence note

⚠️ The Flux.1 [dev] **weights** are under the
[FLUX.1 [dev] Non-Commercial License](https://github.com/black-forest-labs/flux/blob/main/model_licenses/LICENSE-FLUX1-dev):
no commercial use of the model itself. The licence does let you use
the **outputs** for any purpose, including commercial, except to train
a competing model. Use [Flux.1 [schnell]](https://huggingface.co/black-forest-labs/FLUX.1-schnell)
(Apache 2.0) if you need commercial use of open weights.

Both repos are gated on Hugging Face: you need an account and must
accept the conditions before the files download.
