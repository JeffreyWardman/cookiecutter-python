FROM python:3.10-slim
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y --no-install-recommends \
    ca-certificates \
    build-essential \
    make \
    curl \
    libssl-dev \
    software-properties-common \
    git \
    git-lfs \
    vim \
    sudo \
    libgl1-mesa-glx \
    ffmpeg \
    ninja-build \
    python3-dev && \
    apt-get clean

WORKDIR /app

# Install Python 3.10
RUN add-apt-repository -y ppa:deadsnakes/ppa && \
    apt-get update && \
    apt install -y python3.10 && \
    update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.10 1 && \
    update-alternatives --install /usr/bin/python python /usr/bin/python3.10 1

# Install Poetry
ENV PATH="/root/.local/bin:$PATH"
RUN curl -sSL https://install.python-poetry.org | python -
