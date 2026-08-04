# High Tech (high-tech)

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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

High Tech indexes the APIs, data services, and reference artifacts that power the electronics, semiconductor, hardware, and IoT industries. The landscape covers electronic component data and distribution (Octopart / Nexar, Digi-Key, Mouser, Arrow Electronics, Avnet, Newark / element14), ECAD and PCB design data (SnapEDA, Ultra Librarian, Altium 365 via Nexar Design), and hardware lifecycle / IoT device management platforms (AWS IoT, Azure IoT Hub, Particle). The centerpiece of this repo is a normalized **Component** record schema — keyed on Manufacturer Part Number (MPN) + Manufacturer — together with a JSON-LD context aligned to schema.org and a Bill of Materials (BoM) schema for hardware engineering workflows.

**URL:** [Visit APIs.yml](https://raw.githubusercontent.com/api-evangelist/high-tech/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Reference
- **Access:** 3rd-Party
- **x-type:** topic

## Tags

Arrow Electronics, Availability, Bill of Materials, BoM, Component Data, Datasheets, Digi-Key, Distributors, ECAD, Electronic Components, Electronics, Footprints, Hardware, High Tech, IoT, Lifecycle, Manufacturer Part Number, Manufacturers, Mouser, MPN, Nexar, Octopart, PCB Design, Pricing, RoHS, Semiconductors, SnapEDA, Supply Chain, Symbols, Ultra Librarian

## APIs Indexed

### Component & Distribution Data

| Provider | Surface | Auth | Docs |
|---|---|---|---|
| **Octopart / Nexar Supply** | GraphQL | OAuth 2.0 | [nexar.com/api](https://nexar.com/api) |
| **Digi-Key Product Information V4** | REST | OAuth 2.0 (2LO / 3LO) | [developer.digikey.com](https://developer.digikey.com/products) |
| **Mouser Electronics Search API** | REST | API key | [mouser.com/api-search](https://www.mouser.com/api-search/) |
| **Arrow Electronics Pricing & Availability** | REST (JSON/XML) | Authorization key | [developers.arrow.com](https://developers.arrow.com/api/) |
| **Avnet** | Partner APIs | Account-based | [avnet.com](https://www.avnet.com/) |
| **Newark / element14** | Partner APIs | Account-based | [newark.com](https://www.newark.com/) |

### ECAD / PCB Design Data

| Provider | Surface | Docs |
|---|---|---|
| **SnapEDA** | Free symbols, footprints, 3D models | [snapeda.com](https://www.snapeda.com/home/) |
| **Ultra Librarian** | Symbols, footprints, 3D for 16M+ components | [ultralibrarian.com](https://www.ultralibrarian.com/) |
| **Altium 365 / Nexar Design** | GraphQL access to A365 workspace data | [nexar.com/api](https://nexar.com/api) |

### IoT Device Platforms

| Provider | Surface | Docs |
|---|---|---|
| **AWS IoT Core** | MQTT + REST + Device Shadow | [docs.aws.amazon.com/iot](https://docs.aws.amazon.com/iot/) |
| **Azure IoT Hub** | MQTT/AMQP + Device Twins + DPS | [learn.microsoft.com/azure/iot-hub](https://learn.microsoft.com/en-us/azure/iot-hub/) |
| **Particle Device Cloud** | REST + Webhooks + OTA | [docs.particle.io](https://docs.particle.io/reference/cloud-apis/api/) |

## Artifacts

This topic repo emphasizes **shared schemas and semantics** rather than per-provider OpenAPI specs (each provider's own repo holds those).

### `json-schema/` — JSON Schema (draft 2020-12)
- `high-tech-component-schema.json` — Canonical Component record: `mpn`, `manufacturer`, `description`, `category`, `datasheets[]`, `specifications[]`, `lifecycle`, `compliance[]`, `package`, `cad[]`, `offers[]`, `identifiers`.
- `high-tech-bom-schema.json` — Bill of Materials: `bomId`, `revision`, `lines[]` with reference designators, alternates (AML/AVL), and DNP flags.

### `json-structure/` — Field-by-field structural map
- `high-tech-component-structure.json` — Every Component field annotated with type, cardinality, and the upstream providers that contribute it.

### `json-ld/` — Linked-data semantics
- `high-tech-context.jsonld` — JSON-LD context aligning the Component record to `schema:Product`, `schema:Offer`, `schema:Organization`, `schema:PropertyValue`, and a `ht:` namespace for high-tech-specific terms (lifecycle status, RoHS / REACH compliance, CAD models, reference designators).

### `examples/` — Realistic payloads
- `high-tech-component-stm32f407-example.json` — Full Component record for STMicroelectronics STM32F407VGT6 MCU across three distributors.
- `high-tech-component-passive-resistor-example.json` — Yageo RC0402FR-0710KL chip resistor showing high-volume passive pricing.
- `high-tech-bom-iot-sensor-example.json` — Multi-line BoM for an IoT sensor node with alternates and DNP test points.
- `high-tech-octopart-graphql-search-example.json` — GraphQL `supSearchMpn` request/response mapped to the canonical record.
- `high-tech-digikey-keyword-search-example.json` — Digi-Key `POST /products/v4/search/keyword` request/response.
- `high-tech-mouser-part-search-example.json` — Mouser `SearchByPartNumber` request/response.

### `vocabulary/` — Domain terminology
- `high-tech-vocabulary.yml` — Terms across identity (MPN, distributor SKU), packaging (SMD, LQFP, 0402), lifecycle (NRND, LTB, EOL), compliance (RoHS, REACH, Conflict Minerals, ECCN, HTS), ECAD (symbol, footprint, 3D model, reference designator), and BoM (alternates, AML/AVL, DNP).

## Canonical Component Identity

```
(mpn, manufacturer.name)  ⟶  one Component
```

Every distributor SKU, ECAD asset, datasheet, lifecycle state, compliance statement, and price break attaches to this pair. The `identifiers` block carries cross-distributor lookup keys (Octopart ID, Digi-Key P/N, Mouser P/N, Arrow P/N, GTIN).

## Timestamps

- **Created:** 2026-05-23
- **Modified:** 2026-05-23
