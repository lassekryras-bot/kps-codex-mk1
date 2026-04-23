# kRPC Repo Map

Use this file for the repo mental model when answering "where does this live?" or "which part of kRPC owns this?" questions.

## Top-Level Areas

- `server/src`
  - Hold the in-game C# server implementation.
  - Start here for core server behavior and shared runtime logic.
- `service/<ServiceName>/src`
  - Hold game-side service implementations that expose RPCs.
  - Use `service/<ServiceName>/test` when a service has targeted tests.
- `client/<language>`
  - Hold each client library implementation.
  - Common language directories include `csharp`, `cpp`, `java`, `lua`, and `python`.
- `client/serialio` and `client/websockets`
  - Hold protocol-specific test areas rather than normal language clients.
- `doc/src`
  - Hold documentation source content.
- `doc/api`
  - Hold API-doc inputs and generation-related material.
- `protobuf/krpc.proto`
  - Define the protocol schema boundary.
- `tools/TestServer`
  - Hold the standalone server used for communication and integration-style testing without the game.
- `tools/krpctools`
  - Hold Python tooling such as client and doc generation support.
- `tools/krpctest`
  - Hold Python-based testing helpers for interaction with KSP.
- `tools/ServiceDefinitions`
  - Hold tooling for generating service definition JSON from service DLLs.
- `tools/TestingTools`
  - Hold the game-side testing helper service used by automated test workflows.
- `lib`
  - Hold local dependency inputs such as KSP and Mono-related links or copies used by builds.

## Orientation Anchors

- `Development-Guide.md`
  - Use as the main repository structure and tooling overview.
- `Contributing.md`
  - Use for branch, changelog, testing, and PR workflow expectations.
- `WINDOWS_BUILDING.md`
  - Use when the question is specific to Windows setup constraints.
- `BUILD.bazel`
  - Use to understand top-level build targets and boundaries.
- `KRPC.sln`
  - Use to understand the C# solution shape and IDE-oriented entrypoints.
- Per-component `CHANGES.txt`
  - Use to identify user-visible changes and component ownership.

## Fast Classification Hints

- Map "core runtime", "plugin", or "server internals" to `server`.
- Map "SpaceCenter", "UI", "RemoteTech", or named RPC groups to `service/<ServiceName>`.
- Map language SDK questions to `client/<language>`.
- Map docs generation or site questions to `doc`.
- Map message/schema/protocol questions to `protobuf`.
- Map test harnesses, generators, and standalone utilities to `tools`.

## Adjacent Areas To Mention

- Mention `protobuf/krpc.proto` when a server, service, or client question touches wire format.
- Mention `doc` when a code question also changes user-facing RPC documentation.
- Mention `tools/TestServer` or `tools/krpctest` when the user is tracing tests rather than product code.
- Mention `BUILD.bazel` when a feature crosses component boundaries and the user may need to inspect target wiring.
