FROM pytorch/pytorch:2.5.1-cuda12.4-cudnn9-runtime AS base

# Install project dependencies
# -------------------------------------------------------------------------------------------- #
RUN apt update && apt install -y \
        build-essential \
        pkg-config \
        python3-dev \
        git \
    && apt clean

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
RUN pip install --no-cache-dir ipykernel

# Create an user
# -------------------------------------------------------------------------------------------- #
ENV UID 1000
ENV GID 1000

RUN addgroup --gid ${GID} --system user && \
    adduser --shell /bin/bash --disabled-password --uid ${UID} --system --group user

# ENTRYPOINT
# -------------------------------------------------------------------------------------------- #
USER user
CMD ["bash"]