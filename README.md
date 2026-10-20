# Joyrush Local AI

Independent Apple Silicon inference provider on Antseed. Updated 20 October 2026.

## Provider identity

- Operator: Joyrush ([joyrush-D](https://github.com/joyrush-D))
- Registered agent ID: **297151**
- Seller peer ID: `a1dd66149a9e23e49bd144403132ea3a18356ece`
- [GitHub ownership proof](antseed.json)
- [Privacy and data handling notice](PRIVACY.md)
- [Contact / issues](https://github.com/joyrush-D/antseed-provider/issues) — public initial contact only; do not post confidential data.

## Current pilot

Qwen3.8-27B runs locally as a 4-bit MLX checkpoint on an M5 Max with 128 GB unified memory. MTP is not enabled. One concurrent short text request; no tools or multimodal input. The public service key is Qwen3.8-27B and maps to the local Qwen3.8-27B-4bit backend. This is not a claim of independent buyer demand, earnings or sustained uptime.

| Model | State | Input / cached input, USD per million tokens | Output, USD per million tokens |
|---|---|---:|---:|
| Qwen3.8-27B | Active 4-bit pilot; availability conditional; MTP disabled | 0.01 / 0.01 | 0.03 |

The configured context is 8,192 tokens, but the gateway currently accepts at most 16 plain-text messages, 2,048 combined input characters and 4,096 UTF-8 input bytes. Specify either `max_tokens` or `max_completion_tokens` from 1–256; if neither is supplied, the service defaults to 256. Supplying both or an explicit out-of-range limit is rejected. Streaming requires `stream_options.include_usage=true`. These limits are enforced without silent truncation.

## Availability and billing

This is best-effort, conditional capacity, not a 24/7 availability commitment. A workload guard prioritizes an existing training workload; it rejects new requests when safe capacity cannot be verified. During a verified collection-start gap, admission may wait up to five seconds for a fresh observation; it never treats unknown or stale evidence as available capacity. Buyers should inspect current signed network metadata and handle temporary unavailability. No free-to-use model or verified TEE is currently offered.

Usage is metered by the model and Antseed software. The installed payment implementation rounds each request to whole micro-USDC; at these low rates, very short requests may round to zero. An amount displayed in an estimated cents field is not proof of settlement. Technical self-tests and related-party activity are distinct from independent customer demand. Advertised price, token output, settled USDC and ANTS eligibility are separate facts; no rewards or daily revenue are promised.

## How to choose this provider

For a real short-text task, see the [opt-in buyer quickstart](BUYER-QUICKSTART.md). It shows how to inspect the current offer and explicitly select this peer for one request using the official buyer, without lowering the buyer's global automatic-routing trust preference. Hard buyer and gateway policies still apply. This is a new provider with limited settled history; explicit selection is the buyer's choice and does not guarantee availability or ANTS rewards.

## 27B rollout

The 27B pilot was started on 20 October 2026 at 19:34 China Standard Time (UTC+8). Thirteen bounded local runtime checks passed, covering fixed Chinese/English answers, returned usage, streaming, input limits, concurrency rejection and a follow-up request after client disconnect. These are functional checks, not a broad quality benchmark or paid orders. Immediate cancellation of GPU work after a client disconnect is not guaranteed.

The workload guard checks admission before a request; it does not preempt an already-running inference when another workload starts. Requests are limited to 256 output tokens and one concurrent slot. Brief workload overlap is possible. The source checkpoint includes an MTP component, but this backend does not enable it. The previous 9B service has been removed from this pilot's advertisement.
