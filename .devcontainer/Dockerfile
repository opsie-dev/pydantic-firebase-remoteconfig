FROM mcr.microsoft.com/devcontainers/python:3.12-bookworm

ENV PIP_ROOT_USER_ACTION=ignore
RUN apt-get update
RUN apt-get -y install \
    build-essential \
    ca-certificates \
    cmake \
    lsb-release \
    ninja-build \
    python3-dev \
    wget
# NOTE: force libarrow-dev to be the same version as pyarrow binding.
RUN wget https://packages.apache.org/artifactory/arrow/$(lsb_release --id --short | tr 'A-Z' 'a-z')/pool/bookworm/main/a/apache-arrow-apt-source/apache-arrow-apt-source_15.0.2-1_all.deb
RUN apt install -y -V ./apache-arrow-apt-source_15.0.2-1_all.deb
RUN apt update
RUN apt install -y -V libarrow-dev
RUN pip install uv
RUN rm apache-arrow-apt-source_15.0.2-1_all.deb

ENTRYPOINT ["bash"]
