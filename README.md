# 🌙 Chief of Staff

**You sleep. It works the night shift.**

Before bed, dump tomorrow's schedule, your unread messages, and whatever is on your mind.
A 270M-parameter **Gemma 3** running **100% in your browser** reads it all on the night shift
and hands you a finished morning brief:

- ☀️ **Top 3 priorities** — ranked, each with the reason it made the cut
- ✍️ **Replies, already drafted** — one click to copy, in a warm human voice
- ✅ **One decision, already made** — the small thing you were putting off, decided with a reason
- 🌙 **A night log** — watch your chief of staff work through the pile, step by step

A chief of staff sees your schedule and your messages — the most private text you own.
This one never sends it anywhere: no server, no account, no API key. All inference happens
on your device with an open-weight model, and it works fully offline after a one-time download.

## Try it

Open `index.html` in a browser (or visit the GitHub Pages deployment), hit **✨ Demo night**
for a prefilled sample, then **🌙 Start the night shift**. First load downloads the model
(~1 GB, fp32); after that it is cached and works offline.

For the real ritual: fill in *your* tomorrow before bed, start the night shift, and close the
laptop. Your brief is saved on the device and waiting in the morning.

## How it works

Built for a 270M model, not despite it: instead of one giant prompt, the night shift is
**three small, strict-format jobs** — (1) rank tomorrow's priorities, (2) triage messages and
draft replies, (3) make the put-off decision — each with a one-shot example, line-header
parsing, and a garbage-token guard with a raw-text fallback.

- [Transformers.js](https://huggingface.co/docs/transformers.js) 4.2.0 in-browser inference
- Model: `onnx-community/gemma-3-270m-it-ONNX`, **fp32** on WebGPU with WASM fallback
  (the fp16 WebGPU path overflows on this model and emits `<unused56>` token loops —
  a bug diagnosed during Week 1 of this series and reused as a fixed setup ever since)
- Single static `index.html` — no build step, no backend

## The series

Built for the DEV Hacktoberfest Open-Source AI Challenge, Week 3 — "Slow and Steady":
the laziest productivity system is the one that works while you sleep.
Weeks 1–2: [Touch Grass Card](https://github.com/qife422/touch-grass-card) ·
[Listing Writer](https://github.com/qife422/listing-writer) — same tiny model, same browser.

## License

MIT
