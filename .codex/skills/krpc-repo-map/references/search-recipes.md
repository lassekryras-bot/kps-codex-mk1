# Search Recipes

Use these commands as navigation aids. Prefer them for first-pass exploration before broader content searches.

## Find Subsystem Contents

```powershell
rg --files server
rg --files service
rg --files client
rg --files doc
rg --files protobuf
rg --files tools
```

## Narrow To Named Services Or Clients

```powershell
rg --files service/SpaceCenter
rg --files service/UI
rg --files client/python
rg --files client/csharp
```

## Trace Docs, Protocol, And Tooling

```powershell
rg --files doc
rg --files protobuf
rg --files tools/TestServer
rg --files tools/krpctools
rg --files tools/krpctest
```

## Check Build And Change Boundaries

```powershell
rg --files -g 'BUILD.bazel'
rg --files -g 'CHANGES.txt'
rg --files service -g 'BUILD.bazel'
rg --files client -g 'BUILD.bazel'
```

## Find Orientation Anchors

```powershell
rg --files -g 'Development-Guide.md' -g 'Contributing.md' -g 'WINDOWS_BUILDING.md' -g 'KRPC.sln'
```

## Use Content Search Sparingly

Use content search only after identifying the likely subsystem.

```powershell
rg "SpaceCenter" service
rg "TestServer" tools
rg "krpc.proto" -g '*'
```
