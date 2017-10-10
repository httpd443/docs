# PureFTPd設定オプション一覧

対応version 1.0.46


## INDEX

### pure-ftpd.conf, or Debian/Ubuntu Package

| [AllowAnonymousFXP](#allowanonymousfxp) |
[AllowDotFiles](#allowdotfiles) |
[AllowUserFXP](#allowuserfxp) |
[AltLog](#altlog) |
[AnonymousBandwidth](#anonymousbandwidth) |
[AnonymousCanCreateDirs](#anonymouscancreatedirs) |
[AnonymousCantUpload](#anonymouscantupload) |
[AnonymousOnly](#anonymousonly) |
[AnonymousRatio](#anonymousratio) |
[AntiWarez](#antiwarez) |
[AutoRename](#autorename) |
[Bind](#bind) |
[BrokenClientsCompatibility](#brokenclientscompatibility) |
[CallUploadScript](#calluploadscript) |
[Certificate](#certfile) |
[ChrootEveryone](#chrooteveryone) |
[ClientCharset](#clientcharset) |
[CreateHomeDir](#createhomedir) |
[CustomerProof](#customerproof) |
[Daemonize](#daemonize) |
[DisplayDotFiles](#displaydotfiles) |
[DontResolve](#dontresolve) |
[ExtAuth](#extauth) |
[FSCharset](#filesystemcharset) |
[FileSystemCharset](#filesystemcharset) |
[ForcePassiveIP](#forcepassiveip) |
[FortunesFile](#fortunesfile) |
[IPV4Only](#ipv4only) |
[IPV6Only](#ipv6only) |
[KeepAllFiles](#keepallfiles) |
[LDAPConfigFile](#ldapconfigfile) |
[LimitRecursion](#limitrecursion) |
[LogPID](#logpid) |
[MaxClientsNumber](#maxclientsnumber) |
[MaxClientsPerIP](#maxclientsperip) |
[MaxDiskUsage](#maxdiskusage) |
[MaxIdleTime](#maxidletime) |
[MaxLoad](#maxload) |
[MinUID](#minuid) |
[MySQLConfigFile](#mysqlconfigfile) |
[NATmode](#natmode) |
[NoAnonymous](#noanonymous) |
[NoChmod](#nochmod) |
[NoRename](#norename) |
[NoTruncate](#notruncate) |
[PAMAuthentication](#pamauthentication) |
[PGSQLConfigFile](#pgsqlconfigfile) |
[PIDFile](#pidfile) |
[PassivePortRange](#passiveportrange) |
[PerUserLimits](#peruserlimits) |
[ProhibitDotFilesRead](#prohibitdotfilesread) |
[ProhibitDotFilesWrite](#prohibitdotfileswrite) |
[PureDB](#puredb) |
[Quota](#quota) |
[SyslogFacility](#syslogfacility) |
[TLSCipherSuite](#tlsciphersuite) |
[TLS](#tls) |
[TrustedGID](#trustedgid) |
[TrustedIP](#trustedip) |
[Umask](#umask) |
[UnixAuthentication](#unixauthentication) |
[UserBandwidth](#userbandwidth) |
[UserRatio](#userratio) |
[VerboseLog](#verboselog) |

---
### short option

| [-0](#notruncate) |
[-1](#logpid) |
[-2](#certfile) |
[-4](#ipv4only) |
[-6](#ipv6only) |
[-8](#filesystemcharset) |
[-9](#clientcharset) |
[-A](#chrooteveryone) |
[-B](#daemonize) |
[-C](#maxclientsperip) |
[-D](#displaydotfiles) |
[-E](#noanonymous) |
[-F](#fortunesfile) |
[-G](#norename) |
[-H](#dontresolve) |
[-I](#maxidletime) |
[-J](#tlsciphersuite) |
[-K](#keepallfiles) |
[-L](#limitrecursion) |
[-M](#anonymouscancreatedirs) |
[-N](#natmode) |
[-O](#altlog) |
[-P](#forcepassiveip) |
[-Q](#userratio) |
[-R](#nochmod) |
[-S](#bind) |
[-T](#userbandwidth) |
[-U](#umask) |
[-V](#trustedip) |
[-W](#allowanonymousfxp) |
[-X](#prohibitdotfilesread) |
[-Y](#tls) |
[-Z](#customerproof) |
[-a](#trustedgid) |
[-b](#brokenclientscompatibility) |
[-c](#maxclientsnumber) |
[-d](#verboselog) |
[-e](#anonymousonly) |
[-f](#syslogfacility) |
[-g](#pidfile) |
[-h](#help) |
[-i](#anonymouscantupload) |
[-j](#createhomedir) |
[-k](#maxdiskusage) |
[-l](#認証) |
[-m](#maxload) |
[-n](#quota) |
[-o](#calluploadscript) |
[-p](#passiveportrange) |
[-q](#anonymousratio) |
[-r](#autorename) |
[-s](#antiwarez) |
[-t](#anonymousbandwidth) |
[-u](#minuid) |
[-v](#bonjour) |
[-w](#allowuserfxp) |
[-x](#prohibitdotfileswrite) |
[-y](#peruserlimits) |
[-z](#allowdotfiles) |

---
### long option

| [--allowanonymousfxp](#allowanonymousfxp) |
[--allowdotfiles](#allowdotfiles) |
[--allowuserfxp](#allowuserfxp) |
[--altlog](#altlog) |
[--anonymousbandwidth](#anonymousbandwidth) |
[--anonymouscancreatedirs](#anonymouscancreatedirs) |
[--anonymouscantupload](#anonymouscantupload) |
[--anonymousonly](#anonymousonly) |
[--anonymousratio](#anonymousratio) |
[--antiwarez](#antiwarez) |
[--autorename](#autorename) |
[--bind](#bind) |
[--bonjour](#bonjour) |
[--brokenclientscompatibility](#brokenclientscompatibility) |
[--certfile](#certfile) |
[--chrooteveryone](#chrooteveryone) |
[--clientcharset](#clientcharset) |
[--createhomedir](#createhomedir) |
[--customerproof](#customerproof) |
[--daemonize](#daemonize) |
[--displaydotfiles](#displaydotfiles) |
[--dontresolve](#dontresolve) |
[--forcepassiveip](#forcepassiveip) |
[--fortunesfile](#fortunesfile) |
[--fscharset](#filesystemcharset) |
[--help](#help) |
[--ipv4only](#ipv4only) |
[--ipv6only](#ipv6only) |
[--keepallfiles](#keepallfiles) |
[--limitrecursion](#limitrecursion) |
[--login](#認証) |
[--logpid](#logpid) |
[--maxclientsnumber](#maxclientsnumber) |
[--maxclientsperip](#maxclientsperip) |
[--maxdiskusagepct](#maxdiskusage) |
[--maxidletime](#maxidletime) |
[--maxload](#maxload) |
[--minuid](#minuid) |
[--natmode](#natmode) |
[--noanonymous](#noanonymous) |
[--nochmod](#nochmod) |
[--norename](#norename) |
[--notruncate](#notruncate) |
[--passiveportrange](#passiveportrange) |
[--peruserlimits](#peruserlimits) |
[--pidfile](#pidfile) |
[--prohibitdotfilesread](#prohibitdotfilesread) |
[--prohibitdotfileswrite](#prohibitdotfileswrite) |
[--quota](#quota) |
[--syslogfacility](#syslogfacility) |
[--tls](#tls) |
[--tlsciphersuite](#tlsciphersuite) |
[--trustedgid](#trustedgid) |
[--trustedip](#trustedip) |
[--umask](#umask) |
[--uploadscript](#calluploadscript) |
[--userbandwidth](#userbandwidth) |
[--userratio](#userratio) |
[--verboselog](#verboselog) |

---

## 使い方

### Help

pure-ftpdで有効なオプションの一覧を表示する

- short option:
  ```
  $ pure-ftpd -h
  ```

- long option:
  ```
  $ pure-ftpd --help
  ```

## FTPS

### TLS

TLS/SSLの有効/無効を指定する
- 0(デフォルト値)はTLS/SSL無効
- 1はTLS/SSLと非暗号の両方を有効にする
- 2はTLS/SSLのみ有効にする、ファイル転送は暗号化・非暗号の両方を許容する
- 3はファイル転送含めて暗号化通信のみとなる

- short option:
  ```
  $ pure-ftpd -Y (0|1|2|3)
  ```

- long option:
  ```
  $ pure-ftpd --tls=(0|1|2|3)
  ```

- pure-ftpd.conf:
  ```
  TLS        (0|1|2|3)
  ```

- Debian/Ubuntu Package:
  ```
  $ echo (0|1|2|3) | sudo tee /etc/pure-ftpd/conf/TLS
  ```

### TLSCipherSuite

TLSで使用するcipher suiteの設定

- short option:
  ```
  $ pure-ftpd -J <ciphers>
  ```

- long option:
  ```
  $ pure-ftpd --tlsciphersuite=<ciphers>
  ```

- pure-ftpd.conf:
  ```
  TLSCipherSuite        <ciphers>
  ```

- Debian/Ubuntu Package:
  ```
  $ echo <ciphers> | sudo tee /etc/pure-ftpd/conf/TLSCipherSuite
  ```

### CertFile

TLSで使用する証明書ファイルを指定する

- short option:
  ```
  $ pure-ftpd -2 <file>
  ```

- long option:
  ```
  $ pure-ftpd --certfile=<file>
  ```

- pure-ftpd.conf:
  ```
  Certificate        <file>
  ```

- Debian/Ubuntu Package:
  ```
  非対応
  「/etc/pki/tls/certs/pure-ftpd.pem」や「/etc/ssl/private/pure-ftpd.pem』等、ディストリビューションごとの固定値がある
  ```

## 認証

### UnixAuthentication

unix認証方式を使用する

- short option:
  ```
  $ pure-ftpd -l unix:<file>
  ```

- long option:
  ```
  $ pure-ftpd --login=unix:<file>
  ```

- pure-ftpd.conf:
  ```
  UnixAuthentication        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/UnixAuthentication
  ```

### PAMAuthentication

認証にPAMを使用する

- short option:
  ```
  $ pure-ftpd -l pam
  ```

- long option:
  ```
  $ pure-ftpd --login=pam
  ```

- pure-ftpd.conf:
  ```
  PAMAuthentication        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/PAMAuthentication
  ```

### PureDB

PureDBを認証方式に使用する

- short option:
  ```
  $ pure-ftpd -l puredb:<file>
  ```

- long option:
  ```
  $ pure-ftpd --login=puredb:<file>
  ```

- pure-ftpd.conf:
  ```
  PureDB        <file>
  ```

- Debian/Ubuntu Package:
  ```
  $ echo <file> | sudo tee /etc/pure-ftpd/conf/PureDB
  ```

### MySQLConfigFile

MySQLを認証方式に使用する

- short option:
  ```
  $ pure-ftpd -l mysql:<file>
  ```

- long option:
  ```
  $ pure-ftpd --login=mysql:<file>
  ```

- pure-ftpd.conf:
  ```
  MySQLConfigFile        <file>
  ```

- Debian/Ubuntu Package:
  ```
  $ echo <file> | sudo tee /etc/pure-ftpd/conf/MySQLConfigFile
  ```

### PGSQLConfigFile

PostgreSQLを認証方式に使用する

- short option:
  ```
  $ pure-ftpd -l pgsql:<file>
  ```

- long option:
  ```
  $ pure-ftpd --login=pgsql:<file>
  ```

- pure-ftpd.conf:
  ```
  PGSQLConfigFile        <file>
  ```

- Debian/Ubuntu Package:
  ```
  $ echo <file> | sudo tee /etc/pure-ftpd/conf/PGSQLConfigFile
  ```

### LDAPConfigFile

LDAPを認証方式に使用する

- short option:
  ```
  $ pure-ftpd -l ldap:<file>
  ```

- long option:
  ```
  $ pure-ftpd --login=ldap:<file>
  ```

- pure-ftpd.conf:
  ```
  LDAPConfigFile        <file>
  ```

- Debian/Ubuntu Package:
  ```
  $ echo <file> | sudo tee /etc/pure-ftpd/conf/LDAPConfigFile
  ```

### ExtAuth

独自の認証方式を使用する

- short option:
  ```
  $ pure-ftpd -l extauth:<socket file>
  ```

- long option:
  ```
  $ pure-ftpd --login=extauth:<socket file>
  ```

- pure-ftpd.conf:
  ```
  ExtAuth        <socket file>
  ```

- Debian/Ubuntu Package:
  ```
  $ echo <socket file> | sudo tee /etc/pure-ftpd/conf/ExtAuth
  ```

### CreateHomeDir

ユーザログイン時にホームディレクトリが存在しない場合に自動的に作成する

- short option:
  ```
  $ pure-ftpd -j
  ```

- long option:
  ```
  $ pure-ftpd --createhomedir
  ```

- pure-ftpd.conf:
  ```
  CreateHomeDir        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/CreateHomeDir
  ```

### MinUID

指定したuid未満のuidのユーザのログインを禁止する

- short option:
  ```
  $ pure-ftpd -u <uid>
  ```

- long option:
  ```
  $ pure-ftpd --minuid=<uid>
  ```

- pure-ftpd.conf:
  ```
  MinUID        <uid>
  ```

- Debian/Ubuntu Package:
  ```
  $ echo <uid> | sudo tee /etc/pure-ftpd/conf/MinUID
  ```

## ネットワーク

### Bind

サーバが受け付けるIPアドレス(またはホスト名)とポート番号(または/etc/servicesのサービス名)を指定する

- short option:
  ```
  $ pure-ftpd -S [IP][,Port]
  ```

- long option:
  ```
  $ pure-ftpd --bind=[IP][,Port]
  ```

- pure-ftpd.conf:
  ```
  Bind        [IP][,Port]
  ```

- Debian/Ubuntu Package:
  ```
  $ echo [IP][,Port] | sudo tee /etc/pure-ftpd/conf/Bind
  ```

- 使用例:  
```
# IPアドレス172.0.0.1へのアクセスのみ受け付ける
$ pure-ftpd -S 171.0.0.1
# ftp.example.comのポート8021へのアクセスを受け付ける
$ pure-ftpd -S ftp.example.com,8021
# 通常のポート番号21ではなくポート番号8021へのアクセスを受け付ける
$ pure-ftpd -S ,8021
```

### Bonjour

Bonjourを有効にし、Bonjour名を<name>に設定する

- short option:
  ```
  $ pure-ftpd -v <name>
  ```

- long option:
  ```
  $ pure-ftpd --bonjour=<name>
  ```

- pure-ftpd.conf:
  ```
  非対応        nul
  ```

- Debian/Ubuntu Package:
  ```
  非対応
  ```

### IPV4Only

IPv4接続のみ受け付ける

- short option:
  ```
  $ pure-ftpd -4
  ```

- long option:
  ```
  $ pure-ftpd --ipv4only
  ```

- pure-ftpd.conf:
  ```
  IPV4Only        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/IPV4Only
  ```

### IPV6Only

IPv6接続のみ受け付ける

- short option:
  ```
  $ pure-ftpd -6
  ```

- long option:
  ```
  $ pure-ftpd --ipv6only
  ```

- pure-ftpd.conf:
  ```
  IPV6Only        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/IPV6Only
  ```

### MaxIdleTime

タイムアウトまでの無通信時間の最大値を分単位で設定。デフォルトでは15分

- short option:
  ```
  $ pure-ftpd -I <time>
  ```

- long option:
  ```
  $ pure-ftpd --maxidletime=<time>
  ```

- pure-ftpd.conf:
  ```
  MaxIdleTime        <time>
  ```

- Debian/Ubuntu Package:
  ```
  $ echo <time> | sudo tee /etc/pure-ftpd/conf/MaxIdleTime
  ```

## NAT越え

### ForcePassiveIP

PASV/EPSV/SPSVコマンド(passiveモード)への応答に使うIPアドレスを指定する

- short option:
  ```
  $ pure-ftpd -P <ip or hostname>
  ```

- long option:
  ```
  $ pure-ftpd --forcepassiveip=<ip or hostname>
  ```

- pure-ftpd.conf:
  ```
  ForcePassiveIP        <ip or hostname>
  ```

- Debian/Ubuntu Package:
  ```
  $ echo <ip or hostname> | sudo tee /etc/pure-ftpd/conf/ForcePassiveIP
  ```

### NATmode

passiveモードを禁止する

- short option:
  ```
  $ pure-ftpd -N
  ```

- long option:
  ```
  $ pure-ftpd --natmode
  ```

- pure-ftpd.conf:
  ```
  NATmode        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/NATmode
  ```

### PassivePortRange

passiveモードで使用するポートの範囲を指定する

- short option:
  ```
  $ pure-ftpd -p <min port:max port>
  ```

- long option:
  ```
  $ pure-ftpd --passiveportrange=<min port:max port>
  ```

- pure-ftpd.conf:
  ```
  PassivePortRange        <min port> <max port>
  ```

- Debian/Ubuntu Package:
  ```
  $ echo <min port> <max port> | sudo tee /etc/pure-ftpd/conf/PassivePortRange
  ```

- 使用例:  
```
# 使用するポートの範囲を4000〜5000にする
$ pure-ftpd -O -p 4000:5000
```

## ログ

### AltLog

転送ログを指定したファイル・フォーマットで出力する

- short option:
  ```
  $ pure-ftpd -O <format:file>
  ```

- long option:
  ```
  $ pure-ftpd --altlog=<format:file>
  ```

- pure-ftpd.conf:
  ```
  AltLog        <format:file>
  ```

- Debian/Ubuntu Package:
  ```
  $ echo <format:file> | sudo tee /etc/pure-ftpd/conf/AltLog
  ```

- 使用例:  
```
# Apache風の転送ログを出力する
$ pure-ftpd -O clf:/var/log/pureftpd.log
# 独自形式の転送ログを出力する
$ pure-ftpd -O stats:/var/log/pureftpd.log
# IIS風の転送ログを出力する
$ pure-ftpd -O w3c:/var/log/pureftpd.log
# xferlog形式(wu-ftpd等と同じ)で転送ログを出力する
$ pure-ftpd -O xferlog:/var/log/pureftpd.log
```

### DontResolve

FTPクライアントの名前解決を行わずにIPアドレスを出力する

- short option:
  ```
  $ pure-ftpd -H
  ```

- long option:
  ```
  $ pure-ftpd --dontresolve
  ```

- pure-ftpd.conf:
  ```
  DontResolve        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/DontResolve
  ```

### LogPID

プロセスIDをSyslogへの出力に加える。-f <none>が指定された場合にはこのオプションは無視される

- short option:
  ```
  $ pure-ftpd -1
  ```

- long option:
  ```
  $ pure-ftpd --logpid
  ```

- pure-ftpd.conf:
  ```
  LogPID        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/LogPID
  ```

### SyslogFacility

Syslogへ出力する際のfacilityを指定する。デフォルトではftp( or local2 )。noneを指定するとSyslogへの出力を行わない

- short option:
  ```
  $ pure-ftpd -f <facility>
  ```

- long option:
  ```
  $ pure-ftpd --syslogfacility=<facility>
  ```

- pure-ftpd.conf:
  ```
  SyslogFacility        <facility>
  ```

- Debian/Ubuntu Package:
  ```
  $ echo <facility> | sudo tee /etc/pure-ftpd/conf/SyslogFacility
  ```

### VerboseLog

FTPクライアント側の全コマンドをSyslogに出力する。-d -dのように二重に指定するとサーバ側の応答も出力する

- short option:
  ```
  $ pure-ftpd -d
  ```

- long option:
  ```
  $ pure-ftpd --verboselog
  ```

- pure-ftpd.conf:
  ```
  VerboseLog        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/VerboseLog
  ```

## anonymous

### AllowDotFiles

anonymousユーザに対して、ドットで始まる名前のファイルとディレクトリへのreadアクセスを許可する

- short option:
  ```
  $ pure-ftpd -z
  ```

- long option:
  ```
  $ pure-ftpd --allowdotfiles
  ```

- pure-ftpd.conf:
  ```
  AllowDotFiles        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/AllowDotFiles
  ```

### AnonymousBandwidth

anonymousユーザの帯域幅をKB/s単位で制限する

- short option:
  ```
  $ pure-ftpd -t <bandwidth or [up]:[down]>
  ```

- long option:
  ```
  $ pure-ftpd --anonymousbandwidth=<bandwidth or [up]:[down]>
  ```

- pure-ftpd.conf:
  ```
  AnonymousBandwidth        <bandwidth> or <up> <down>
  ```

- Debian/Ubuntu Package:
  ```
  $ echo <bandwidth> or <up> <down> | sudo tee /etc/pure-ftpd/conf/AnonymousBandwidth
  ```

### AnonymousCanCreateDirs

anonymousユーザのディレクトリ作成を許可する

- short option:
  ```
  $ pure-ftpd -M
  ```

- long option:
  ```
  $ pure-ftpd --anonymouscancreatedirs
  ```

- pure-ftpd.conf:
  ```
  AnonymousCanCreateDirs        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/AnonymousCanCreateDirs
  ```

### AnonymousCantUpload

パーミッションに関わらずanonymousユーザのアップロードを禁止する

- short option:
  ```
  $ pure-ftpd -i
  ```

- long option:
  ```
  $ pure-ftpd --anonymouscantupload
  ```

- pure-ftpd.conf:
  ```
  AnonymousCantUpload        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/AnonymousCantUpload
  ```

### AnonymousOnly

Anonymous専用FTPサーバにする。anonymous以外のユーザはログインできない

- short option:
  ```
  $ pure-ftpd -e
  ```

- long option:
  ```
  $ pure-ftpd --anonymousonly
  ```

- pure-ftpd.conf:
  ```
  AnonymousOnly        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/AnonymousOnly
  ```

### AnonymousRatio

anonymousユーザのratio比率を設定する。-q 1:5なら1MBのファイルを献上する見返りに5MBのファイルを入手できる

- short option:
  ```
  $ pure-ftpd -q <upload:download>
  ```

- long option:
  ```
  $ pure-ftpd --anonymousratio=<upload:download>
  ```

- pure-ftpd.conf:
  ```
  AnonymousRatio        <upload> <download>
  ```

- Debian/Ubuntu Package:
  ```
  $ echo <upload> <download> | sudo tee /etc/pure-ftpd/conf/AnonymousRatio
  ```

### AntiWarez

anonymousユーザが「ftp」ユーザ所有のファイルのダウンロードを禁止する。つまり、あるanonymousユーザがアップロードしたファイルを別のanonymousユーザがダウンロードすることを防ぐということ。warezサイト化防止のためのオプション

- short option:
  ```
  $ pure-ftpd -s
  ```

- long option:
  ```
  $ pure-ftpd --antiwarez
  ```

- pure-ftpd.conf:
  ```
  AntiWarez        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/AntiWarez
  ```

### MaxLoad

ロードアベレージが<load>を超えるときにanonymousユーザのダウンロードを禁止する。ファイル一覧表示とアップロードは可能

- short option:
  ```
  $ pure-ftpd -m <load>
  ```

- long option:
  ```
  $ pure-ftpd --maxload=<load>
  ```

- pure-ftpd.conf:
  ```
  MaxLoad        <load>
  ```

- Debian/Ubuntu Package:
  ```
  $ echo <load> | sudo tee /etc/pure-ftpd/conf/MaxLoad
  ```

### NoAnonymous

一般ユーザのみログインを許可し、anonymousユーザのログインを禁止する

- short option:
  ```
  $ pure-ftpd -E
  ```

- long option:
  ```
  $ pure-ftpd --noanonymous
  ```

- pure-ftpd.conf:
  ```
  NoAnonymous        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/NoAnonymous
  ```

### TrustedIP

管理用のIPアドレスを指定。このIPアドレスへアクセスしてきた場合は一般ユーザのみログインでき、他のIPアドレス以外へアクセスしてきた場合はanonymousユーザのみログインできる

- short option:
  ```
  $ pure-ftpd -V <IP>
  ```

- long option:
  ```
  $ pure-ftpd --trustedip=<IP>
  ```

- pure-ftpd.conf:
  ```
  TrustedIP        <IP>
  ```

- Debian/Ubuntu Package:
  ```
  $ echo <IP> | sudo tee /etc/pure-ftpd/conf/TrustedIP
  ```

## ファイルアクセス

### ChrootEveryone

root以外の全ユーザをchrootする

- short option:
  ```
  $ pure-ftpd -A
  ```

- long option:
  ```
  $ pure-ftpd --chrooteveryone
  ```

- pure-ftpd.conf:
  ```
  ChrootEveryone        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/ChrootEveryone
  ```

### CustomerProof

ユーザが起こしがちな過ちを防ぐ。今のところ、ユーザがchmodで自らのファイルやディレクトリにアクセスできなくなるのを防止する

- short option:
  ```
  $ pure-ftpd -Z
  ```

- long option:
  ```
  $ pure-ftpd --customerproof
  ```

- pure-ftpd.conf:
  ```
  CustomerProof        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/CustomerProof
  ```

### DisplayDotFiles

クライアント側が-aオプションをつけなくてもファイル一覧表示時にデフォルトでドットファイルを表示する

- short option:
  ```
  $ pure-ftpd -D
  ```

- long option:
  ```
  $ pure-ftpd --displaydotfiles
  ```

- pure-ftpd.conf:
  ```
  DisplayDotFiles        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/DisplayDotFiles
  ```

### KeepAllFiles

ファイルの消失防止のためのオプション。ファイルの名前変更と削除を禁止し、ファイルのアップロードとアップロードのresumeは許可される。上書きについてはアップロード時のresumeのために許可されるので、-rオプションと組み合わせて使うとよい

- short option:
  ```
  $ pure-ftpd -K
  ```

- long option:
  ```
  $ pure-ftpd --keepallfiles
  ```

- pure-ftpd.conf:
  ```
  KeepAllFiles        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/KeepAllFiles
  ```

### LimitRecursion

ファイル一覧に表示するファイルの数と(-Rオプションによる再帰的表示時の)サブディレクトリの深度の上限を設定する。無制限にしたい場合は-1を設定値にするとよい。FTPクライアント側が特定ディレクトリ配下のファイル情報を再帰的に一気に取得するような仕様の場合は、この設定値を緩和する必要が生じる可能性がある。デフォルトでは2000:5

- short option:
  ```
  $ pure-ftpd -L <max files:max depth>
  ```

- long option:
  ```
  $ pure-ftpd --limitrecursion=<max files:max depth>
  ```

- pure-ftpd.conf:
  ```
  LimitRecursion        <max files> <max depth>
  ```

- Debian/Ubuntu Package:
  ```
  $ echo <max files> <max depth> | sudo tee /etc/pure-ftpd/conf/LimitRecursion
  ```

### NoChmod

root以外のユーザによるchmodコマンドの使用を禁止する

- short option:
  ```
  $ pure-ftpd -R
  ```

- long option:
  ```
  $ pure-ftpd --nochmod
  ```

- pure-ftpd.conf:
  ```
  NoChmod        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/NoChmod
  ```

### NoRename

ファイルの移動、ファイル名変更を禁止する

- short option:
  ```
  $ pure-ftpd -G
  ```

- long option:
  ```
  $ pure-ftpd --norename
  ```

- pure-ftpd.conf:
  ```
  NoRename        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/NoRename
  ```

### ProhibitDotFilesRead

ドットファイルの読み書きを禁止する。~/.sshのようなドットで始まるディレクトリの場合はcdすることができなくなる

- short option:
  ```
  $ pure-ftpd -X
  ```

- long option:
  ```
  $ pure-ftpd --prohibitdotfilesread
  ```

- pure-ftpd.conf:
  ```
  ProhibitDotFilesRead        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/ProhibitDotFilesRead
  ```

### ProhibitDotFilesWrite

ドットファイルへの一般ユーザの上書きと作成、削除を禁止する。anonymousユーザの場合は、セキュリティ上の理由(.rhostsや.sshなど)でドットファイルへのアクセスはデフォルトで禁止されている

- short option:
  ```
  $ pure-ftpd -x
  ```

- long option:
  ```
  $ pure-ftpd --prohibitdotfileswrite
  ```

- pure-ftpd.conf:
  ```
  ProhibitDotFilesWrite        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/ProhibitDotFilesWrite
  ```

### Quota

virtual quotaを使用する。.ftpqutoaファイルが作成され、ユーザごとにホームディレクトリ内のファイル数の最大値と容量の最大値を制限する

- short option:
  ```
  $ pure-ftpd -n <max files:max size>
  ```

- long option:
  ```
  $ pure-ftpd --quota=<max files:max size>
  ```

- pure-ftpd.conf:
  ```
  Quota        <max files:max size>
  ```

- Debian/Ubuntu Package:
  ```
  $ echo <max files> <max size> | sudo tee /etc/pure-ftpd/conf/Quota
  ```

### TrustedGID

rootとgidに指定したグループに所属するユーザ以外のユーザをchrootする

- short option:
  ```
  $ pure-ftpd -a <gid>
  ```

- long option:
  ```
  $ pure-ftpd --trustedgid=<gid>
  ```

- pure-ftpd.conf:
  ```
  TrustedGID        <gid>
  ```

- Debian/Ubuntu Package:
  ```
  $ echo <gid> | sudo tee /etc/pure-ftpd/conf/TrustedGID
  ```

### Umask

ファイルとディレクトリ作成時のumaskを指定する。デフォルトは133と022

- short option:
  ```
  $ pure-ftpd -U <umask file:umask dir>
  ```

- long option:
  ```
  $ pure-ftpd --umask=<umask file:umask dir>
  ```

- pure-ftpd.conf:
  ```
  Umask        <umask file:umask dir>
  ```

- Debian/Ubuntu Package:
  ```
  $ echo <umask file:umask dir> | sudo tee /etc/pure-ftpd/conf/Umask
  ```

- 使用例:  
```
# ファイルのumaskを177、ディレクトリのumaskを077にする
$ pure-ftpd -U 177:077
```

## アップロード

### AutoRename

ファイルのアップロード時に、すでに同名のファイルが同じディレクトリに存在する場合は上書きせずにxyz.1、xyz.2などとする

- short option:
  ```
  $ pure-ftpd -r
  ```

- long option:
  ```
  $ pure-ftpd --autorename
  ```

- pure-ftpd.conf:
  ```
  AutoRename        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/AutoRename
  ```

### CallUploadScript

pure-uploadscriptを有効にする

- short option:
  ```
  $ pure-ftpd -o
  ```

- long option:
  ```
  $ pure-ftpd --uploadscript
  ```

- pure-ftpd.conf:
  ```
  CallUploadScript        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/CallUploadScript
  ```

### MaxDiskUsage

ディスクの使用量が指定したパーセンテージを超えた場合は、それ以上のアップロードを禁止する

- short option:
  ```
  $ pure-ftpd -k <percentage>
  ```

- long option:
  ```
  $ pure-ftpd --maxdiskusagepct=<percentage>
  ```

- pure-ftpd.conf:
  ```
  MaxDiskUsage        <percentage>
  ```

- Debian/Ubuntu Package:
  ```
  $ echo <percentage> | sudo tee /etc/pure-ftpd/conf/MaxDiskUsage
  ```

- 使用例:  
```
# ディスク使用量が95%を超えるとそれ以上のアップロードを禁止する
$ pure-ftpd -k 95
```

### NoTruncate

アトミックなアップロード。アップロードするファイルが既に存在するときに、そのまま上書きせずにアップロードが終わってから入れ替える。このオプションはvirtual quotaと互換性がない

- short option:
  ```
  $ pure-ftpd -0
  ```

- long option:
  ```
  $ pure-ftpd --notruncate
  ```

- pure-ftpd.conf:
  ```
  NoTruncate        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/NoTruncate
  ```

## クライアントとの互換性

### BrokenClientsCompatibility

RFCに準拠しないFTPクライアントソフトとの互換性を優先する。FFFTPのNLST問題をサーバ側での解決する場合などに有効

- short option:
  ```
  $ pure-ftpd -b
  ```

- long option:
  ```
  $ pure-ftpd --brokenclientscompatibility
  ```

- pure-ftpd.conf:
  ```
  BrokenClientsCompatibility        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/BrokenClientsCompatibility
  ```

### ClientCharset

FTPクライアント側のファイル名のデフォルトの文字コードを指定する

- short option:
  ```
  $ pure-ftpd -9 <charset>
  ```

- long option:
  ```
  $ pure-ftpd --clientcharset=<charset>
  ```

- pure-ftpd.conf:
  ```
  ClientCharset        <charset>
  ```

- Debian/Ubuntu Package:
  ```
  $ echo <charset> | sudo tee /etc/pure-ftpd/conf/ClientCharset
  ```

### FileSystemCharset

サーバ側のファイル名の文字コードを指定する。iconvを利用しているので、設定値は、EUC-JP CP932 ISO-2022-JP SJIS UTF-8 UTF-8-MAC等となる

- short option:
  ```
  $ pure-ftpd -8 <charset>
  ```

- long option:
  ```
  $ pure-ftpd --fscharset=<charset>
  ```

- pure-ftpd.conf:
  ```
  FileSystemCharset        <charset>
  ```

- Debian/Ubuntu Package:
  ```
  $ echo <charset> | sudo tee /etc/pure-ftpd/conf/FSCharset
  ```

## アクセス制限

### MaxClientsNumber

FTPクライアントの同時接続数の上限をclientsに設定。デフォルトでは50。-pオプション使用時は、その範囲のポートの数の半分以下にすること

- short option:
  ```
  $ pure-ftpd -c <clients>
  ```

- long option:
  ```
  $ pure-ftpd --maxclientsnumber=<clients>
  ```

- pure-ftpd.conf:
  ```
  MaxClientsNumber        <clients>
  ```

- Debian/Ubuntu Package:
  ```
  $ echo <clients> | sudo tee /etc/pure-ftpd/conf/MaxClientsNumber
  ```

### MaxClientsPerIP

接続元IPアドレスあたりの同時接続数を指定する

- short option:
  ```
  $ pure-ftpd -C <clients>
  ```

- long option:
  ```
  $ pure-ftpd --maxclientsperip=<clients>
  ```

- pure-ftpd.conf:
  ```
  MaxClientsPerIP        <clients>
  ```

- Debian/Ubuntu Package:
  ```
  $ echo <clients> | sudo tee /etc/pure-ftpd/conf/MaxClientsPerIP
  ```

### PerUserLimits

ユーザあたりの同時最大接続数、anonymousユーザの最大接続数を指定する

- short option:
  ```
  $ pure-ftpd -y <user:anon>
  ```

- long option:
  ```
  $ pure-ftpd --peruserlimits=<user:anon>
  ```

- pure-ftpd.conf:
  ```
  PerUserLimits        <user:anon>
  ```

- Debian/Ubuntu Package:
  ```
  $ echo <user> <anon> | sudo tee /etc/pure-ftpd/conf/PerUserLimits
  ```

- 使用例:  
```
# 同一ユーザーの同時接続上限が3、anonymousの同時接続上限は20
$ pure-ftpd -y 3:20 -c 15 -C 5
```

### UserBandwidth

全てのユーザの帯域幅をKB/s単位で制限する

- short option:
  ```
  $ pure-ftpd -T <bandwidth or [up]:[down]>
  ```

- long option:
  ```
  $ pure-ftpd --userbandwidth=<bandwidth or [up]:[down]>
  ```

- pure-ftpd.conf:
  ```
  UserBandwidth        <bandwidth> or <up> <down>
  ```

- Debian/Ubuntu Package:
  ```
  $ echo <bandwidth> or <up> <down> | sudo tee /etc/pure-ftpd/conf/UserBandwidth
  ```

### UserRatio

anonymousユーザ、一般ユーザの両方に対してratio比率を設定する。-aオプション使用時には該当のグループに属するユーザはこの制限は適用されない

- short option:
  ```
  $ pure-ftpd -Q <upload:download>
  ```

- long option:
  ```
  $ pure-ftpd --userratio=<upload:download>
  ```

- pure-ftpd.conf:
  ```
  UserRatio        <upload> <download>
  ```

- Debian/Ubuntu Package:
  ```
  $ echo <upload> <download> | sudo tee /etc/pure-ftpd/conf/UserRatio
  ```

## FXP

### AllowAnonymousFXP

認証ユーザとanonymousユーザの両方にFXPの使用を許可する

- short option:
  ```
  $ pure-ftpd -W
  ```

- long option:
  ```
  $ pure-ftpd --allowanonymousfxp
  ```

- pure-ftpd.conf:
  ```
  AllowAnonymousFXP        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/AllowAnonymousFXP
  ```

### AllowUserFXP

認証ユーザのFXPの使用を許可する

- short option:
  ```
  $ pure-ftpd -w
  ```

- long option:
  ```
  $ pure-ftpd --allowuserfxp
  ```

- pure-ftpd.conf:
  ```
  AllowUserFXP        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/AllowUserFXP
  ```

## その他

### Daemonize

バックグラウンドに切り離して起動する

- short option:
  ```
  $ pure-ftpd -B
  ```

- long option:
  ```
  $ pure-ftpd --daemonize
  ```

- pure-ftpd.conf:
  ```
  Daemonize        yes
  ```

- Debian/Ubuntu Package:
  ```
  $ echo yes | sudo tee /etc/pure-ftpd/conf/Daemonize
  ```

### FortunesFile

ログイン時に<file>からランダムに選ばれたメッセージを表示する

- short option:
  ```
  $ pure-ftpd -F <file>
  ```

- long option:
  ```
  $ pure-ftpd --fortunesfile=<file>
  ```

- pure-ftpd.conf:
  ```
  FortunesFile        <file>
  ```

- Debian/Ubuntu Package:
  ```
  $ echo <file> | sudo tee /etc/pure-ftpd/conf/FortunesFile
  ```

### PIDFile

pidファイルの場所を指定する。--with-nonrootでビルドしていなければ、デフォルト値は/var/run/pure-ftpd.pid

- short option:
  ```
  $ pure-ftpd -g <pid file>
  ```

- long option:
  ```
  $ pure-ftpd --pidfile=<pid file>
  ```

- pure-ftpd.conf:
  ```
  PIDFile        <pid file>
  ```

- Debian/Ubuntu Package:
  ```
  非対応
  「/var/run/pure-ftpd/pure-ftpd.pid」に固定
  ```

