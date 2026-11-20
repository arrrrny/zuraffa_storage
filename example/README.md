# zuraffa_storage

MinIO-backed artifact storage for Zuraffa — a thin client plus upload hooks
that persist generated artifacts to an S3/MinIO bucket.

## Upload an artifact

```dart
import 'package:zuraffa_storage/zuraffa_storage.dart';

Future<void> main() async {
  final client = MinioClient(
    endpoint: 'localhost:9000',
    accessKey: 'minioadmin',
    secretKey: 'minioadmin',
  );

  await client.uploadObject(
    bucket: 'artifacts',
    object: 'build/app.tar.gz',
    bytes: fileBytes,
  );
}
```

## Persist artifacts via the upload hook

```dart
import 'package:zuraffa_storage/zuraffa_storage.dart';

final hook = MinioUploadHook(client, bucket: 'artifacts');
await hook.onArtifact(artifact);
```