# Legacy deployment guide

This file describes an obsolete `infra/docker-compose.yml` workflow. Fybud Deploy reads only the
repository-root `docker-compose.deploy.yml`; it does not clone or read this folder. Do not use these
examples.

Use the current playbook at [../DEPLOY.md](../DEPLOY.md). The live contract is [../AGENTS.md](../AGENTS.md).

Current injection rule: Fybud Deploy injects only `IMAGE_TAG` and allocated `*_HOST_PORT` values.
All application settings, including database URLs and public URLs, are supplied through the Deploy
Environment page.
