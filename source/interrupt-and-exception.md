---
title: 割り込みと例外
date: 2021-03-23
tags: ['Linux', 'OS']
---

# 割り込みと例外
オペレーティングシステムにおける割り込みと例外について学習したため、そのまとめとしてここに整理する。

## Intelプロセッサにおける割り込みと例外
- 割り込みは2種類に分類できる
  - 同期割り込み
    - CPU内の制御回路により生成される
    - 実行中の命令終了時にのみ発生
  - 非同期割り込み
    - クロック信号に合わせて、CPU以外のデバイスが生成する
- Intelプロセッサでは、同期割り込みのことを**例外**、非同期割り込みのことを**割り込み**と呼ぶ

## IRQ (Interrupt Requests)
- 割り込み生成可能なハードウェアコントローラから送出される信号
- ハードウェアコントローラはIRQラインと呼ばれるラインを持っており、IRQラインはプログラマブル割り込みコントローラと呼ばれるハードウェア回路に接続されている

### 割り込みディスクリプタテーブル
- 割り込みや例外のベクタとハンドラの対応を管理するテーブル
- GDTとLDTの構造とほぼ同じ