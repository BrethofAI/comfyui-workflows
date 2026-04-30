# LTX chunked-loop video workflow

> Generate **arbitrary-length** video from LTX-2 by chunking + last-frame re-feeding. Hero workflow for Brethof AI; powers the Nova YouTube b-roll.

🚧 **Coming next:** the actual `workflow.json`, sample outputs, and
the exact custom-node + model pin list. This README is the spec we're
shipping against.

## The pattern

LTX-2 caps single-shot generation at a few seconds. To make minute-long
clips:

1. **Chunk 1** — generate normally from the prompt + reference frame.
2. **Chunk 2** — feed the *last 4 frames* of chunk 1 as the starting
   context for chunk 2, plus a prompt template that re-states the
   global scene description.
3. **Chunk N** — same, indefinitely.
4. **Stitch** — overlap-blend the join (4 frames at 24 fps = ~166 ms)
   so the boundary is invisible.

The chunk-prompt template re-establishes:
- Scene description (constant per scene)
- Style / camera lock ("anamorphic 2.39:1, slow dolly-left, golden hour")
- Motion direction (so chunk boundaries don't jump motion vectors)

## Required (when shipped)

- ComfyUI commit: TBD (will pin specific SHA)
- LTX-2 weights: [Lightricks/LTX-Video](https://huggingface.co/Lightricks/LTX-Video) — see [awesome-ai-mine](https://github.com/BrethofAI/awesome-ai-mine) for licence status of each LTX version
- Custom nodes: TBD (will pin specific commits)
- VRAM: 24 GB recommended; 16 GB possible with FP8 quantisation

## Status

- [ ] `workflow.json` exported and committed
- [ ] `samples/` populated with 30-second + 60-second reference clips
- [ ] Custom-node + model pin list verified on a clean ComfyUI install
- [ ] FP8-quantised variant for 16 GB GPUs

PRs welcome once the workflow lands.
