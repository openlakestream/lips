# Contributing a LIP

This guide explains when a change needs a Lakestream Improvement Proposal (LIP), and how a LIP is
written, reviewed and accepted. To contribute code, see the contributing guide of the component:
[Ursa](https://github.com/lakestream-io/ursa/blob/main/CONTRIBUTING.md) or
[Ursa for Apache Kafka](https://github.com/lakestream-io/kafka/blob/HEAD/CONTRIBUTING.md).

> **Using an AI assistant?** Read the [AI policy](https://github.com/lakestream-io/ursa/blob/main/AI_POLICY.md) first.
> **Are you a coding agent?** Start with [AGENTS.md](AGENTS.md).

## When you need a LIP

A LIP is for a change that other people build on or operate against. Most LIPs change an interface:
an API, an SPI, a format, or a configuration surface. Write the LIP for Lakestream as a whole, and
list what changes in each component, even when only one component changes.

### Lakestream API and Ursa

You need a LIP for:

- new or changed public types in `lakestream-api`
- changes to an SPI contract, such as `TableMaterializer` or `TableMaterializerFactory`
- changes to the on-object or WAL formats, or to serialized field numbers and identifiers
- every new materializer, because registering one adds a `TableCatalogType` to `lakestream-api`
  (see [Write a materializer](https://github.com/lakestream-io/ursa/blob/main/docs/developer/materializer-guide.md))

### Ursa for Apache Kafka (UFK)

You need a LIP for:

- changes to what a Kafka client can observe on a diskless topic: produce, fetch and offset behavior,
  errors, or limits
- new or changed configuration keys for diskless storage (the `ursa.*` broker, controller and topic
  configurations)
- changes to the contract between Kafka and Lakestream: how a topic maps to a stream, the stream
  properties Kafka writes, and the payload Kafka writes to the write-ahead log (WAL). Ursa's Kafka
  codecs and every materializer read these.
- changes to how the controller creates, grows, deletes or cleans up diskless topics

Changes to how classic topics behave usually belong upstream, as a
[KIP](https://cwiki.apache.org/confluence/display/KAFKA/Kafka+Improvement+Proposals) in Apache Kafka.
If a change can't avoid touching classic behavior, it needs a LIP.

### When you don't

You don't need a LIP for bug fixes, internal refactoring, performance work that keeps behavior and
formats unchanged, tests, or documentation. If you're not sure, ask in the place where step 1 below
says to start.

## How it works

1. **Start a discussion** in the repository of the component you want to change. Describe the
   problem: what you're trying to build, and what gets in the way today. The first step is agreeing
   that the problem is worth solving.
   - For `lakestream-api` or Ursa, open a thread in Ursa's
     [Discussions: Ideas](https://github.com/lakestream-io/ursa/discussions/categories/ideas). For a
     new materializer, open a
     [New materializer proposal](https://github.com/lakestream-io/ursa/issues/new?template=materializer_proposal.yml)
     issue instead.
   - For Ursa for Apache Kafka, open a thread in Kafka's
     [Discussions: Ideas](https://github.com/lakestream-io/kafka/discussions/categories/ideas).
   - If the change spans components, start in the repository that owns the interface you're changing,
     usually Ursa, which holds `lakestream-api`. Link to the thread from the other components.
2. **Write the LIP.** Copy [TEMPLATE.md](TEMPLATE.md) to `proposals/LIP-NNN-Short-Title.md`. Use the
   highest existing LIP number plus one. If two open pull requests pick the same number, the one
   merged second renumbers. Add the LIP to the index in [README.md](README.md).
3. **Open a pull request** in this repository that adds the file with the status *Proposed*, and link
   it from the discussion. Keep the design review on the pull request, so the document and its
   review stay together.
4. **Review.** The code owners of this repository review it, together with a maintainer of each
   component the LIP changes. Mention those maintainers on the pull request. Expect questions about
   compatibility, rollback, alternatives and testing.
5. **Merge.** Merging the pull request accepts the LIP. Implementation pull requests, in whichever
   repository, link to it. A LIP that isn't accepted is closed, with the reasons recorded on the
   pull request.
6. **Keep the status current** as the work lands. Update the header of the LIP and its row in the
   index in the same pull request. The README lists [what each status means](README.md#status).

## Writing a good LIP

- Lead with the problem. A reader should understand why the change matters before reading the
  design.
- Say what changes in each component, and whether one component has to ship before another.
- Be explicit about compatibility. Say what happens on upgrade and on rollback, and call breaking
  changes breaking.
- Keep it as short as the change allows. Link to existing documentation instead of repeating it. Use
  absolute URLs for links outside this repository: a relative link only works inside it.
- Record the alternatives you rejected, and why. They stop the same debate from happening twice.

## Commits and pull requests

The rules are the same as in the component repositories. Ursa's
[contributing guide](https://github.com/lakestream-io/ursa/blob/main/CONTRIBUTING.md#commits) has the
details.

- Sign off every commit with `git commit -s`. The sign-off certifies the
  [Developer Certificate of Origin](https://developercertificate.org/).
- If an AI tool helped meaningfully, add an `Assisted-by:` trailer to the commit, and fill in the
  *AI assistance* section of the pull request template.
- Pull requests are squash-merged, so the pull request title becomes the commit subject on `main`.

## License

LIPs are licensed under the [Apache License 2.0](LICENSE), and so is your contribution.
