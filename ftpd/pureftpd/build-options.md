# PureFTPdビルド用オプション一覧

対応version 1.0.46

## 概要

PureFTPdをソースコードからビルドする際に指定できるオプションの中で、PureFTPdの機能に関するものを取り上げています。`--prefix`のような一般的なものは省略しています。詳細は下記のようにして確かめるとよいでしょう
```
$ tar zxvf pure-ftpd-1.0.46.tar.gz
$ cd pure-ftpd-1.0.46
$ ./configure --help
$ less INSTALL
$ less README
```

## INDEX

| [--with-altlog](#--with-altlog) |
 [--without-ascii](#--without-ascii) |
 [--without-banner](#--without-banner) |
 [--with-bonjour](#--with-bonjour) |
 [--with-boring](#--with-boring) |
 [--with-brokenrealpath](#--with-brokenrealpath) |
 [--without-capabilities](#--without-capabilities) |
 [--with-certfile](#--with-certfile) |
 [--with-cookie](#--with-cookie) |
 [--without-cork](#--without-cork) |
 [--with-diraliases](#--with-diraliases) |
 [--with-everything](#--with-everything) |
 [--with-extauth](#--with-extauth) |
 [--with-ftpwho](#--with-ftpwho) |
 [--without-globbing](#--without-globbing) |
 [--without-humor](#--without-humor) |
 [--with-implicittls](#--with-implicittls) |
 [--without-inetd](#--without-inetd) |
 [--without-iplogging](#--without-iplogging) |
 [--with-language](#--with-language) |
 [--with-largefile](#--with-largefile) |
 [--with-ldap](#--with-ldap) |
 [--with-minimal](#--with-minimal) |
 [--with-mysql](#--with-mysql) |
 [--without-nonalnum](#--without-nonalnum) |
 [--with-nonroot](#--with-nonroot) |
 [--with-pam](#--with-pam) |
 [--with-paranoidmsg](#--with-paranoidmsg) |
 [--with-peruserlimits](#--with-peruserlimits) |
 [--with-pgsql](#--with-pgsql) |
 [--with-privsep](#--with-privsep) |
 [--with-probe-random-dev](#--with-probe-random-dev) |
 [--with-puredb](#--with-puredb) |
 [--with-quotas](#--with-quotas) |
 [--with-ratios](#--with-ratios) |
 [--with-rfc2640](#--with-rfc2640) |
 [--without-sendfile](#--without-sendfile) |
 [--without-shadow](#--without-shadow) |
 [--without-standalone](#--without-standalone) |
 [--with-sysquotas](#--with-sysquotas) |
 [--with-throttling](#--with-throttling) |
 [--with-tls](#--with-tls) |
 [--without-unicode](#--without-unicode) |
 [--with-uploadscript](#--with-uploadscript) |
 [--without-usernames](#--without-usernames) |
 [--with-virtualchroot](#--with-virtualchroot) |
 [--with-virtualhosts](#--with-virtualhosts) |
 [--with-welcomemsg](#--with-welcomemsg) |

## ざっくり設定

### --with-everything

ほとんどの機能を含んだ肥大サーバを作る。具体的には以下のオプションを同時に指定するのと同じ。
```
--with-altlog
--with-bonjour
--with-cookie
--with-diraliases
--with-extauth
--with-ftpwho
--with-peruserlimits
--with-puredb
--with-quotas
--with-ratios
--with-throttling
--with-uploadscript
--with-virtualhosts
```

### --with-minimal

最小限の小さなサーバをつくる。標準のFTP実装のみ対応し拡張(SITE IDLE,SITE CHMOD, MLSD, ...)は対応しない、スタンドアロンモード不可、ASCIIモード非対応など。コンパイルにgcc 3.3以上が必要。ワイルドカード表現には対応しているが`--without-globbing`を組み合わせるとこれも除外してさらに小さくできる


## FTPS

### --with-certfile

SSL certificateファイルの位置を指定する。デフォルトは`/etc/ssl/private/pure-ftpd.pem`
```
--with-certfile=<file>
```

### --with-implicittls

Implicit(暗黙の) TLS(port 990)を有効にする

### --with-tls

FTPSに対応するためにはこのオプションを指定する


## 認証

### --with-extauth

拡張認証機能(extauth)による仮想ユーザ機能を有効にする

### --with-ldap

LDAPによる仮想ユーザ機能を有効にする。OpenLDAPが必要
```
--with-ldap(=<directory>)
```

### --with-mysql

MySQLデータベースによる仮想ユーザ機能を有効にする。MySQLが必要
```
--with-mysql(=<directory>)
```

### --with-pam

PAMに対応する

### --with-pgsql

PostgreSQLデータベースによる仮想ユーザ機能を有効にする。PostgreSQLが必要
```
--with-pgsql(=<directory>)
```

### --without-shadow

/etc/shadowを使用しない

### --with-puredb

PureDBによる仮想ユーザ機能を有効にする


## システムに関係するもの

### --with-brokenrealpath

一部のSolarisのrealpath()実装に対応するためのオプション。それ以外の環境か、altlogやpure-uploadscriptを使用しないなら不要

### --with-bonjour

MacOSXでBonjour機能を有効にする

### --without-capabilities

Linux環境で、libcapがインストールされている場合でもlibcapを使用しない

### --without-cork

TCP_CORKを無効にする。プレステ用Linuxのような一部のLinuxで必要

### --with-largefile

32bitアーキテクチャで2GB以上のファイルのダウンロードに対応する

### --with-probe-random-dev

コンパイル時に/dev/¥*randomの有無を判定するのではなく実行時に判定する。ホストによって/dev/¥*randomが必ずしも存在するわけでないSolarisのようなOS向けにバイナリパッケージを作成するためのオプション

### --without-sendfile

sendfileシステムコールを使用しない。SMBFS/TmpFS/NTFSでの不具合対応のためのもの


## メッセージ表示

### --without-banner

初期バナーメッセージを表示しない

### --with-boring

ビジネスライクなメッセージ表示にする。サーバ応答メッセージからバージョン番号を除外したい場合はこのオプションを有効にする

### --with-cookie

ランダムメッセージやユーザログイン時のメッセージのカスタマイズ機能を有効にする

### --without-humor

除外しても有効にしても実用面の問題はない。無害なところでジョークを交えた応答をする

### --with-language

サーバの応答やsyslog出力の言語を変更する
```
--with-language=<lang>
```

### --with-paranoidmsg

ユーザ不在時の認証失敗のメッセージとパスワードの誤りによる認証失敗のメッセージとを同一にする

### --without-usernames

ファイル一覧表示の際にユーザ名/グループ名を使わずにUIDとGIDを数字のままで表示する

### --with-welcomemsg

(非推奨)wu-ftpdのwelcome.msg機能を有効にする。この機能を有効にしなくてもデフォルトでは.bannerファイルがあればその内容をディレクトリ移動時に表示する


## ログ

### --with-altlog

標準でSyslogへ出力されるログとは別に、転送ログ出力機能を有効にする。ログフォーマットはCLF(Apache互換),Stats(独自形式),W3C(IIS互換),xferlog(wu-ftpd互換)。

### --without-iplogging

FTPクライアントのIPアドレスをログに残さない


## FTPサーバー機能

### --without-ascii

ASCIIモードに対応しない

### --with-diraliases

ディレクトリエイリアス(ショートカット)機能を有効にする。詳細はREADMEファイルの「DIRECTORY ALIASES」を参照のこと

### --without-globbing

グロビング(ワイルドカード表現によるファイル指定)機能を除外する


## 管理用

### --with-ftpwho

pure-ftpwhoコマンドによるftpwho機能を有効にする。この機能はメモリを余分に消費する

### --without-inetd

inetdからの起動に対応しない。スタンドアロンのみでの運用の場合に使う

### --with-nonroot

一般ユーザアカウントで動作するroot権限不要のFTPサーバを作る。unix認証などroot権限を必要とするような機能は使えなくなる

### --with-privsep

OpenSSHのようなprivilege separation機能を有効にする。詳細はREADMEの「PRIVILEGE SEPARATION」を参照のこと

### --without-standalone

スタンドアロンモードでの起動に対応しない

### --with-uploadscript

ファイルがアップロードされた時に外部スクリプトを呼び出すpure-uploadscript機能を有効にする

### --with-virtualchroot

chroot()を使わない仮想chroot機能を有効にする。このオプションを指定しなければ一般的なchroot機能が標準で有効になる。chroot領域外へのシンボリックリンクを作りたい人のための機能

### --with-virtualhosts

IPアドレスごとに異なるanonymousFTPサーバを実現する。詳細はREADMEの「VIRTUAL SERVERS」を参照のこと


## リソース制限
### --with-peruserlimits

同一ユーザの同時アクセス数制限機能を有効にする

### --with-quotas

仮想quotas機能を有効にする

### --with-ratios

ratio機能を有効にする。ファイル交換サーバ用

### --with-sysquotas

システムのquotas機能に対応する

### --with-throttling

帯域制限機能を有効にする


## 多言語対応

### --without-nonalnum

ファイル名が半角英数字+「.-_」で構成されたファイルのみ扱う

### --with-rfc2640

ファイル名の文字コード変換を有効にする。iconvライブラリが必要

### --without-unicode

non-latinな文字を許可しない

