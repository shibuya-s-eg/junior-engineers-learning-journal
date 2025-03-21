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
        * l ... リンク
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

上記から、echoは管理者のみが書き換えも可能、他は読み込みと実行のみが可能です。
実際に、書き換えを行おうとすると以下のようにエラーになります。

{{< image src="echo.png" width="400px" height="300px" caption="echo" >}}

また、実行には読み込みが必要です。では、実行権限は読み込み権限を包含しているのでしょうか？
読み込み権限なしに、実行権限だけを持つようなパターンはあるのでしょうか？これについては、次節で見ていきたいと思います。

ここでは、アクセス権限意外の部分を復習してみましょう。

* リンク数

アクセス権限の横にある数字はリンク数です。
Windowsでいうショートカットに近いものです。

{{< image src="echo.png" width="400px" height="300px" caption="echolink" >}}

ここでは、実際にechoを呼ぶecholinkを作成しています。
echolinkからechoが呼び出されていることがわかります。

{{< admonition note "シンボリックリンクとハードリンク" >}}
Linuxのリンクにはシンボリックリンクとハードリンクがあります。
Windowsのショートカットに近いものはシンボリックリンクの方です。
* シンボリックリンク\
    * ファイルやディレクトリへのパス情報
    * 参照先が消えるとリンクが使えなくなる。hhhhhhhhhhhhhhh
* ハードリンク\
    * 元ファイルと同じinodeを指す\
    → もとのファイルが消えても、ハードリンクからはデータにアクセス可能\
    → リンク先の変更は元ファイルにも影響\
    ※ これについては、2.2 VFSで詳しく話します。
{{< /admonition >}}

* 所有者、所有グループ
* 最終更新日時
* サイズ
* ファイル名

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

{{< admonition tip >}}
chmodで存在しないユーザを指定したらどうなのでしょう。

{{< image src="chmod.png" width="400px" height="300px" caption="chmod" >}}

と言われ怒られるようです。
{{< /admonition >}}

### 1.2　その他パーミッション

その他のパーミッションについて見ていきます。

* setuid, setgid

setuid, setgidは実行時に所有者の権限で実行するためのものです。
passwdを例に見ていきましょう。

{{< image src="passwd.png" width="400px" height="300px" caption="passwd" >}}


{{< admonition note "uid・gid" >}}
ユーザやグループのための一意の識別子です。
ユーザの情報は"/etc/passwd"に、グループの情報は"/etc/group"にあります。

<div class="image-row">
    {{< image src="etc-passwd.png" width="400px" height="300px" caption="/etc/passwd" >}}
    {{< image src="etc-group.png" width="400px" height="300px" caption="/etc/group" >}}
</div>

ユーザIDは1000以上が割り当てられます。rootは0です。
{{< /admonition >}}

{{< admonition note "shadow" >}}
先程の"/etc/passwd"には実際のパスワードは入っていませんでした。
これは、"/etc/passwd"はすべてのユーザから読み込まれてしまうため、パスワードが他のユーザに漏洩してしまうからです。
実際のパスワードは"/etc/passwd"に保存されています。

{{< image src="etc-shadow.png" width="400px" height="300px" caption="/etc/shadow" >}}

構造：

{{< /admonition >}}

{{< admonition note "setuidの危険性" >}}

{{< /admonition >}}

* スティッキービット

スティッキービットはディレクトリに適用するものです。
スティッキービットが適用されたディレクトリはすべてのユーザーがファイルの作成・書き込み可能です。
スティッキービットの特徴は**ファイルの削除は所有者のみが可能**ということです。
/tmpなどはステッキービットが適用されている例です。
実際にスティッキービットを試してみましょう。

{{< image src="stickybit" width="400px" height="300px" caption="stickybit" >}}

スティッキービットに作成されたファイルの権限はになります。

また、ファイル所有者以外のユーザはファイルの読み込み、書き込みは可能ですが、削除をしようとすると怒られます。

では、ファイルのアクセス権限とディレクトリに適用されたスティッキービットはどちらが優先されるのでしょう？

{{< image src="access-rights-vs-stickeybit.png" width="400px" height="300px" caption="アクセス権とスティッキービット" >}}

{{< admonition tip >}}
スティッキービットはファイルの削除は不可能ですが、書き込みは可能です。
ここで、他のユーザにファイル内容をすべて削除されてしまうと、ファイルを削除されたような状態になります。
スティッキービットは一体何のためにあるのでしょうか？

結論、スティッキービットは誤って他人のファイルを削除することを防止するためのものです。
ファイルの中身を書き換えられてしまうことに変わりはないので、それを防ぐには通常のアクセス権管理が必要です。
{{< /admonition >}}

### 1.4　sudo

1.3でsetuid, setgidを学んだところで、sudoも復習しておきましょう。

sudoは管理者権限でコマンドを実行するために利用されます。
sudoの管理を行っているのは"/etc/sudoers"です。実際に見てみましょう。

{{< image src="sudoers.png" width="400px" height="300px" caption="sudoers" >}}

alice ALL=(ALL:ALL) ALL
【ユーザー名】 → 権限を与えるユーザー
ALL → すべてのホストでコマンドを実行可能
(ALL:ALL) →
1つ目の ALL → sudo 実行時に任意のユーザーに切り替え可能
2つ目の ALL → sudo 実行時に任意のグループに切り替え可能
ALL → すべてのコマンド実行可能

それでは、sudoを試してみましょう。

{{< image src="hello.png" width="400px" height="300px" caption="hello" >}}

sudoerに書いたあとはsudoで実行できるようになっています。


{{< admonition tip >}}
"/etc/sudoers"を編集する際は、"visudo"コマンドが推奨されています。
これには以下のような機能があるからのようです。
* 保存時に構文エラーのチェックを行う
* 同時編集を禁止する
* （"/etc/sudoers"自体の）パーミッションの自動保護
* "/etc/sudoers"の破壊防止（rootに戻れなくなることを防止）
{{< /admonition >}}

### 1.5　コピー時の動作

1.1~1.3ででファイルのアクセス権限について復習しました。
では、ファイルをコピーした際はどのような挙動をするのでしょうか。

デフォルトのcpコマンドの動作は以下です。
* コピー元の読み取り権限が必要
* コピー元のアクセス権の設定をコピー
* 所有者、所有グループはコピーを行った人のものに変更

"-p"オプションをつけると、アクセス権に加え、所有者やタイムスタンプなども完全にコピーされます。

{{< image src="copy.png" width="400px" height="300px" caption="copy" >}}

リンクファイル作成時はどうでしょうか？

* シンボリックリンク\
シンボリックリンク自体は独立したファイルとして扱われます。※ シンボリックリンクはただのパスのようなものであるため。
    * 所有者はリンク作成者
    * パーミッションは"lrwxrwxrwx"\
    リンク先のファイルを操作する際にそちらに左右されるため、リンクファイル自体にパーミッションをもたせる必要がない。
* ハードリンク\
    * 所有者、パーミッション等はコピー元ファイルと同じ

{{< image src="link.png" width="400px" height="300px" caption="link" >}}


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
