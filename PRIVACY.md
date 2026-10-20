# Privacy and Data Handling Notice

**Operational disclosure for this limited pilot. Updated 20 October 2026.**

Prepared: 20 October 2026.

## 1. Operator and service

The service name is **Joyrush Local AI**, operated by the independent individual provider publicly known as **Joyrush**. Public contact is through [GitHub Issues](https://github.com/joyrush-D/antseed-provider/issues). The operator's legal name and private application email are supplied separately to the Foundation and are not published in this notice.

This notice describes the current limited Antseed inference pilot and the handling observed in its local deployment. It is not Antseed Foundation's privacy policy and does not describe unrelated services operated by other network participants.

The currently configured model is Qwen3.5-9B Q4_K_M. A Qwen3.8-27B 4-bit deployment is under preparation and is not represented here as live. MTP is not enabled. The service has one concurrent request slot and is available only when its workload admission guard permits it.

## 2. Data processed to deliver inference

The provider receives the text messages and supported generation settings that the buyer sends, processes them using the local model, and returns generated text and usage information. This requires the model process to handle the request and response in memory.

The current custom inference gateway does not intentionally write prompt text, response text, request headers, buyer identifiers or request URLs to its own access log. The reviewed deployment is for inference and contains no workflow for training a model on buyer submissions.

This is **not a zero-retention or immediate-erasure guarantee**. Model caches, operating-system memory or swap, software failures and diagnostics may retain data temporarily. No verified TEE or independently audited confidential-computing guarantee is claimed.

## 3. Usage, payment and diagnostic records

The Antseed software is configured to maintain local metering and payment records. The reviewed database schemas include:

- Session and peer identifiers, service/provider identifiers and timestamps.
- Input and output token counts, request counts, status, latency and streaming indicators.
- Usage receipts, receipt verification information and digital signatures.
- Buyer and seller wallet addresses, payment-channel limits, deadlines, statuses and settlement amounts.
- Response hashes and payment authorization metadata.

The database schema also supports free-tier abuse-control records, including buyer addresses and remote IP addresses. The current pilot does not advertise a free model; the existence of these fields is not a claim that such records have actually been collected.

Local process output and error logs are retained for operation and troubleshooting. The seller currently enables diagnostic logging filtered for model-health events. The model server also writes operational output and errors. A complete audit of every third-party diagnostic path has not been performed, so this notice does not promise that all third-party components are incapable of including content in exceptional diagnostics.

## 4. Why records are used

Inference content is processed to answer the buyer's request. Usage and payment records support accurate billing, buyer authorization, settlement, receipt verification, dispute handling and abuse prevention. Operational records support availability and fault diagnosis.

The provider does not offer prompt or response content for sale and does not intentionally use it to train the deployed model. Any future material change to these practices should be disclosed before the changed processing begins.

## 5. Network path, public records and other parties

Inference runs on an Apple Silicon machine operated in Shenzhen, China. Buyer connections reach it through an operator-controlled public VPS relay and an encrypted tunnel. The reviewed relay forwards protocol traffic and caches signed public service metadata; its code does not log inference payloads.

Hosting and network operators may process connection metadata in providing connectivity. The relay supplier and physical hosting region have not yet been independently confirmed from the available deployment records. The service therefore makes no promise that relay processing occurs in a specified country or that all processing remains in the buyer's jurisdiction. Traffic may cross national borders. These details will be updated when verified; an IP address or a server nickname is not treated as proof of physical location.

Antseed network participants may receive public service metadata such as provider identity, advertised services, prices, capability information and availability. USDC settlement takes place on Base. Wallet addresses, transactions and other on-chain records may be public and independently retained by explorers, indexers and other network participants.

No commercial model API is used as the inference backend in the reviewed current deployment. Participation in the Antseed network may involve independently operated infrastructure whose privacy practices the provider does not control.

## 6. Retention and deletion

No fixed automatic deletion schedule for the local Antseed metering/payment records or process logs was confirmed in this deployment review. Records therefore may remain until the operator reviews and deletes them. This fact is disclosed rather than promising a retention period that is not implemented.

On receiving a request, the operator will assess which local records can be deleted, taking into account outstanding settlements, disputes, security needs and any applicable recordkeeping obligations. A deletion request does not guarantee immediate removal of all copies or diagnostic artifacts.

Public blockchain records and copies independently kept by other network participants cannot be erased by this provider. The provider cannot promise deletion of records outside its control.

## 7. Access and security

The local model endpoint and custom inference gateway bind to loopback addresses. Public service traffic uses the Antseed transport path and an encrypted relay tunnel rather than exposing the model HTTP backend directly.

These controls reduce exposure but do not establish perfect security or audited data isolation. Privileged local operators and administrators may be able to access process memory, files or diagnostic records.

## 8. Buyer choices and requests

Buyers choose whether and what to submit. Please do not send passwords, wallet recovery phrases, payment-card details or highly sensitive personal information to this limited pilot.

For access, correction, deletion or privacy questions, open a [GitHub Issue in the service repository](https://github.com/joyrush-D/antseed-provider/issues). Issues are public: initially provide only a general description and ask for a private handling route if the matter involves personal information. Do not post prompt text, identity documents, private keys, seed phrases, passwords or other confidential information in an issue. The operator may need proportionate evidence through a suitable private route to establish that a request concerns the requesting person.

The provider will respond to requests and handle complaints according to the circumstances and applicable requirements. This notice does not claim certification or guaranteed compliance in every jurisdiction.

## 9. Changes

Material changes to the live model, processing route, logging, data recipients or retention should be reflected in a revised notice.

