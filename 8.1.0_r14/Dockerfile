FROM droidfivex/android-build-environment:oreo

LABEL maintainer="droidfivex <droidfivex@gmail.com>"

ENV \
    manifest_repository=https://android.googlesource.com/platform/manifest \
    manifest_branch=android-8.1.0_r14

RUN mkdir -p $manifest_branch
WORKDIR $manifest_branch

RUN \
    yes | repo init \
        --depth=1 \
        --quiet \
        --manifest-url=$manifest_repository \
        --manifest-branch=$manifest_branch && \
    repo sync \
        --jobs=$(cat /proc/cpuinfo | grep processor | wc -l) \
        --network-only \
        --current-branch \
        --no-tags \
        --quiet
