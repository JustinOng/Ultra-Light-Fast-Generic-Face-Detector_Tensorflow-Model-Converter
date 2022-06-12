# Use tensorflow image here just for dependencies, though we later reinstall tensorflow==2.3.1
FROM tensorflow/tensorflow:2.8.1-gpu

COPY requirements.txt /tmp/pip-tmp/requirements.txt
RUN pip3 --disable-pip-version-check --no-cache-dir install -r /tmp/pip-tmp/requirements.txt \
  && rm -rf /tmp/pip-tmp

RUN (apt-get update --allow-unauthenticated || true) && export DEBIAN_FRONTEND=noninteractive \
  && apt-get -y install --no-install-recommends ffmpeg libsm6 libxext6 git

ARG USERNAME=user
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN groupadd --gid $USER_GID $USERNAME \
  && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME -s /bin/bash

USER user
