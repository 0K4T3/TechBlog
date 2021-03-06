---
title: フォーマット文字列攻撃
date: 2021-03-12
tags: ['C', 'printf', 'CTF']
---

# フォーマット文字列攻撃
フォーマット文字列攻撃について学習したため、そのまとめここに整理する。

## フォーマット文字列攻撃とは
- printfの引数として与える、フォーマット文字列が外部から指定可能な際に成立する。
    - 入力値をそのまま引数として使用している場合など

## 主な攻撃内容
- %xや%pを用いた、メモリ内容の出力
    - printf関数は%xや%pを指定することで、フォーマット文字列が存在するスタックの内容を出力することができる
- %nを用いた、メモリの書き換え
    - printf関数は%nを指定することで、それまで出力した文字数をメモリに書き込むことができる (フォーマット文字列以降の引数で、書き込むアドレスを指定)
    - %3$nなどのように指定することで、スタックの上から任意の位置を指定して書き込むことも可能
    - %nは4byte単位での書き込みだが、%hn(2byte), %hhn(1byte)も指定可能 (hはharfから？)