ARG alpine_version \
    node_version

FROM gitlab-registry-internal.spirit-dev.net/infrastructure/docker/alpine:${alpine_version}

ARG alpine_version \
    node_version

LABEL alpine_version="${alpine_version}" \
    node_version="${node_version}" \
    spiritdev_official="yes" \
    layer="1" \
    from="gitlab-registry-internal.spirit-dev.net/infrastructure/docker/alpine" \
    maintainer="bordat.jean@gmail.com"

RUN apk add --no-cache nodejs=18.20.1-r0 npm=9.6.6-r0 git=2.40.4-r0 && \
    npm install -g semantic-release @semantic-release/gitlab @semantic-release/git @semantic-release/changelog @google/semantic-release-replace-plugin
