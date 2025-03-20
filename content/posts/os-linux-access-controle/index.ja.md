---
weight: 4
title: "Linuxのアクセス制御を完全に理解する"
date: 2025-03-20T00:00:00+09:00
lastmod: 2025-03-20T00:00:00+09:00
draft: false
author: "しぶや"
authorLink: "https://github.com/shibuya-s-eg"
description: "Linuxのアクセス制御を完全に理解する。"
images: []
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["OS"]
categories: ["OS"]

lightgallery: true
---

こんにちは、しぶやです。\
Linuxのアクセス制御の理解がかなり浅いと気づいたので、これを機にLinuxのアクセス制御を「完全に理解」していきたいと思います。\

## TL;DR

*
*
*

## 0　はじめに

Linuxに限った話ではないですが、ファイルについて理解することは非常に重要だと思います。
というのも、以下のような有名な考え方があります。

> Linuxでは全てをファイルとして扱うようになっています。[LPI-JAPAN](https://lpi.or.jp/lpic_all/linux/intro/intro10.shtml)

僕がLinuxを好きである一番の理由です。
Linuxがかっこ良いからというわけではなく、すべてをファイルとして扱ってくれるLinuxは理解しやすいのです。
Windows等は複雑すぎて僕にはまだ理解できない部分がほとんどです。いずれ勉強したい。。

話を戻して、本記事ではLinuxにおけるアクセス制御、すなわちファイルのアクセス制御について「完全に理解」していきたいと思います。
「少し分かる」レベルの人は軽く読み飛ばしてください。


※ 本記事では以下の環境で動作検証をしています。
* OS：Ubuntu 24.04.1 LTS
* ルートファイルシステム：ext4
* ホスト：AWS EC2

## 1　Linuxにおけるアクセス制御の基本

まずは、基本の復習からです。

### 1.1　基本のパーミッション

Linuxにおけるファイルパーミッションは以下のような形をしています。

* drwxrwxrw

これは、以下の4つに分けられます。

* d + rwx + rwx + rwx (= drwxrwxrwx)
    * d---------\
    ファイルの種類を表す。
        * - ... ファイル
        * l ... シンボリックリンク
        * d ... ディレクトリ
        * etc.
    * -rwx------\
    所有ユーザの権限を表す。
        * - ... 権限なし
        * r ... 読み込み権限
        * w ... 書き込み権限
        * x ... 実行権限
    * ----rwx---\
    所有グループの権限を表す。
    読み方は所有ユーザと同様。
    * -------rwx\
    その他のユーザの権限を表す。
    読み方は所有ユーザと同様。

それでは、実際のファイルを見てみましょう。

{{< image src="echo.png" width="400px" height="300px" caption="echo" >}}

echo

{{< admonition note "chmod, chown" >}}
以下の2つはよく使うコマンドですね。
* chmod
    * ファイルのアクセス権限を変更する。
    * 例：chmod ./hoge.txt 644\
    （hoge.txtを所有者のみ読み込み書き込みok、所有グループ、その他のユーザは読み込みのみokに変更）
* chown
    * ファイルの所有者を変更する。
    * 例：chown hoge:ghoge ./hoge.txt\
    （hoge.txtの所有者をhogeに、所有グループをghogeに変更）
{{< /admonition >}}


### 1.2　その他パーミッション

setuid, setgid, stickybit

### 1.3　権限昇格

### 1.4　コピー時の動作

### 1.5　子プロセスへの継承


## 2　Linuxにおけるアクセス制御の深堀

### 2.1　ファイルシステム


### 2.2　VFS

vfs, inode

### 2.3　ファイル操作の流れ

app - syscall -> vfs -fs_call-> fs

strace

### 2.4　カーネルの権限管理

capability, getcap, getpcaps
カーネルパラメータ

## 3　その他のアクセス制御

facl
selinux

## 4　まとめ


ファイルパミッションの基本、setuid, setgid, そもそものuid, gid, すべてファイルである, コピー時の動作、ファイル管理のビット列、
strace, getpcaps, capability, getcap, カーネルパラメータ、権限昇格、facl


## 参考

[1] [ClamAV](https://www.synology.com/)
[2] [WIKIPEDIA Antivirus software](https://en.wikipedia.org/wiki/Antivirus_software)
[3] [Trellix 脅威対策の主な内容]（https://docs.trellix.com/ja-JP/bundle/endpoint-security-10.6.0-threat-prevention-product-guide-windows/page/GUID-7939E36B-8FC4-42F4-BE70-46AB2B9B0954.html）
