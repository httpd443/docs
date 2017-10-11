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
### --with-implicittls
### --with-tls

## 認証

### --with-extauth
### --with-ldap
### --with-mysql
### --with-pam
### --with-pgsql
### --without-shadow
### --with-puredb

## システムに関係するもの

### --with-brokenrealpath
### --without-capabilities
### --with-largefile
### --with-probe-random-dev
### --without-sendfile

## メッセージ表示

### --without-banner
### --with-boring
### --with-cookie
### --without-humor
### --with-language
### --with-paranoidmsg
### --with-welcomemsg

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

