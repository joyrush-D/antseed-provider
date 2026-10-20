# Qwen3.8-27B: opt-in buyer quickstart

Trial offer checked on 20 October 2026. Confirm the current offer in your own buyer before spending.

This is a new provider with limited settled service history. Explicitly choosing this provider is an informed opt-in; you do **not** need to reduce your global automatic-routing trust threshold. This guide is for real inference work. It offers no token rewards, reimbursement, uptime guarantee, or guaranteed eligibility for ANTS.

## Offer

| Item | Trial setting |
| --- | --- |
| Public service | `Qwen3.8-27B` |
| Implementation | Local MLX, 4-bit quantization; MTP is not enabled |
| Input / cached input | $0.01 / $0.01 per million tokens |
| Output | $0.03 per million tokens |
| Simultaneous requests | 1 |
| Input | 1–16 text messages; combined content at most 2,048 characters **and** 4,096 UTF-8 bytes |
| Output | At most 256 tokens |
| Intended work | Short text translation, extraction, rewriting, or summarization |

The character and byte limits both apply. This trial does not accept images, tool calls, structured-output requests, or large agent prompts. Availability is best effort: the host may decline new requests while its primary workload is active.

## 1. Prepare your own buyer and budget

Use the [official local buyer setup](https://antseed.com/docs/api/). With the official CLI installed, the documented start command is:

```sh
antseed buyer start
```

The default local endpoint is `http://127.0.0.1:8377`. Keep it local. If the desktop app already runs your buyer, use that existing buyer.

This is a **paid** service. Fund **your own** buyer using the official funding flow, with a USDC amount you choose. Do not send funds to this provider's peer ID as a deposit. The native buyer does not provide gateway-style cumulative budgets; use the [official gateway](https://antseed.com/docs/quickstart/) if you need API-key spend limits.

Funding and transaction costs are separate from inference:

- The official automatic deposit relay currently deducts **0.05 USDC per sweep**. First-deposit and funding requirements are described in the [funding documentation](https://antseed.com/docs/gateway/funding/).
- Normal inference channel transactions are submitted by the seller, which pays the Base gas. The current **4% protocol fee is deducted from the seller's settlement**, not added again to the listed buyer token charge.
- Your exchange/card provider may charge separately. Authorized-wallet actions, such as on-chain recovery or withdrawal, can require Base ETH gas. Review those costs before signing.

See [payments](https://antseed.com/docs/payments/) and [seller payment fees](https://antseed.com/docs/provide/payments/). A channel reservation locks spending capacity; it is not the same as consumed inference spend.

## 2. Check the offer without sending an inference request

```sh
curl -s http://127.0.0.1:8377/v1/models
```

Find this exact peer and service in the catalog:

```text
Peer:    a1dd66149a9e23e49bd144403132ea3a18356ece
Service: Qwen3.8-27B
```

Catalog reads are free and come from your buyer's discovered peer cache. If the offer is absent, wait for discovery or check the official troubleshooting guidance; do not assume an old listing means the provider is available.

## 3. Send your real short-text task to this provider

Replace the message content below with work you actually want performed. **Running this request authorizes real USDC charges through your funded buyer.** The example is not a request to generate artificial usage.

```sh
curl -i http://127.0.0.1:8377/v1/chat/completions \
  -H 'Content-Type: application/json' \
  -d '{
    "model": "a1dd66149a9e23e49bd144403132ea3a18356ece@Qwen3.8-27B",
    "messages": [
      {"role": "user", "content": "REPLACE WITH YOUR OWN SHORT TEXT TASK"}
    ],
    "max_tokens": 128,
    "stream": false
  }'
```

The `peer@model` syntax pins this request only. Other requests keep your normal routing preferences. A hard pin does not fall back to another provider. Your buyer's hard price/reputation requirements and any gateway policy still apply; explicit selection does not override them.

For the full syntax and response headers, see [the official local buyer API](https://antseed.com/docs/api/) and [routing](https://antseed.com/docs/api/routing/).

## Limits and results

- Use either `max_tokens` or `max_completion_tokens`, not both; the supported range is 1–256. If neither is supplied, the trial uses 256.
- Message roles are `system`, `user`, and `assistant`; each content value must be a string. Send one completion per request (`n: 1`, if specified).
- For streaming, include `"stream_options": {"include_usage": true}`. The non-streaming example above is the simpler starting point.
- On `429` or `503`, respect `Retry-After` and wait; do not run a tight retry loop. Service may remain unavailable while the primary workload runs.
- Inspect the returned peer/model, usage, and price headers. For authoritative channel totals, use the official buyer's metering and payment views. A response, a pending authorization, and final settlement are different states.
- If your buyer refuses the provider under a hard policy, review that policy deliberately or choose another provider. Do not disable safety or trust controls globally to make this example work.

