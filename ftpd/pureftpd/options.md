# PureFTPd設定オプション一覧

対応version 1.0.*


## PureFTPdの設定について

- PureFTPdの設定は、**pure-ftpd(8)**にコマンドラインオプションとその引数を渡すことで可能である
- 一方で**pure-ftpd.conf**という設定ファイルを使うこともできる
- version 1.0.44から、**pure-ftpd(8)**に**pure-ftpd.conf**を引数として指定できるようになった
```
$ pure-ftpd /path/to/pure-ftpd.conf
```

- version 1.0.44よりも古いバージョンでは、**pure-config.pl**または**pure-config.py**といったwrapperスクリプトを中継することで**pure-ftpd.conf**の設定値をコマンドラインオプションに変換する仕組みとなっている
```
$ pure-config.pl /path/to/pure-ftpd.conf
```

- DebianやUbuntuのDebパッケージでは**/etc/pure-ftpd/conf**ディレクトリ配下にファイルを配置して設定する。詳細は`man pure-ftpd-wrapper`


## TODO

- &lt;と&gt;を修正する
- 基本表記と例示の書き方を見直す
- Debian/Ubuntuパッケージに対応する
- 最新バージョンに対応させる
- 分類と並び順を再考する


## INDEX

### pure-ftpd.conf, or Debian/Ubuntu Package

