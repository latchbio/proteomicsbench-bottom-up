# syntax=docker/dockerfile:1.4
FROM python:3.13-slim

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        curl \
        build-essential \
        gcc \
    && rm -rf /var/lib/apt/lists/*

RUN curl -LsSf https://astral.sh/uv/install.sh | sh
ENV PATH="/root/.local/bin:${PATH}"

# Harbor uploads declared artifacts to the same absolute paths in this image.
RUN mkdir -p /workspace /logs/verifier /logs/artifacts

COPY . /tests/

RUN cd /tests && uv pip install --system --no-cache -r requirements.txt
