ARG alpine_version \
    node_version

FROM gitlab-registry-internal.spirit-dev.net/infrastructure/docker/alpine:${alpine_version}
# FROM alpine:3.21.2

ARG alpine_version \
    node_version

LABEL alpine_version="${alpine_version}" \
    node_version="${node_version}" \
    spiritdev_official="yes" \
    layer="1" \
    from="gitlab-registry-internal.spirit-dev.net/infrastructure/docker/alpine" \
    maintainer="bordat.jean@gmail.com"

RUN apk add --no-cache nodejs=22.15.1-r0 npm=10.9.1-r0 git=2.47.3-r0 && \
    npm install -g semantic-release \
    @semantic-release/gitlab \
    @semantic-release/git \
    @semantic-release/changelog \
    semantic-release-replace-plugin \
    @semantic-release/exec \
    @semantic-release/commit-analyzer
