# 執筆検討メモ


以下、今後執筆を検討しているものたちです。

* :(fas fa-brands fa-ubuntu fa-fw): OS
    * パッケージマネージャ
* :(fas fa-solid fa-network-wired fa-fw): Network
    * OSPF
    * RIP
    * STP
* :(fas fa-solid fa-shield-halved fa-fw): Security
    * 堅牢化
    * ClamAV
    * Suricata
* :(fas fa-solid fa-database fa-fw): Database, Storage
    * NAS
    * Postgres
    * OracleDB
* :(fas fa-chart-column fa-fw): Data Science
    * 古典学習
* :(fas fa-solid fa-cloud fa-fw): Cloud
    * AWSサービス
* :(fas fa-solid fa-server fa-fw): Virtualization
    * Proxmox
    * K8s
    * Docker
* :(fas fa-solid fa-microchip fa-fw): Hardware
    * メモリ
* :(fas fa-solid fa-sitemap fa-fw): System Design, Deployment, and Management
    * ガイドライン
    * フレームワーク
* :(fas fa-solid fa-coins fa-fw): Finace
    * お金の流れ
* :(fas fa-solid fa-book fa-fw): Basic Theory
    * 物理
* :(fas fa-solid fa-circle-user fa-fw): Others
    * 1年目の感想


メモ

* 基礎
    * サイバーセキュリティと情報セキュリティ
    * 物理的セキュリティと論理的セキュリティ
    * CIA
    * 付加的な特性

* 制度/フレームワーク/ガイドライン
    * ISMS
        * 27000シリーズ
        * 27001
        * 27002
        * 27018
        * クラウドセキュリティ認証
    * JIS Q
        * 27017
        * 20000
        * 15001
        * 27014
    * ISMAP
    * SOC保証制度
    * SIM3
    * cmmc
    * cmmi
    * samm
    * NIST SP 800-40
    * 金融庁 財務報告に関わる内部統制の評価及び監査に関する実施基準
    * 金融庁 サイバーセキュリティ対策のための統一基準群
    * SCAP
    * SOAR
    * サイバーキルチェーン
    * MITER
    * NIST サイバーセキュリティフレームワーク
    * コンピュータセキュリティインシデントガイド
    * 証拠保全のやつ


* セキュリティソリューション
    * CASB

* 開発手法
    * ウォークスルー
    * トップダウン
    * ボトムアップ
    * サンドイッチ
    * 並行シミュレーション
    * アジャイル
    * ウォーターフォール
    * テスト駆動開発
    * DEVOPS
    * カオスエンジニアリング
    * XP
    * 適応型ソフトウェア開発
    * フィーチャ駆動型開発

* ソフトウェア品質
    * 形式手法
    * インスペクション
    * ホワイトボックス
    * ブラックボックス

* サイドチャネル攻撃
    * タイミング攻撃
    * 故障利用攻撃
    * 電力解析攻撃
    * 破壊攻撃

* Webセキュリティ
    * 攻撃
        * クロスサイトスクリプティング
        * クロスサイトリクエストフォージェリ
        * HTTPヘッダインジョクション
        * OSコマンドインジェクション
        * セッションハイジャック
        * マンインサミドル
        * Pass The Hash
    * 防御
        * CSRFトークン
        * samesite属性
        * EV SSL見分け
        * HSTS
        * Keep-Alive
        * キャッシュコントロール
        * トランザクション認証
            * これって同じ秘密鍵的なものをサーバでも持っている感じ?

* 無線LANセキュリティ
    * WPA3
    * WPA2 Enteprise, Personal
    * Enhanced Open
    * EAP
        * MD5
        * TLS
        * TTLS
        * TOPTP
        * PEAP
    * ジャミング攻撃
    * 隠れ端末問題:https://xtech.nikkei.com/atcl/nxt/column/18/00247/041000003/
        * 他のキャリアを見つけられない
        * そもそものCSMA/CAは

* セキュリティ団体
    * CRYPTOREC
    * NICT
        * ダイダロス
        * NOTICE
        * 総合テストベッド
    * IPA

* DoS
    * synflood
    * http post flood
    * ボットネット
    * optimisticack, duplicate ack, partial ack: firewallとかの送信順序をどうこうするやつ
    * smurf攻撃
    * メールボム


* DNS
    * CAAレコード
    * RSIGレコード
    * SPFレコード
    * DNS SEC
    * TSIG
    * カミンスキー攻撃
    * SPF
    * nslookup, digが行っていること。通信の中身
    * DNSアンプ攻撃
    * DNSリフレクタ攻撃
    * DNSSECは権威DNSとキャッシュDNSの間、クライアントとの間はdns over tlsとか
    * キャッシュポイズニングとID的なやつ
    * ポートランダマイゼーション　

* メール
    * PGP
    * M/MIME
    * SMTP Auth
    * SMTP 587
    * APOP
    * POP3
    * IMAPS
    * SMTP Submission
    * OP25B
    * IP25B
    * メールの仕組み・構成
    * フィッシングについて考える
    * mxレコードとaレコードがどう利用されているのか
    * 中継するサーバは受信者と送信者のもののみなのか。パブリックな中継がある？


* Cookie
* PKI
    * X509
    * OCSP
    * CRL
    * XMLデジタル署名
    * CP, CPS

* 認証基礎
    * SAML
    * OAuth
    * OpenID
    * Pass The Hash
    * Cookie認証
    * Kerberos認証
    * リバースプロキシ型認証
    * FIDO
        * UAF
        * CATP 1
        * CATP 2
    * CAPTHA
    * ロックアウト
    * リスクベース
    * JWT?

* 暗号
    * FIPS
    * TLS1.3暗号スイート
    * ハッシュ
        * 衝突困難性
    * ブロック暗号 CTR
    * TLSの役割
        * 暗号化
        * 改ざん防止
        * サーバ証明


* 脆弱性
    * CVSS
        * 基本評価基準
        * 現状評価基準

* SOAP

* HMAC, ブラウザやJWT








