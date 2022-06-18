FROM us-docker.pkg.dev/cookies-eng/public/base/codespaces:v1k

ENV SHELL=zsh \
    HOME=/home/dev \
    DEVCONTAINER=yes

USER dev
WORKDIR /home/dev

# install container-specific Bazel settings
COPY .devcontainer/container.bazel.rc /home/dev/.bazelrc
