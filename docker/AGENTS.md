# docker AGENTS.md

## Purpose
Builds, tests, and packages official container images for semantic-release automation used across CI/CD pipelines.

## Ownership
- `docker/Dockerfile`: Container image definition, Alpine base, pinned Node.js/npm/git packages, and semantic-release CLI and plugins.
- `docker/test.yaml`: Container structure tests validating image labels, Alpine version, and Node.js execution.
- `docker/.gitlab-ci.yml`: GitLab CI stages for Kaniko-based container build and publish.

## Local Contracts
- Base image must reference `gitlab-registry-internal.spirit-dev.net/infrastructure/docker/alpine:${alpine_version}`.
- Mandatory image labels: `alpine_version`, `node_version`, `spiritdev_official="yes"`, `layer="1"`, `from`, and `maintainer`.
- Pin exact package versions in `apk add` (e.g. Node.js, npm, git).
- Keep `test.yaml` schema and test assertions synchronised with labels and installed tools.

## Work Guidance
- Build container locally: `make build` or `docker build -f docker/Dockerfile --build-arg alpine_version=latest -t semantic-release:latest .`
- Interactive debug: `make run`
- Compose operations: `make compose-build`, `make compose-run`, `make compose-exec`

## Verification
- Dockerfile linting: `hadolint docker/Dockerfile`
- Container structure validation: `container-structure-test test --image semantic-release:latest --config docker/test.yaml`

## Child DOX Index
(No subtrees)
