# Infrastructure

Configuration files used by `docker-compose.yml` for local development.

| Path | Used by | Holds |
| --- | --- | --- |
| `seaweedfs/s3.json` | `storage` service | The S3 access key and secret for local development only |

Nothing in this folder is used in staging or production. Real credentials live in the host's secret store.
