---
name: krpc-repo-map
description: Outline the kRPC repository, explain subsystem boundaries, and point Codex to the most likely directories and files for investigation. Use when Codex needs to understand where code lives in kRPC, compare server vs service vs client ownership, locate docs or protocol definitions, or quickly map a user request to the right part of the repo before making changes.
---

# kRPC Repo Map

## Overview

Use this skill to orient quickly in `krpc` and to answer navigation questions with repo-true paths. Favor a concise subsystem map, concrete file and directory pointers, and simple search commands over architecture speculation.

Read [references/repo-map.md](references/repo-map.md) for the repo mental model. Read [references/search-recipes.md](references/search-recipes.md) when you need concrete `rg`-based navigation commands.

## Navigation Workflow

1. Classify the request by subsystem before searching.
2. Start from the top-level map: `server`, `service`, `client`, `doc`, `protobuf`, `tools`, `lib`.
3. Narrow to the most likely directory and name the next files or folders to inspect.
4. Summarize findings as:
   - what this area does
   - where to look next
   - what adjacent areas matter
5. Keep the answer path-first and concise unless the user asks for a deeper walkthrough.

## Subsystem Map

- `server`
  - Treat as the in-game C# server plugin.
  - Start at `server/src`.
- `service`
  - Treat as the game-side RPC/service implementations.
  - Look for `service/<ServiceName>/src` and `service/<ServiceName>/test`.
- `client`
  - Treat as the client libraries by language.
  - Map language-specific work to `client/<language>`.
  - Treat `client/serialio` and `client/websockets` as protocol test areas.
- `doc`
  - Treat as the documentation source and generated API-doc inputs.
  - Start with `doc/src` and `doc/api`.
- `protobuf`
  - Treat as the communication schema boundary.
  - Start with `protobuf/krpc.proto`.
- `tools`
  - Treat as the dev and test tooling area.
  - Expect supporting programs such as `TestServer`, `krpctools`, `krpctest`, `ServiceDefinitions`, and `TestingTools`.
- `lib`
  - Treat as the external or local dependency staging area used by builds.
  - Use only as a boundary marker unless the question is specifically about build inputs.

## Search Guidance

- Prefer directory walks and `rg --files` over broad content searches for first-pass orientation.
- Use `BUILD.bazel`, per-component `CHANGES.txt`, `Development-Guide.md`, `Contributing.md`, and `WINDOWS_BUILDING.md` as anchor files when the request is ambiguous.
- Avoid claiming a subsystem owns behavior until you can point to the directory or file that implements it.
- Distinguish repo areas clearly:
  - server core runtime
  - service-specific RPC surface
  - client library implementation
  - docs and generated API docs
  - protocol schema
  - tooling and test harnesses

## Response Shape

- Start with the most likely subsystem.
- Name 2-5 concrete paths to inspect.
- Add 1-3 shell-simple search commands if they help narrow the area.
- Call out one adjacent area only when it changes how the user should reason about the repo.
- Stay focused on understanding and navigation, not build or contribution workflow, unless the user asks for that explicitly.
