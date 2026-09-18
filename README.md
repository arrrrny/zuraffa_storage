# zuraffa_storage

S3/MinIO storage capability for [Zuraffa](https://pub.dev/packages/zuraffa) —
`MinioClient` and the MinIO artifact-upload hooks.

This is an **optional companion package**: it carries the heavyweight `minio`
dependency stack so that core-only consumers stay lean
(issue [#1661](https://github.com/arrrrny/zuraffa/issues/1661)). In zuraffa
≤6.x these APIs lived in `package:zuraffa` itself — see the
[core CHANGELOG](https://github.com/arrrrny/zuraffa/blob/master/CHANGELOG.md)
for the full migration map.

## Features

- `MinioClient` — S3/MinIO object client (bucket management, object
  up/download, presigned URLs)
- `MinIOArtifactHook` — publish build artifacts to MinIO by registering via
  `Zuraffa.registerArtifactHook`
- `MinioUploadHook` — failure-artifact upload wiring for the same hook
  registry

## Install

```bash
dart pub add zuraffa_storage
```

Requires `zuraffa: ^7.0.0`.

## Usage

Enable the capability in your Zuraffa project:

```bash
zfa plugin enable storage
```

Then import the surface you need:

```dart
import 'package:zuraffa_storage/zuraffa_storage.dart';
```

## Development

This repository is a standalone split from the core `zuraffa` monorepo
(issue [#1690](https://github.com/arrrrny/zuraffa/issues/1690) §4) with full
git history preserved. Its `pubspec.yaml` declares a hosted
`zuraffa: ^7.0.0` constraint plus a `dependency_overrides` entry resolving
`zuraffa` to the local core checkout — so a sibling checkout of
[arrrrny/zuraffa](https://github.com/arrrrny/zuraffa) at `../zuraffa` is
required for `dart pub get`, `dart analyze`, and `dart test`:

```text
~/Developer/
├── zuraffa/          # core checkout (any branch)
└── zuraffa_storage/  # this repository
```

CI provides that sibling checkout automatically. See
[PUBLISH.md](PUBLISH.md) before releasing.

## Links

- [Repository](https://github.com/arrrrny/zuraffa_storage)
- [Issue tracker](https://github.com/arrrrny/zuraffa_storage/issues)
- [Zuraffa core](https://github.com/arrrrny/zuraffa) ·
  [zuraffa on pub.dev](https://pub.dev/packages/zuraffa)
