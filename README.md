# High Tech (high-tech)

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
