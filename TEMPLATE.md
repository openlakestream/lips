# LIP-NNN: Title of the proposal

<!--
Copy this file to proposals/LIP-NNN-Short-Title.md and replace every placeholder.
Delete any section that doesn't apply, and write "None" where a category has no changes.
See CONTRIBUTING.md for the process.
-->

- *Author(s)*: Your Name (@your-github-handle)
- *Status*: Proposed
- *Proposal time*: YYYY-MM-DD
- *Components*: the components this changes, from lakestream-api, Ursa and Kafka (UFK)
- *Discussion*: link to the discussion or issue where the proposal started
- *Implementation*: links to the pull requests, once they exist
- *Released in*: the component and version, once released, such as "Ursa 1.1.0"

## TL;DR

Two or three sentences: the problem, the change, and who it affects.

## Background

What a reader needs to know to follow the proposal. Link to existing documentation rather than
repeating it.

## Motivation

The problem, concretely. What are people trying to do, and what gets in the way today?

## Goals

### In scope

### Out of scope

## Design

### High-level design

### Detailed design

## Changes by component

What changes in each component. Delete the components that don't change.

- **lakestream-api** ([lakestream-io/ursa](https://github.com/lakestream-io/ursa)):
- **Ursa** ([lakestream-io/ursa](https://github.com/lakestream-io/ursa)):
- **Kafka (UFK)** ([lakestream-io/kafka](https://github.com/lakestream-io/kafka)):

## Public-facing changes

List everything that a user, an operator or an implementer can see change.

### API and SPI

Changes to `lakestream-api` types and to SPI contracts such as `TableMaterializer`.

### Storage formats

Changes to the on-object or WAL formats, and to serialized field numbers or identifiers.

### Kafka client behavior

What producers, consumers and admin clients observe on a diskless topic: request handling, errors,
offsets and limits.

### The Kafka and Lakestream contract

Changes to how a topic maps to a stream, to the stream properties Kafka writes, or to the payload
Kafka writes to the WAL. Say which Ursa components read what you change.

### Classic topics

Any effect on Kafka topics that don't use diskless storage. The expected answer is "None".

### Configuration

New, changed or removed configuration keys, with their defaults, and the component that reads each
one.

### Metrics and logs

## Compatibility

### Upgrade

What happens when a cluster upgrades? Do existing data, configuration and metadata keep working?

### Rollback

What happens if an operator rolls back to the previous release after this change has written data or
metadata? If rolling back isn't possible, say so plainly.

### Version skew

If the change spans components, which one has to be released or upgraded first? Kafka brokers bundle
an Ursa runtime, and the Ursa compactor runs as a separate service, so say what happens while they
run different versions, for example during a rolling upgrade.

## Security considerations

New inputs, credentials, network access or permissions, and how they are protected.

## Testing

How the change will be tested: unit tests, integration tests with Testcontainers, Kafka's isolated
Ursa integration tests, and compatibility tests.

## Alternatives

What else you considered, and why you didn't choose it.

## For a new materializer

Fill in this section when the LIP proposes a materializer, and delete it otherwise. See
[Write a materializer](https://github.com/lakestream-io/ursa/blob/main/docs/developer/materializer-guide.md).

- **Destination:** the table format or store, and the versions you support.
- **Catalog type and configuration:** the proposed `TableCatalogType` name, the `TableCatalog`
  connection keys, and the configuration prefix that operators would use.
- **Commit and replay:** how the materializer commits, and how it avoids writing records twice when a
  task re-runs the same offset range.
- **Schema mapping and evolution:** how Avro, JSON Schema and Protobuf schemas map to the destination,
  and which schema changes it can follow.
- **Failure handling:** which errors fail the task, and what happens to a record that can't be
  written.
- **Testing:** the Testcontainers image for the destination, or how else it will be tested.
- **Code and maintainers:** where the code lives, and who maintains it.
- **Dependencies:** the client libraries the materializer uses, and their licenses.

## General notes
