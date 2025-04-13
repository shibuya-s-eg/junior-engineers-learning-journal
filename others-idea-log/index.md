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
    * サイバーセキュリティと情報セキュリティ：済
    * 物理的セキュリティと論理的セキュリティ：済
    * CIA：済
    * 付加的な特性：済

* NDA

* 制度/フレームワーク/ガイドライン
    * ISMS
        * 27000シリーズ
        * 27001
        * 27002
        * 27017
        * 27018
        * クラウドセキュリティ認証
    * JIS Q
        * 27017 20000
        * 15001
        * 27014
    * ISMAP
        * ismap liu
        * SP800-53を参照
    * 防衛産業サイバーセキュリティ基準
        * 能動的サイバー防御
    * ISMS適合性評価制度
        * 範囲はISMS適用範囲定義書
    * ISMSクラウドセキュリティ認証
    * AI事業者ガイドライン
    * NIST ZTA
    * ZTNA
        * SDPコントローラ
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
        * 偵察
        * 武器化
    * MITER
    * NIST サイバーセキュリティフレームワーク
    * コンピュータセキュリティインシデントガイド
    * 証拠保全のやつ
    * STIX
        * サイバー攻撃活動
        * 攻撃者
        * 攻撃手口
        * 検知指標
        * 観測事象
        * インシデント
        * 対処措置
        * 攻撃対象
    * 内部不正ガイドライン
    * 電子商取引及び情報財取引等に関する準則
    * JIPDEC
    * JCMVP
    * ウィーケストリンクモデル
        * ドベネックの桶
    * ISO/IEC 15408

* セキュリティソリューション
    * CASB
    * sase
        * SD-WAN
        * SWG
        * FWAAS
        * ZTNA
        * RBI
        * CASB
        * CSPM
        * DLP
        * UEBA
    * CAASM
    * NIST SP800 207
    * 拡張ゼロトラスト

* 非機能
    * キャパシティ管理

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

* AIへの攻撃

* IoT
    * タイポスワっティング
    * ホモグラフ攻撃
    * 好き民具
    * 電磁シールド
    * ステガノグラフィ
    * テンペスト攻撃
    * wi-peep

* Webセキュリティ
    * 攻撃
        * SQLインジェクション
        * クロスサイトスクリプティング
        * クロスサイトリクエストフォージェリ
        * HTTPヘッダインジョクション
        * メールヘッダインジェクション
        * ディレクトリトラバーサル
        * サーバーサイドリクエストフォージェリ
        * OSコマンドインジェクション
        * セッションハイジャック
        * マンインサミドル
        * Pass The Hash
        * rat
        * MITM
            * トランザクション署名
        * モバイルコード
        * 水飲み場攻撃
        * emotet
        * monero
        * LOTL
        * ｸｲｯｼﾝｸﾞ

    * 防御
        * CSRFトークン
        * samesite属性
        * EV SSL見分け
        * HSTS
        * Keep-Alive
        * キャッシュコントロール
        * トランザクション認証
            * これって同じ秘密鍵的なものをサーバでも持っている感じ?
        * X XSS Protection
        * Client Security Policy
        * Chache Controle: no chacheとか
        * セッションフィくせーション
        * cookie monster bug
        * domain属性
        * url rewriting
        * ドメインフロンティング
        * 2.8.1
        * content ecurity policy
        * traceメソッド
        * クリックジャッキング, samesite
        * x frame option
        * PUA
        * ゾーニング


* IRC
* 3-2-1ルール
* マルウェア検知手法
* ノーウェアランサム
* ct,  security.txt
* ACME, SCEP
* IRR
* RPKI
* ROA
* ROV
* rootでログインさせるとだれが使ったのか分からない。
* IPHNEはMACアドレス地をランダム化させているらしい
* JC-STAR
* NPU
* インシデント対応
    * BCP
    * BCM
    * IRP
    * コンティンジェンシープラン
    * ディザスタリカバリ


