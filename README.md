# Momo

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

MoMo is Vietnam's largest mobile-money and e-wallet platform, operated by Online Mobile Services
Joint Stock Company ("M_Service"), founded in 2007 and licensed by the State Bank of Vietnam for
e-wallet, money transfer and collection/disbursement services.

This repository profiles the four public APIs MoMo publishes at
[developers.momo.vn](https://developers.momo.vn/):

- **All-in-One (AIO v2) Payment Gateway** — `https://payment.momo.vn/v2/gateway/api`
- **Business Page OpenAPI** — `https://business.momo.vn/api`
- **Voucher Distribution API** — `https://business.momo.vn/api`
- **Mini App Open API** — `https://openapi.momo.vn/gateway/open/v1`

**MoMo publishes no OpenAPI, AsyncAPI, protobuf or WSDL.** The nearest machine-readable contract is
a set of **14 public Postman collections** (67 requests), which MoMo links from its own docs and
which are saved verbatim in [`postman/`](postman/). Everything else in this repository is either
searched from MoMo's own documentation or derived from those collections; nothing is invented.

Notable findings from the 2026-08-26 pass:

- **Idempotency is real and documented** — `requestId` in the request body, unique per company
  account, honoured for at least 31 days, HTTP 422 + `resultCode` 7000 on a duplicate in flight.
- **Reversibility is documented** — cancel-before-capture and full/partial refund, with published
  amount bounds. **Disbursements are not reversible**; MoMo publishes no recall operation.
- **No status page, no SLA, no deprecation policy, no rate limits.** A withdrawn API version is
  discovered at runtime via `resultCode` 12.
- **No `/.well-known/` documents on any host** (64 probes across 8 hosts) and **no MCP server**.
- **PCI DSS v4.0** is claimed on MoMo's own newsroom; the first-party PHP and Java SDKs are stale
  (untagged since 2022 and version 1.0 from 2019 respectively), while the Mini App component
  packages on npm are actively released.

- https://www.momo.vn/
- https://developers.momo.vn/
- https://github.com/momo-wallet
