# PureFTPdビルド用オプション一覧

対応version 1.0.46


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
 [--with-nonroot](#-with-nonroot) |
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

## おおざっぱな設定

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

### --without-capabilities

Linux環境で、libcapがインストールされている場合でもlibcapを使用しない

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

ビジネスライクで退屈なメッセージ表示にする

### --with-cookie

ランダムメッセージやユーザログイン時のメッセージのカスタマイズ機能を有効にする

### --without-humor

除外しても有効にしても実用には大差はない。FTPセッション維持のためのコマンドに対する応答に影響する

### --with-language

サーバの応答やsyslog出力の言語を変更する
```
--with-language=<lang>
```

### --with-paranoidmsg

ユーザ不在時の認証失敗のメッセージとパスワードの誤りによる認証失敗のメッセージとを同一にする

### --with-welcomemsg

(非推奨)wu-ftpdのwelcome.msg機能を有効にする。この機能を有効にしなくてもデフォルトでは.bannerファイルがあればその内容をディレクトリ移動時に表示する


## 

### --with-altlog
### --without-ascii
### --with-bonjour
### --without-cork
### --with-diraliases
### --with-ftpwho
### --without-globbing
### --without-inetd
### --without-iplogging
### --without-nonalnum
### --with-nonroot
### --with-peruserlimits
### --with-privsep
### --with-quotas
### --with-ratios
### --with-rfc2640
### --without-standalone
### --with-sysquotas
### --with-throttling
### --without-unicode
### --with-uploadscript
### --without-usernames
### --with-virtualchroot
### --with-virtualhosts

