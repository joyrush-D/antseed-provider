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

Qwen3.5-9B Q4_K_M runs locally with llama.cpp / Apple Metal on an M5 Max with 128 GB unified memory. One concurrent text request; no tools or multimodal input. Technical discovery and encrypted connectivity have been checked; this is not a claim of independent buyer demand, earnings or sustained uptime.

| Model | State | Input / cached input, USD per million tokens | Output, USD per million tokens |
|---|---|---:|---:|
| Qwen3.5-9B | Configured pilot; availability conditional | 0.05 / 0.05 | 0.20 |
| Qwen3.8-27B-4bit | Prepared candidate; not live, MTP not enabled | 0.01 / 0.01 proposed | 0.03 proposed |

The configured context is 8,192 tokens, but the gateway currently accepts at most 16 plain-text messages, 2,048 combined input characters and 4,096 UTF-8 input bytes. An explicit output budget of 1–256 tokens is required. Streaming requires `stream_options.include_usage=true`. These limits are enforced without silent truncation.

## Availability and billing

This is best-effort, conditional capacity, not a 24/7 availability commitment. A workload guard prioritizes an existing training workload; it rejects new requests when safe capacity cannot be verified. Buyers should inspect current signed network metadata and handle temporary unavailability. No free-to-use model or verified TEE is currently offered.

Usage is metered by the model and Antseed software. Technical self-tests and related-party activity are distinct from independent customer demand. Advertised price, token output, settled USDC and ANTS eligibility are separate facts; no rewards or daily revenue are promised.

## 27B rollout

The 27B candidate is prepared at USD 0.01 / 0.03 per million input/output tokens, with one concurrent short request and the workload guard retained. Runtime output quality, metering and cancellation checks must pass before it is advertised as available. Its source checkpoint contains an MTP component, but the prepared generic backend does not enable MTP; it is not advertised as an MTP service.
