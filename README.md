# Immich on WSL (Robust Setup)

**WSL2 (Ubuntu Base)**Docker Compose**NVIDIA GPU Support**Tailscale VPN**MTU 1200 Fix**

Windows 11 + WSL2 環境における、堅牢なつもりの Immich サーバー構築ガイド

## Overview

本プロジェクトは、Windows 11 上の WSL2 環境において、**完全に隔離された最小構成の Ubuntu Base**を使用し、**NVIDIA GPU による機械学習**と**Tailscale によるセキュアなリモートアクセス**を実現する Immich サーバーの構築手順書である。

## Features

- **Minimalist Base:** Microsoft Store 版ではなく、Ubuntu Base (Rootfs) を使用し不要なアプリを排除。
- **GPU Acceleration:** NVIDIA Container Toolkit を導入し、Immich の機械学習（顔認識等）を RTX GPU で高速化。
- **Hybrid Storage:** データベースは高速な NVMe SSD (WSL 内) に、大容量画像データは物理 HDD (NTFS マウント) に配置。
- **Network Optimization:** Tailscale VPN 経由でのパケット詰まりを防ぐため、MTU/MSS を最適化済み。
- **Automated:** Windows タスクスケジューラによる、画面レスでの自動起動スクリプト付属。

## Installation Guide

構築は以下の 2 段階で構成されている。HTML ファイルをダウンロードし、ブラウザで開いて実行すること。

- [Phase 1: 環境構築編(System Setup)](https://syameimarukoa.github.io/Immich-on-WSL/index.html)
- [Phase 2: 展開・設定編(Deployment)](https://syameimarukoa.github.io/Immich-on-WSL/deployment.html)

※ 上記のリンクは、同じフォルダに `index.html` と `deployment.html` が存在する場合に機能する。
