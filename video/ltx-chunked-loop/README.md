# LTX chunked-loop video workflow

> Longer video from LTX-2 by chunking + last-frame re-feeding. **Scoped, not published:** no `workflow.json`, samples or pin list yet, and no date.

This README describes the approach we scoped. It is not a shipped
workflow.

## The pattern

For clips longer than a single generation:

1. **Chunk 1** — generate normally from the prompt + reference frame.
2. **Chunk 2** — feed the *last 4 frames* of chunk 1 as the starting
   context for chunk 2, plus a prompt template that re-states the
   global scene description.
3. **Chunk N** — same, repeated.
4. **Stitch** — overlap-blend the join (4 frames at 24 fps = ~166 ms)
   so the boundary is hard to see.

The chunk-prompt template re-establishes:
- Scene description (constant per scene)
- Style / camera lock ("anamorphic 2.39:1, slow dolly-left, golden hour")
- Motion direction (so chunk boundaries don't jump motion vectors)

## Models and nodes

- LTX-2 weights: [Lightricks/LTX-2](https://huggingface.co/Lightricks/LTX-2), superseded by [Lightricks/LTX-2.3](https://huggingface.co/Lightricks/LTX-2.3) — LTX-2 Community License; see [awesome-ai-minefield](https://github.com/BrethofAI/awesome-ai-minefield) for its clauses.
- ComfyUI supports LTX-Video 2 and 2.3 natively, and Lightricks
  recommends its LTXVideo nodes from ComfyUI-Manager
  ([Lightricks/ComfyUI-LTXVideo](https://github.com/Lightricks/ComfyUI-LTXVideo)).
- A published version would pin the ComfyUI commit, node commits,
  model SHA256s and VRAM requirements, per [`_template/`](../../_template/README.md).