| [AllowAnonymousFXP](#AllowAnonymousFXP) |
[AllowDotFiles](#AllowDotFiles) |
[AllowUserFXP](#AllowUserFXP) |
[AltLog](#AltLog) |
[AnonymousBandwidth](#AnonymousBandwidth) |
[AnonymousCanCreateDirs](#AnonymousCanCreateDirs) |
[AnonymousCantUpload](#AnonymousCantUpload) |
[AnonymousOnly](#AnonymousOnly) |
[AnonymousRatio](#AnonymousRatio) |
[AntiWarez](#AntiWarez) |
[AutoRename](#AutoRename) |
[Bind](#Bind) |
[BrokenClientsCompatibility](#BrokenClientsCompatibility) |
[CallUploadScript](#CallUploadScript) |
[ChrootEveryone](#ChrootEveryone) |
[ClientCharset](#ClientCharset) |
[CreateHomeDir](#CreateHomeDir) |
[CustomerProof](#CustomerProof) |
[Daemonize](#Daemonize) |
[DisplayDotFiles](#DisplayDotFiles) |
[DontResolve](#DontResolve) |
[ExtAuth](#Authentication) |
[FileSystemCharset](#FileSystemCharset) |
[ForcePassiveIP](#ForcePassiveIP) |
[FortunesFile](#FortunesFile) |
[IPV4Only](#IPV4Only) |
[IPV6Only](#IPV6Only) |
[KeepAllFiles](#KeepAllFiles) |
[LDAPConfigFile](#Authentication) |
[LimitRecursion](#LimitRecursion) |
[LogPID](#LogPID) |
[MaxClientsNumber](#MaxClientsNumber) |
[MaxClientsPerIP](#MaxClientsPerIP) |
[MaxDiskUsage](#MaxDiskUsage) |
[MaxIdleTime](#MaxIdleTime) |
[MaxLoad](#MaxLoad) |
[MinUID](#MinUID) |
[MySQLConfigFile](#Authentication) |
[NATmode](#NATmode) |
[NoAnonymous](#NoAnonymous) |
[NoChmod](#NoChmod) |
[NoRename](#NoRename) |
[NoTruncate](#NoTruncate) |
[PAMAuthentication](#Authentication) |
[PassivePortRange](#PassivePortRange) |
[PerUserLimits](#PerUserLimits) |
[PGSQLConfigFile](#Authentication) |
[PIDFile](#PIDFile) |
[ProhibitDotFilesRead](#ProhibitDotFilesRead) |
[ProhibitDotFilesWrite](#ProhibitDotFilesWrite) |
[PureDB](#Authentication) |
[Quota](#Quota) |
[SyslogFacility](#SyslogFacility) |
[TLS](#TLS) |
[TrustedGID](#TrustedGID) |
[TrustedIP](#TrustedIP) |
[Umask](#Umask) |
[UnixAuthentication](#Authentication) |
[UserBandwidth](#UserBandwidth) |
[UserRatio](#UserRatio) |
[VerboseLog](#VerboseLog) |


---
### short option

| [-0](#NoTruncate) |
[-1](#LogPID) |
[-4](#IPV4Only) |
[-6](#IPV6Only) |
[-8](#FileSystemCharset) |
[-9](#ClientCharset) |
[-a](#TrustedGID) |
[-A](#ChrootEveryone) |
[-b](#BrokenClientsCompatibility) |
[-B](#Daemonize) |
[-c](#MaxClientsPerIP) |
[-C](#MaxClientsNumber) |
[-d](#VerboseLog) |
[-D](#DisplayDotFiles) |
[-e](#AnonymousOnly) |
[-E](#NoAnonymous) |
[-f](#SyslogFacility) |
[-F](#FortunesFile) |
[-g](#PIDFile) |
[-G](#NoRename) |
[-h](#Help) |
[-H](#DontResolve) |
[-i](#AnonymousCantUpload) |
[-I](#MaxIdleTime) |
[-j](#CreateHomeDir) |
[-k](#MaxDiskUsage) |
[-K](#KeepAllFiles) |
[-l](#Authentication) |
[-L](#LimitRecursion) |
[-m](#MaxLoad) |
[-M](#AnonymousCanCreateDirs) |
[-n](#Quota) |
[-N](#NATmode) |
[-o](#CallUploadScript) |
[-O](#AltLog) |
[-p](#PassivePortRange) |
[-P](#ForcePassiveIP) |
[-q](#AnonymousRatio) |
[-Q](#UserRatio) |
[-r](#AutoRename) |
[-R](#NoChmod) |
[-s](#AntiWarez) |
[-S](#Bind) |
[-t](#AnonymousBandwidth) |
[-T](#UserBandwidth) |
[-u](#MinUID) |
[-U](#Umask) |
[-v](#Bonjour) |
[-V](#TrustedIP) |
[-w](#AllowUserFXP) |
[-W](#AllowAnonymousFXP) |
[-x](#ProhibitDotFilesWrite) |
[-X](#ProhibitDotFilesRead) |
[-y](#PerUserLimits) |
[-Y](#TLS) |
[-z](#AllowDotFiles) |
[-Z](#CustomerProof) |


---
### long option

| [--allowanonymousfxp](#AllowAnonymousFXP) |
[--allowdotfiles](#AllowDotFiles) |
[--allowuserfxp](#AllowUserFXP) |
[--altlog](#AltLog) |
[--anonymousbandwidth](#AnonymousBandwidth) |
[--anonymouscancreatedirs](#AnonymousCanCreateDirs) |
[--anonymouscantupload](#AnonymousCantUpload) |
[--anonymousonly](#AnonymousOnly) |
[--anonymousratio](#AnonymousRatio) |
[--antiwarez](#AntiWarez) |
[--autorename](#AutoRename) |
[--bind](#Bind) |
[--brokenclientscompatibility](#BrokenClientsCompatibility) |
[--bonjour](#Bonjour) |
[--chrooteveryone](#ChrootEveryone) |
[--clientcharset](#ClientCharset) |
[--createhomedir](#CreateHomeDir) |
[--customerproof](#CustomerProof) |
[--daemonize](#Daemonize) |
[--displaydotfiles](#DisplayDotFiles) |
[--dontresolve](#DontResolve) |
[--fscharset](#FileSystemCharset) |
[--forcepassiveip](#ForcePassiveIP) |
[--fortunesfile](#FortunesFile) |
[--help](#Help) |
[--ipv4only](#IPV4Only) |
[--ipv6only](#IPV6Only) |
[--keepallfiles](#KeepAllFiles) |
[--limitrecursion](#LimitRecursion) |
[--login](#Authentication) |
[--logpid](#LogPID) |
[--maxclientsnumber](#MaxClientsNumber) |
[--maxclientsperip](#MaxClientsPerIP) |
[--maxdiskusagepct](#MaxDiskUsage) |
[--maxidletime](#MaxIdleTime) |
[--maxload](#MaxLoad) |
[--minuid](#MinUID) |
[--natmode](#NATmode) |
[--noanonymous](#NoAnonymous) |
[--nochmod](#NoChmod) |
[--norename](#NoRename) |
[--notruncate](#NoTruncate) |
[--passiveportrange](#PassivePortRange) |
[--peruserlimits](#PerUserLimits) |
[--pidfile](#PIDFile) |
[--prohibitdotfilesread](#ProhibitDotFilesRead) |
[--prohibitdotfileswrite](#ProhibitDotFilesWrite) |
[--quota](#Quota) |
[--syslogfacility](#SyslogFacility) |
[--tls](#TLS) |
[--trustedgid](#TrustedGID) |
[--trustedip](#TrustedIP) |
[--umask](#Umask) |
[--uploadscript](#CallUploadScript) |
[--userbandwidth](#UserBandwidth) |
[--userratio](#UserRatio) |
[--verboselog](#VerboseLog) |


---

## 使い方

### Help

pure-ftpdで有効なオプションの一覧を表示する

- short option
```
$ pure-ftpd -h
```

-  long option
```
$ pure-ftpd --help
```

## スタンドアロン起動時にのみ有効な機能

### IPV4Only

IPv4接続のみ受け付ける

- short option
```
$ pure-ftpd -4
```

-  long option
```
$ pure-ftpd --ipv4only
```

-  pure-ftpd.conf
```
IPV4Only        yes
```

-  Debian/Ubuntu Package
```
$ echo yes | sudo tee /etc/pure-ftpd/conf/IPV4Only
```

### IPV6Only

IPv6接続のみ受け付ける

- short option
```
$ pure-ftpd -6
```

-  long option
```
$ pure-ftpd --ipv6only
```

-  pure-ftpd.conf
```
IPV6Only        yes
```

-  Debian/Ubuntu Package
```
$ echo yes | sudo tee /etc/pure-ftpd/conf/IPV6Only
```

### Daemonize

バックグラウンドに切り離して起動する

- short option
```
$ pure-ftpd -B
```

-  long option
```
$ pure-ftpd --daemonize
```

-  pure-ftpd.conf
```
Daemonize        yes
```

-  Debian/Ubuntu Package
```
$ echo yes | sudo tee /etc/pure-ftpd/conf/Daemonize
```

### PIDFile

pidファイルの場所を指定する。--with-nonrootでビルドしていなければ、デフォルトでは/var/run/pure-ftpd.pid

- short option
```
$ pure-ftpd -g <pid file>
```

-  long option
```
$ pure-ftpd --pidfile <pid file>
```

-  pure-ftpd.conf
```
PIDFile　　　　　　　　<pid file>
```

-  Debian/Ubuntu Package  
**/var/run/pure-ftpd/pure-ftpd.pid**に固定されている


### Bind

サーバが受け付けるIPアドレス(またはホスト名)とポート番号(または/etc/servicesのサービス名)を指定する

- short option
```
$ pure-ftpd -S [IP][,Port]
```

-  long option
```
$ pure-ftpd --bind [IP][,Port]
```

-  pure-ftpd.conf
```
    Bind        [IP][,Port]
```

-  Debian/Ubuntu Package  
```
$ echo [IP][,Port] | sudo tee /etc/pure-ftpd/conf/Bind
```

例
- IPアドレス172.0.0.1へのアクセスのみ受け付ける
```
$ pure-ftpd -S 171.0.0.1
```

- ftp.example.comのポート8021へのアクセスを受け付ける
```
$ pure-ftpd -S ftp.example.com,8021
```

- 通常のポート番号21ではなくポート番号8021へのアクセスを受け付ける
```
$ pure-ftpd -S ,8021
```

## 認証

### NoAnonymous

一般ユーザのみログインを許可し、anonymousユーザのログインを禁止する

- short option
```
$ pure-ftpd -E
```

-  long option
```
$ pure-ftpd --noanonymous
```

-  pure-ftpd.conf
```
NoAnonymous        yes
```

-  Debian/Ubuntu Package  
```
$ echo yes | sudo tee /etc/pure-ftpd/conf/NoAnonymous
```

### Authentication

認証データベースの種類とその接続設定ファイルを指定する

- short option
```
$ pure-ftpd -l <unix|pam|puredb|mysql|pgsql|ldap|extauth>[:config file]
```

-  long option
```
$ pure-ftpd --login <unix|pam|puredb|mysql|pgsql|ldap|extauth>[:file]
```

-  pure-ftpd.conf
```
UnixAuthentication        yes
PAMAuthentication         yes
PureDB             <file>
MySQLConfigFile    <file>
PGSQLConfigFile    <file>
LDAPConfigFile     <file>
ExtAuth            <file>
```

-  Debian/Ubuntu Package  
	- unix認証
	
		```
		$ echo yes | sudo tee /etc/pure-ftpd/conf/UnixAuthentication
		$ sudo ln -s ../conf/UnixAuthentication /etc/pure-ftpd/auth/65unix
		```


	- PAM認証
	
		```
		$ echo yes | sudo tee /etc/pure-ftpd/conf/PAMAuthentication
		$ sudo ln -s ../conf/PAMAuthentication /etc/pure-ftpd/auth/70pam
		```

	- PureDB認証
	
		```
		$ echo <file> | sudo tee /etc/pure-ftpd/conf/PureDB
		$ sudo ln -s ../conf/PureDB /etc/pure-ftpd/auth/50puredb
		```

	- MySQL認証
	
		```
		$ echo <file> | sudo tee /etc/pure-ftpd/conf/MySQLConfigFile
		$ sudo ln -s ../conf/MySQLConfigFile /etc/pure-ftpd/auth/50mysql
		```

	- PostgreSQL認証
	
		```
		$ echo <file> | sudo tee /etc/pure-ftpd/conf/PGSQLConfigFile
		$ sudo ln -s ../conf/PGSQLConfigFile /etc/pure-ftpd/auth/50pgsql
		```

	- LDAP認証
	
		```
		$ echo <file> | sudo tee /etc/pure-ftpd/conf/LDAPConfigFile
		$ sudo ln -s ../conf/LDAPConfigFile /etc/pure-ftpd/auth/50ldap
		```

	- ExtAUTH認証
	
		```
		$ echo <file> | sudo tee /etc/pure-ftpd/conf/ExtAuth
		$ sudo ln -s ../conf/ExtAuth /etc/pure-ftpd/auth/50extauth
		```

例
- /etc/pure/pwd.pdbファイルにPureDB形式で登録されたユーザのログインを許可する
```
$ pure-ftpd -l puredb:/etc/pure/pwd.pdb
```

- まず/etc/pure/ldap.confファイルで設定されたLDAPによる認証を行い、それをパスしないユーザについてはPAMによる認証を行う
```
$ pure-ftpd -l ldap:/etc/pure/ldap.conf -l pam
```

### MinUID

指定したuid未満のuidのユーザのログインを禁止する

- short option
```
$ pure-ftpd -u <uid>
```

-  long option
```
$ pure-ftpd --minuid <uid>
```

-  pure-ftpd.conf
```
MinUID        <uid>
```

-  Debian/Ubuntu Package  
```
$ echo <uid> | sudo tee /etc/pure-ftpd/conf/MinUID
```

### TLS

AUTH TLSを設定するオプション。デフォルトでは0

- short option
```
    $ pure-ftpd -Y (0|1|2)
```

-  long option
```
    $ pure-ftpd --tls (0|1|2)
```

-  pure-ftpd.conf
```
    TLS        (0|1|2)
```

-  Debian/Ubuntu Package  
```
$ echo (0|1|2) | sudo tee /etc/pure-ftpd/conf/TLS
```

例
- AUTH TLSを使用しない
```
$ pure-ftpd -Y 0
```

- AUTH TLSと非暗号セッションの両方を許可する
```
$ pure-ftpd -Y 1
```

- AUTH TLSのみ許可する
```
$ pure-ftpd -Y 2
```

## ファイルアクセス

### TrustedGID

rootとgidに指定したグループに所属するユーザ以外のユーザをchrootする

- short option
```
$ pure-ftpd -a <gid>
```

-  long option
```
$ pure-ftpd --trustedgid <gid>
```

-  pure-ftpd.conf
```
TrustedGID        <gid>
```

-  Debian/Ubuntu Package  
```
$ echo <gid> | sudo tee /etc/pure-ftpd/conf/TrustedGID
```


### ChrootEveryone

root以外の全ユーザをchrootする

- short option
```
$ pure-ftpd -A
```

-  long option
```
$ pure-ftpd --chrooteveryone
```

-  pure-ftpd.conf
```
ChrootEveryone        yes
```

-  Debian/Ubuntu Package  
```
$ echo yes | sudo tee /etc/pure-ftpd/conf/ChrootEveryone
```
    

### NoRename

ファイルの移動、ファイル名変更を禁止する

- short option
```
$ pure-ftpd -G
```

-  long option
```
$ pure-ftpd --norename
```

-  pure-ftpd.conf
```
NoRename        yes
```

-  Debian/Ubuntu Package  
```
$ echo yes | sudo tee /etc/pure-ftpd/conf/NoRename
```
    

### NoChmod

root以外のユーザによるchmodコマンドの使用を禁止する

- short option
```
$ pure-ftpd -R
```

-  long option
```
$ pure-ftpd --nochmod
```

-  pure-ftpd.conf
```
NoChmod        yes
```

-  Debian/Ubuntu Package  
```
$ echo yes | sudo tee /etc/pure-ftpd/conf/NoChmod
```
    

### Umask

ファイルとディレクトリ作成時のumaskを指定する。デフォルトは133と022

- short option
```
$ pure-ftpd -U <umask file:umask dir>
```

- long option
```
$ pure-ftpd --umask <umask file:umask dir>
```

- pure-ftpd.conf
```
Umask        <umask file:umask dir>
```

- Debian/Ubuntu Package  
```
$ echo <umask file:umask dir> | sudo tee /etc/pure-ftpd/conf/Umask
```


例
- ファイルのumaskを177、ディレクトリのumaskを077にする
```
$ pure-ftpd -U 177:077
```


### ProhibitDotFilesWrite

ドットファイルへの一般ユーザの上書きと作成、削除を禁止する。anonymousユーザの場合は、セキュリティ上の理由(.rhostsや.sshなど)でドットファイルへのアクセスはデフォルトで禁止されている

    # short option
    $ pure-ftpd -x

    # long option
    $ pure-ftpd --prohibitdotfileswrite

    # pure-ftpd.conf
    ProhibitDotFilesWrite

### ProhibitDotFilesRead

前項の-xオプションの機能に加えて、ドットファイルを読むことも禁止する。~/.sshのようなドットで始まるディレクトリの場合はcdすることができなくなる

    # short option
    $ pure-ftpd -X

    # long option
    $ pure-ftpd --prohibitdotfilesread

    # pure-ftpd.conf
    ProhibitDotFilesRead

## 利便性

### NoTruncate

アトミックなアップロード。アップロードするファイルが既に存在するときに、そのまま上書きせずにアップロードが終わってから入れ替える。このオプションはvirtual quotaと互換性がない


    # short option
    $ pure-ftpd -0

    # long option
    $ pure-ftpd --notruncate

    # pure-ftpd.conf
    NoTruncate

### BrokenClientsCompatibility

RFCに準拠しないFTPクライアントソフトとの互換性を優先する&lt;br&gt;
FFFTPのNLST問題をサーバ側での解決する場合などに有効

    # short option
    $ pure-ftpd -b

    # long option
    $ pure-ftpd --brokenclientscompatibility

    # pure-ftpd.conf
    BrokenClientsCompatibility

### DisplayDotFiles

クライアント側が-aオプションをつけなくてもファイル一覧表示時にデフォルトでドットファイルを表示する

    # short option
    $ pure-ftpd -D

    # long option
    $ pure-ftpd --displaydotfiles

    # pure-ftpd.conf
    DisplayDotFiles

### CreateHomeDir

ユーザログイン時にホームディレクトリが存在しない場合に自動的に作成する

    # short option
    $ pure-ftpd -j

    # long option
    $ pure-ftpd --createhomedir

    # pure-ftpd.conf
    CreateHomeDir

### CustomerProof

ユーザが起こしがちな過ちを防ぐ。今のところ、ユーザがchmodで自らのファイルやディレクトリにアクセスできなくなるのを防止する

    # short option
    $ pure-ftpd -Z

    # long option
    $ pure-ftpd --customerproof

    # pure-ftpd.conf
    CustomerProof

## 負荷の制御など

### MaxIdleTime

タイムアウトまでの無通信時間の最大値を分単位で設定。デフォルトでは15分

    # short option
    $ pure-ftpd -I &lt;time&gt;

    # long option
    $ pure-ftpd --maxidletime &lt;time&gt;

    # pure-ftpd.conf
    MaxIdleTime        &lt;time&gt;

### MaxDiskUsage

ディスクの使用量が指定したパーセンテージを超えた場合に、それ以上のアップロードを禁止する

    # short option
    $ pure-ftpd -k &lt;percentage&gt;

    # long option
    $ pure-ftpd --maxdiskusagepct &lt;percentage&gt;

    # pure-ftpd.conf
    MaxDiskUsage        &lt;percentage&gt;

例
```
# ディスク使用量が95%を超えるとそれ以上のアップロードを禁止する
$ pure-ftpd -k 95
```

### ファイル一覧表示の数の抑制

ファイル一覧に表示するファイルの数と(-Rオプションによる再帰的表示時の)サブディレクトリの深度の上限を設定する。FTPクライアント側が特定ディレクトリ配下のファイル情報を再帰的に一気に取得するような仕様の場合は、この設定値を緩和する必要が生じる可能性がある。デフォルトでは2000:5

    # short option
    $ pure-ftpd -L &lt;max files:max depth&gt;

    # long option
    $ pure-ftpd --limitrecursion &lt;max files:max depth&gt;

    # pure-ftpd.conf
    LimitRecursion        &lt;max files:max depth&gt;

### Quota

virtual quotaを使用する。.ftpqutoaファイルが作成され、ユーザごとにホームディレクトリ内のファイル数の最大値と容量の最大値を制限する

    # short option
    $ pure-ftpd -n &lt;max files:max size&gt;

    # long option
    $ pure-ftpd --quota &lt;max files:max size&gt;

    # pure-ftpd.conf
    Quota        &lt;max files:max size&gt;

## 同時アクセス制限

### MaxClientsNumber

FTPクライアントの同時接続数の上限をclientsに設定。デフォルトでは50。-pオプション使用時は、その範囲のポートの数の半分以下にすること

    # short option
    $ pure-ftpd -c &lt;clients&gt;

    # long option
    $ pure-ftpd --maxclientsnumber &lt;clients&gt;

    # pure-ftpd.conf
    MaxClientsNumber        &lt;clients&gt;

### MaxClientsPerIP

接続元IPアドレスあたりの同時接続数を指定する

    # short option
    $ pure-ftpd -C &lt;clients&gt;

    # long option
    $ pure-ftpd --maxclientsperip &lt;clients&gt;

    # pure-ftpd.conf
    MaxClientsPerIP        &lt;clients&gt;

### MaxClientsPerIP

接続元IPアドレスあたりの同時接続数を指定する

    # short option
    $ pure-ftpd -C &lt;clients&gt;

    # long option
    $ pure-ftpd --maxclientsperip &lt;clients&gt;

    # pure-ftpd.conf
    MaxClientsPerIP        &lt;clients&gt;

### PerUserLimits

ユーザあたりの同時最大接続数、anonymousユーザの最大接続数を指定する

    # short option
    $ pure-ftpd -y &lt;user:anon&gt;

    # long option
    $ pure-ftpd --peruserlimits &lt;user:anon&gt;

    # pure-ftpd.conf
    PerUserLimits        &lt;user:anon&gt;

例
```
# 全体の上限が15セッション
# 同一IPからのアクセスの上限が5
# 同じユーザアカウントからのアクセスの上限が3
# anonymous接続の上限は20
$ pure-ftpd -y &lt;3:20&gt; -c &lt;15&gt; -C &lt;5&gt;
```

### AnonymousBandwidth

anonymousユーザの帯域幅をKB/s単位で制限する

    # short option
    $ pure-ftpd -t &lt;bandwidth or [up]:[down]&gt;

    # long option
    $ pure-ftpd --anonymousbandwidth &lt;bandwidth or [up]:[down]&gt;

    # pure-ftpd.conf
    AnonymousBandwidth        &lt;bandwidth or [up]:[down]&gt;

### UserBandwidth

全てのユーザの帯域幅をKB/s単位で制限する

    # short option
    $ pure-ftpd -T &lt;bandwidth or [up]:[down]&gt;

    # long option
    $ pure-ftpd --userbandwidth &lt;bandwidth or [up]:[down]&gt;

    # pure-ftpd.conf
    UserBandwidth        &lt;bandwidth or [up]:[down]&gt;

## ログ

### LogPID

プロセスIDをSyslogへの出力に加える。-f &lt;none&gt;が指定された場合にはこのオプションは無視される

    # short option
    $ pure-ftpd -1

    # long option
    $ pure-ftpd --logpid

    # pure-ftpd.conf
    LogPID

### VerboseLog

FTPクライアント側の全コマンドをSyslogに出力する。-d -dのように二重に指定するとサーバ側の応答も出力する

    # short option
    $ pure-ftpd -d

    # long option
    $ pure-ftpd --verboselog

    # pure-ftpd.conf
    VerboseLog

### SyslogFacility

Syslogへ出力する際のfacilityを指定する。デフォルトではftp( or local2 )。noneを指定するとSyslogへの出力を行わない

    # short option
    $ pure-ftpd -f &lt;facility&gt;

    # long option
    $ pure-ftpd --syslogfacility &lt;facility&gt;

    # pure-ftpd.conf
    SyslogFacility        &lt;facility&gt;

### DontResolve

FTPクライアントの名前解決を行わずにIPアドレスを出力する

    # short option
    $ pure-ftpd -H

    # long option
    $ pure-ftpd --dontresolve

    # pure-ftpd.conf
    DontResolve

### AltLog

転送ログを指定したファイル・フォーマットで出力する

    # short option
    $ pure-ftpd -O &lt;format:file&gt;

    # long option
    $ pure-ftpd --altlog &lt;format:file&gt;

    # pure-ftpd.conf
    AltLog        &lt;format:file&gt;

例
```
# Apache風の転送ログを出力する
$ pure-ftpd -O &lt;clf:/var/log/pureftpd.log&gt;
# 独自形式の転送ログを出力する
$ pure-ftpd -O &lt;stats:/var/log/pureftpd.log&gt;
# IIS風の転送ログを出力する
$ pure-ftpd -O &lt;w3c:/var/log/pureftpd.log&gt;
# xferlog形式(wu-ftpd等と同じ)で転送ログを出力する
$ pure-ftpd -O &lt;xferlog:/var/log/pureftpd.log&gt;
```

## AnonymousFTP

### AnonymousOnly

Anonymous専用FTPサーバにする。anonymous以外のユーザはログインできない

    # short option
    $ pure-ftpd -e

    # long option
    $ pure-ftpd --anonymousonly

    # pure-ftpd.conf
    AnonymousOnly

### AnonymousCantUpload

パーミッションに関わらずanonymousユーザのアップロードを禁止する

    # short option
    $ pure-ftpd -i

    # long option
    $ pure-ftpd --anonymouscantupload

    # pure-ftpd.conf
    AnonymousCantUpload

### MaxLoad

ロードアベレージが&lt;load&gt;を超えるときにanonymousユーザのダウンロードを禁止する。ファイル一覧表示とアップロードは可能

    # short option
    $ pure-ftpd -m &lt;load&gt;

    # long option
    $ pure-ftpd --maxload &lt;load&gt;

    # pure-ftpd.conf
    MaxLoad        &lt;load&gt;

### AnonymousCanCreateDirs

anonymousユーザのディレクトリ作成を許可する

    # short option
    $ pure-ftpd -M

    # long option
    $ pure-ftpd --anonymouscancreatedirs

    # pure-ftpd.conf
    AnonymousCanCreateDirs

### AntiWarez

anonymousユーザが「ftp」ユーザ所有のファイルのダウンロードを禁止する。つまり、あるanonymousユーザがアップロードしたファイルを別のanonymousユーザがダウンロードすることを防ぐということ。warezサイト化防止のためのオプション

    # short option
    $ pure-ftpd -s

    # long option
    $ pure-ftpd --antiwarez

    # pure-ftpd.conf
    AntiWarez

### TrustedIP

管理用のIPアドレスを指定。このIPアドレスへアクセスしてきた場合は一般ユーザのみログインでき、他のIPアドレス以外へアクセスしてきた場合はanonymousユーザのみログインできる

    # short option
    $ pure-ftpd -V &lt;ip&gt;

    # long option
    $ pure-ftpd --trustedip &lt;ip&gt;

    # pure-ftpd.conf
    TrustedIP        &lt;ip&gt;

### AllowDotFiles

anonymousユーザに対して、ドットで始まる名前のファイルとディレクトリへのreadアクセスを許可する

    # short option
    $ pure-ftpd -z

    # long option
    $ pure-ftpd --allowdotfiles

    # pure-ftpd.conf
    AllowDotFiles

## NAT,パケットフィルタ

### NATmode

passiveモードを禁止する

    # short option
    $ pure-ftpd -N

    # long option
    $ pure-ftpd --natmode

    # pure-ftpd.conf
    NATmode

### PassivePortRange

passiveモードで使用するポートの範囲を指定する

    # short option
    $ pure-ftpd -p &lt;min port:max port&gt;

    # long option
    $ pure-ftpd --passiveportrange &lt;min port:max port&gt;

    # pure-ftpd.conf
    PassivePortRange        &lt;min port:max port&gt;

例
```
# 使用するポートの範囲を4000〜5000にする
$ pure-ftpd -O -p 4000:5000
```

### ForcePassiveIP

PASV/EPSV/SPSVコマンド(要するにpassiveモード)への応答に使うIPアドレスを指定する。DDNS利用時はホスト名を指定する

    # short option
    $ pure-ftpd -P &lt;IP or Host&gt;

    # long option
    $ pure-ftpd --forcepassiveip &lt;IP or Host&gt;

    # pure-ftpd.conf
    ForcePassiveIP        &lt;IP or Host&gt;

## AnonymousRatio

### anonymousのratio比率

anonymousユーザのratio比率を設定する。-q 1:5なら1MBのファイルを献上する見返りに5MBのファイルを入手できる

    # short option
    $ pure-ftpd -q &lt;upload:download&gt;

    # long option
    $ pure-ftpd --anonymousratio &lt;upload:download&gt;

    # pure-ftpd.conf
    AnonymousRatio        &lt;upload:download&gt;

### UserRatio

anonymousユーザ、一般ユーザの両方に対してratio比率を設定する。-aオプション使用時には該当のグループに属するユーザはこの制限は適用されない

    # short option
    $ pure-ftpd -Q &lt;upload:download&gt;

    # long option
    $ pure-ftpd --userratio &lt;upload:download&gt;

    # pure-ftpd.conf
    UserRatio        &lt;upload:download&gt;

## FXP

### AllowUserFXP

一般ユーザのFXPの使用を許可する

    # short option
    $ pure-ftpd -w

    # long option
    $ pure-ftpd --allowuserfxp

    # pure-ftpd.conf
    AllowUserFXP

### AllowAnonymousFXP

一般ユーザ以外にanonymousユーザにもFXPの使用を許可する

    # short option
    $ pure-ftpd -W

    # long option
    $ pure-ftpd --allowanonymousfxp

    # pure-ftpd.conf
    AllowAnonymousFXP

## 文字コード

### FileSystemCharset

サーバ側のファイル名の文字コードを指定する。iconvを利用しているので、&lt;charset&gt;の値は、EUC-JP CP932 ISO-2022-JP SJIS UTF-8 UTF-8-MAC等となる

    # short option
    $ pure-ftpd -8 &lt;charset&gt;

    # long option
    $ pure-ftpd --fscharset &lt;charset&gt;

    # pure-ftpd.conf
    FileSystemCharset        &lt;charset&gt;

### ClientCharset

FTPクライアント側のファイル名のデフォルトの文字コードを指定する

    # short option
    $ pure-ftpd -9 &lt;charset&gt;

    # long option
    $ pure-ftpd --clientcharset &lt;charset&gt;

    # pure-ftpd.conf
    ClientCharset        &lt;charset&gt;

## その他

### FortunesFile

ログイン時に&lt;file&gt;からランダムに選ばれたメッセージを表示する

    # short option
    $ pure-ftpd -F &lt;file&gt;

    # long option
    $ pure-ftpd --fortunesfile &lt;file&gt;

    # pure-ftpd.conf
    FortunesFile        &lt;file&gt;

### KeepAllFiles

ファイルの消失防止のためのオプション。ファイルの名前変更と削除を禁止し、ファイルのアップロードとアップロードのresumeは許可される。上書きについてはアップロード時のresumeのために許可されるので、-rオプションと組み合わせて使うとよい

    # short option
    $ pure-ftpd -K

    # long option
    $ pure-ftpd --keepallfiles

    # pure-ftpd.conf
    KeepAllFiles

### CallUploadScript

pure-uploadscriptを有効にする

    # short option
    $ pure-ftpd -o

    # long option
    $ pure-ftpd --uploadscript

    # pure-ftpd.conf
    CallUploadScript

### AutoRename

ファイルのアップロード時に、すでに同名のファイルが同じディレクトリに存在する場合は上書きせずにxyz.1、xyz.2などとする

    # short option
    $ pure-ftpd -r

    # long option
    $ pure-ftpd --autorename

    # pure-ftpd.conf
    AutoRename

### Bonjour

Bonjour([参考:support.apple.com](https://support.apple.com/ja-jp/bonjour))を有効にし、Bonjour名を&lt;name&gt;に設定する

    # short option
    $ pure-ftpd -v &lt;name&gt;

    # long option
    $ pure-ftpd --bonjour &lt;name&gt;

    # pure-ftpd.conf
    非対応

