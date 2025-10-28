# ベースイメージ
FROM ubuntu:22.04

# 必要ツール
RUN apt-get update && apt-get install -y \
    build-essential \
    cmake \
    git \
    curl \
    wget \
    python3 \
    python3-pip \
    unzip \
    pkg-config \
    libssl-dev \
    && rm -rf /var/lib/apt/lists/*

# CPU最適化用の環境変数
ENV CMAKE_C_FLAGS="-march=native -O3"
ENV CMAKE_CXX_FLAGS="-march=native -O3"

# 作業ディレクトリ
WORKDIR /app

# Python仮想環境
RUN python3 -m venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"

# llama.cpp をビルド
COPY llama.cpp/ /app/llama.cpp/
RUN mkdir /app/llama.cpp/build && cd /app/llama.cpp/build && \
    cmake -DLLAMA_CURL=OFF -DLLAMA_CPU_NO_AVX=OFF .. && \
    cmake --build . --config Release

# 作業ディレクトリに戻る
WORKDIR /app