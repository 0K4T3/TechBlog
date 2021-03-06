---
title: 仮想ファイルシステム(VFS)について
date: 2021-03-28
tags: ['Linux']
---

# 仮想ファイルシステム(VFS)について
仮想ファイルシステム(VFS)について学習したため、そのまとめとしてここに整理する。

## 仮想ファイルシステム(VFS)
- Virtual File System
- Linuxにおいて、様々な種類のファイルシステムを透過的に扱うための仕組み
- アプリケーションとファイルシステムの実装との間にある抽象的なレイヤであり、アプリケーションからは操作対象のファイルがどのようなファイルシステムなのかを知る必要がなく操作できる

## 共通ファイルモデル
- VFSを構成する概念の一つで、取り扱うすべてのファイルシステムを透過的に扱うためのモデル
- 共通ファイルモデルを構成するオブジェクト
  - スーパーブロックオブジェクト
    - マウントされたファイルシステムに関する情報を保存するオブジェクト
  - iノードオブジェクト
    - 個々のファイルについての情報を保存するオブジェクト
    - iノード番号割り当てられており、それぞれのファイルを1意に識別する
  - ファイルオブジェクト
    - オープンされているファイルとプロセスのやり取りに関する情報を保存するオブジェクト
    - プロセスがファイルをオープンしている間だけ、カーネルメモリ内に存在する
  - dエントリオブジェクト
    - ディレクトリエントリ(個々のファイル名)と、対応するリンクについての情報を保存するオブジェクト
