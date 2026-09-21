# Lakestream Improvement Proposals (LIPs)

A LIP is a short design document for a change that other people build on or operate against: the
Lakestream API, an SPI contract, a storage format, or the contract between Kafka and Lakestream.
Writing the design down before the code lets reviewers and future implementers agree on *what* is
changing, and why, before anyone debates *how*.

This repository holds the LIPs for every Lakestream component. A LIP is written for Lakestream as a
whole, and lists what changes in each component:

| Component | Where the code lives |
|---|---|
| `lakestream-api`: the public, protocol-neutral Lakestream API | [lakestream-io/ursa](https://github.com/lakestream-io/ursa), in the `lakestream-api` module |
| Ursa: stream storage on object storage, and the materialization framework | [lakestream-io/ursa](https://github.com/lakestream-io/ursa) |
| Ursa for Apache Kafka (UFK): Kafka with diskless topics backed by Ursa | [lakestream-io/kafka](https://github.com/lakestream-io/kafka) |

To propose a change, read [CONTRIBUTING.md](CONTRIBUTING.md), then start from
[TEMPLATE.md](TEMPLATE.md).

## Status

| Status | Meaning |
|---|---|
| Proposed | Under review in a pull request |
| Accepted | Merged; implementation can start |
| Implemented | The code has landed on the default branch of every component the LIP changes |
| Released | Shipped in a release; record the component and version |
| Superseded | Replaced by a later LIP; link to it |

## Index

| LIP | Title | Components | Status |
|---|---|---|---|
| [161](proposals/LIP-161-Table-Materialization-Framework.md) | Table Materialization Framework | lakestream-api, Ursa | Released in Ursa 1.0.0 |
| [162](proposals/LIP-162-Diskless-Storage-with-Ursa-Integration.md) | Diskless Storage with Ursa Integration | Kafka (UFK) | Released in UFK 4.3.1.1 |
| [163](proposals/LIP-163-Ursa-Zone-Aware-Owner-Selection.md) | Ursa Zone-Aware Owner Selection | Kafka (UFK) | Released in UFK 4.3.1.1 |

Numbering starts at 161, the number LIP-161 was first published under. LIP-162 and LIP-163 were
LIP-001 and LIP-002 in lakestream-io/kafka before they moved here.
