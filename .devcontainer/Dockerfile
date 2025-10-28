# .devcontainer/Dockerfile
FROM ubuntu:22.04

# 必要なパッケージをインストール
RUN apt-get update && apt-get install -y \
    build-essential \
    cmake \
    python3 \
    python3-pip \
    git \
    wget \
    vim \
    && apt-get clean

# llama.cppビルド用
RUN apt-get install -y clang make

# Python仮想環境ツール
RUN pip install --upgrade pip uv

# 作業ディレクトリ
WORKDIR /app
