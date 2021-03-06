---
title: Linuxにおけるファイルシステムについて
date: 2021-03-21
tags: ['Linux', 'filesystem']
---

# Linuxにおけるファイルシステムについて
Linuxにおけるファイルシステムについて学習したため、そのまとめとしてここに整理する。

## ファイルシステムとは
- ディスク上のデータを、ファイル・ディレクトリなどの概念により構造的に管理するための仕組み
- ファイル名によるデータの管理や、ディレクトリによる階層的なデータの管理などといった仕組みを提供する

## Linuxで主に使用されるファイルシステム
- ext2・ext3・ext4
  - ext4が現在のLinuxで使用されるデファクトスタンダードのファイルシステムとなっている
  - 3つとも互換性があり、ext4からext3、ext3からext2への変換も可能

## スーパーブロック
- ファイルシステム自体のサイズやinodeの総数など、パーティション全体の情報を持つブロック

## inode領域
- すべてのinodeがテーブル形式で管理されている領域

## データブロック
- ファイルやディレクトリの実際のデータが保存されている領域

## inode
- ファイル・ディレクトリと一対一で結びつく、一意なデータ構造
- ファイルタイプや所有者番号、実際にデータが管理されているディスク上の位置やサイズなどといった情報を保持している

## ディレクトリの実態
- ファイルと同様にinodeが割り当てられinode領域上に管理され、データブロック内に実際のデータが保存されている
- 保持しているデータは、自身の子であるファイルのファイル名とinode番号のペアである
