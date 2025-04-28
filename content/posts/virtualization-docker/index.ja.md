---
weight: 4
title: "Dockerを完全に理解する"
date: 2025-03-18T00:00:00+09:00
lastmod: 2025-03-18T00:00:00+09:00
draft: false
author: "しぶや"
authorLink: "https://github.com/shibuya-s-eg"
description: "Dockerを完全に理解する。"
images: []
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["Virtualization"]
categories: ["Virtualization"]

lightgallery: true
---

こんにちは、しぶやです。\
学生時代の研究から始まり、社会人になってからも愛用しているDockerについて、気合をいれてまとめようと思います。

## TL;DR

*
*
*

## 0　はじめに

### 0.1　コンテナの歴史

### 0.2　VMとの違い

### 0.3　近年の傾向

## 1　コンテナの仕組み

### 1.1　namespace
### 1.2　cgroup
### 1.3　chroot/rootfs
### 1.4　コンテナの本質
コンテナはプロセス。
initプロセスとPID
ホストから見たとき

## 2　Dockerイメージ

### 2.1　Docker Hub

### 2.2　イメージの構成

Layerの階層構造
再利用性
Union FS


### 2.3　最小化

scratch, Alpine, distroless
思想
attack surfaceの削減
運用

## 3　コンテナセキュリティ

### 3.1　capability

管理者権限を与えずに、最小権限の原則に則り、動作に必要な権限のみを与えるやつです。
以下は「Linuxのアクセス制御を完全に理解する」からの抜粋です。

>

基本的なアクセス制御から復習したい方は「Linuxのアクセス制御を完全に理解する」をお勧めします！

### 3.2　コンテナroot

コンテナ内のrootは？
ユーザ変える必要ある？
--privileged

### 3.3　イメージ

信頼性
Docker Content Trust

## 4　Dockerのユースケースとアーキテクチャ

### 4.1　CI/CD


### 4.2　Kubernetes

### 4.3　環境統一


## 5　Dockerのメリット/デメリット

### 5.1　メリット

環境構築の迅速化
環境の再現性と移植性
リソースの軽量性
ホストを汚さない
アタックサーフェスの削減

### 5.2　デメリット

セキュリティ境界の脆弱性
ホスト依存の可能性
オーバーヘッド

## 6　まとめ

kubernetes thread model
kunernetes atacck tree

## 参考

[1] [docker](https://www.docker.com/)
[2] [コンテナセキュリティ　コンテナ化されたアプリケーションを保護する要素技術 ](https://www.amazon.co.jp/%E3%82%B3%E3%83%B3%E3%83%86%E3%83%8A%E3%82%BB%E3%82%AD%E3%83%A5%E3%83%AA%E3%83%86%E3%82%A3-%E3%82%B3%E3%83%B3%E3%83%86%E3%83%8A%E5%8C%96%E3%81%95%E3%82%8C%E3%81%9F%E3%82%A2%E3%83%97%E3%83%AA%E3%82%B1%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%E3%82%92%E4%BF%9D%E8%AD%B7%E3%81%99%E3%82%8B%E8%A6%81%E7%B4%A0%E6%8A%80%E8%A1%93-Liz-Rice/dp/4295016403)