* 自動車
    * 自動車の情報セキュリティへの取り組みガイド
    * misra c
    * misra c++
    * obd2
    * CAN
    * 車載イーサネット
    * SOM/IP
    * DOIP


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
    * wpa2とwpa3の違い
    * wifi dpp
    * sae
    * iphoneのMACアドレスランダム化
    * OpenRoaming
        * eduroam

* セキュリティ団体
    * CRYPTOREC
    * NICT
        * ダイダロス
        * NOTICE
        * 総合テストベッド
    * IPA
    * NISC
    * JCSIP
    * JPCERT/CC
    * FIRST
    * 経済産業省
    * セプターカウンシル

* DoS
    * synflood
    * http post flood
    * ボットネット
    * optimisticack, duplicate ack, partial ack: firewallとかの送信順序をどうこうするやつ
    * smurf攻撃
    * メールボム

* NMAP
    * ステルススキャン

* BOF
    * DEP
        * return-to-libc
    * アドレス空間ランダム化
    * PIE
    * 整数オーバーフロー
    * BOFの仕組み
    * stack guard
    * ssp
    * カナリア
    * automatic fotification

* ルートキット


* DNS
    * CAAレコード
        * この意味
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
    * 2.6.1
    * ファーミング
    * DNSアンプ
        * キャッシュサーバ公開しない
        * どうやってレスをでかくする？
    * DNSトンネリング
    * 権威DNSも返してくれるけどrecursion noなので、再起問い合わせしてくれない
    * FAST FLUX
    * Domain flux
    * IDNA


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

* mtm
    * arpスプーフィング
    * tcp, udp, web, 認証


* Cookie
* PKI
    * X509
    * OCSP
    * SCVP
        * 認証局側に訪問がばれる
    * CRL
    * XMLデジタル署名
    * CP, CPS
    * dv, ev, ov: 1年間
        * 1年間
        * Let's Encryptoはdvでありcnのみ

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
    * CHAPリプレイ攻撃、なりすまし
    * レインボーテーブル、ソルト
    * パスワードスプレー
    * パスワードリスト
    * クレデンシャルスタッフィング攻撃
    * pass tha hash
    * ケルベロス認証
    * s/key
    * パスキー
    * IDaaS
        * idパスワードはネットワークに流さない。
    * reflesh token
    * SCIM
    * OIDC
        * samlにはないがodicにはユーザからの同意を得る手順がある
    * SMS認証
        * 課金
        * 拒否
        * SIMスワップ
    * バイオメトリクス認証
        * 本人拒否率
        * 他人受け入れ率
        * 代替手段が必要
        * 問題点
    * バイオメトリクス認証
        * 本人拒否率
        * 他人受け入れ率
        * マスターフェイス
        * ウルフ攻撃
    * ekyc
        * EKYCのライブネスチェック
        * 犯収法
            * 顧客の指名・住所・生年月日などの「本人特定事項」や「取引を行う目的」
        * ホ方式、ワ方式
        * ディープフェイク
    * ハードウェアトークン
    * JWT
    * CSMS認証
    * 認証局のかい総合像
    * ISO 42001
    * ジョーアカウント


* FAPI
* FAPI 2.0
    * HOK
    * MTLS
    * DPOP

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
    * 楕円曲線はリソース低い
    * 耐量子暗号
    * 量子鍵配送
    * 楕円極性
        * ed25519
    * モスカの定理
    * 講師暗号
    * ショアのアルゴリズム
    * 秘密計算
    * 準同型暗号
    * 秘密分散
    * ハイブリット
    * しきい値秘密分散
        * チェックサムっぽい
    * MD5
        * 衝突
    * MAC
    * HMAC
    * CMAC
    * ゼロ知識証明
        * CHAP



* 脆弱性
    * CVSS
        * 基本評価基準
        * 現状評価基準
        * 脅威
        * CVSS-〇〇
    * SSVC

* SOAP

* HMAC, ブラウザやJWT



