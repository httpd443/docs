# PureFTPd起動時オプション及び設定項目の一覧 (version 1.0.21)

## 概要

PureFTPdの設定は、起動時にコマンドラインオプションとして指定するようになっています。しかしそれでは使い勝手が悪いので、一般的にはpure-ftpd.confに記述し、起動時にそれらの内容をコマンドラインオプションに変換する仕組みになっています。<br>
ここではpure-ftpd.confの指定と、コマンドラインオプションとの両方を併記しています。

## 記述について

- コマンド実行時のオプションは、見やすさのために説明対象のオプションのみを記すことにする
- コマンドプロンプトは「$」で統一する。root権限が必要かどうかは考慮していない
- 便宜上の簡潔さのため、pure-ftpd.confの記述内容とコマンド実行との併記については、CUI上の厳密さは無視している

## 使い方に関する項目

### オプション一覧の表示

pure-ftpdで有効なオプションの一覧を表示する

    # short option
    $ pure-ftpd -h
    
    # long option
    $ pure-ftpd --help


## スタンドアロン起動時にのみ有効な機能

### IPv4のみ

IPv4接続のみ受け付ける

    # short option
    $ pure-ftpd -4

    # long option
    $ pure-ftpd --ipv4only

    # pure-ftpd.conf
    IPV4Only        yes

### IPv6のみ

IPv6接続のみ受け付ける

    # short option
    $ pure-ftpd -6

    # long option
    $ pure-ftpd --ipv6only

    # pure-ftpd.conf
    IPV6Only        yes

### バックグラウンド起動

バックグラウンドに切り離して起動する

    # short option
    $ pure-ftpd -B

    # long option
    $ pure-ftpd --daemonize

    # pure-ftpd.conf
    Daemonize        yes

### pidファイル

pidファイルの場所を指定する。--with-nonrootでビルドしていなければ、デフォルトでは/var/run/pure-ftpd.pid

    # short option
    $ pure-ftpd -g <pid file>

    # long option
    $ pure-ftpd --pidfile <pid file>

    # pure-ftpd.conf
    PIDFile　　　　　　　　<pid file>

### IPアドレスとポート番号の指定

サーバが受け付けるIPアドレス(or ホスト名)とポート番号(or /etc/servicesのサービス名)を指定する

    # short option
    $ pure-ftpd -S [IP][,Port]

    # long option
    $ pure-ftpd --bind [IP][,Port]

    # pure-ftpd.conf
    Bind        [IP][,Port]

例
```
# IPアドレス172.0.0.1へのアクセスのみ受け付ける
$ pure-ftpd -S 171.0.0.1

# ftp.example.comのポート8021へのアクセスを受け付ける
$ pure-ftpd -S ftp.example.com,8021

# 通常のポート番号21ではなくポート番号8021へのアクセスを受け付ける
$ pure-ftpd -S ,8021
```

## 認証

### anonymous

一般ユーザのみログインを許可し、anonymousユーザのログインを禁止する

    # short option
    $ pure-ftpd -E

    # long option
    $ pure-ftpd --noanonymous

    # pure-ftpd.conf
    NoAnonymous        yes

### 認証データベース

認証データベースを指定する

    # short option
    $ pure-ftpd -l <認証DBの種類>[:file]

    # long option
    $ pure-ftpd --login <認証DBの種類>[:file]

    # pure-ftpd.conf
    UnixAuthentication
    PAMAuthentication
    PureDB        <file>
    MySQLConfigFile        <file>
    PGSQLConfigFile        <file>
    LDAPConfigFile        <file>
    ExtAuth        <file>

例
```
# /etc/pure/pwd.pdbファイルにPureDB形式で登録されたユーザのログインを許可する
$ pure-ftpd -l puredb:/etc/pure/pwd.pdb

# まず/etc/pure/ldap.confファイルで設定されたLDAPによる認証を行い、それをパスしないユーザについてはPAMによる認証を行う
$ pure-ftpd -l ldap:/etc/pure/ldap.conf -l pam
```

### ログインユーザーのuid制限

指定したuid未満のuidのユーザのログインを禁止する

    # short option
    $ pure-ftpd -u <uid>

    # long option
    $ pure-ftpd --minuid <uid>

    # pure-ftpd.conf
    MinUID        <uid>

### AUTH TLS

AUTH TLSを設定するオプション。デフォルトでは0

    # short option
    $ pure-ftpd -Y (0|1|2)

    # long option
    $ pure-ftpd --tls (0|1|2)

    # pure-ftpd.conf
    TLS        (0|1|2)

例
```
# AUTH TLSを使用しない
$ pure-ftpd -Y 0

# AUTH TLSと非暗号セッションの両方を許可する
$ pure-ftpd -Y 1

# AUTH TLSのみ許可する
$ pure-ftpd -Y 2
```

## ファイルアクセス

### 特定グループ以外のユーザーをchroot

rootとgidに指定したグループに所属するユーザ以外のユーザをchrootする

    # short option
    $ pure-ftpd -a <gid>

    # long option
    $ pure-ftpd --trustedgid <gid>

    # pure-ftpd.conf
    TrustedGID        <gid>

### root以外をchroot

root以外の全ユーザをchrootする

    # short option
    $ pure-ftpd -A

    # long option
    $ pure-ftpd --chrooteveryone

    # pure-ftpd.conf
    ChrootEveryone

### ファイルの移動、ファイル名変更の禁止

ファイルの移動、ファイル名変更を禁止する

    # short option
    $ pure-ftpd -G

    # long option
    $ pure-ftpd --norename

    # pure-ftpd.conf
    NoRename

### chmod制限

root以外のユーザによるchmodコマンドの使用を禁止する

    # short option
    $ pure-ftpd -R

    # long option
    $ pure-ftpd --nochmod

    # pure-ftpd.conf
    NoChmod

### umask

ファイルとディレクトリ作成時のumaskを指定する。デフォルトは133と022

    # short option
    $ pure-ftpd -U <umask file:umask dir>

    # long option
    $ pure-ftpd --umask <umask file:umask dir>

    # pure-ftpd.conf
    Umask        <umask file:umask dir>

例
```
# ファイルのumaskを177、ディレクトリのumaskを077にする
$ pure-ftpd -U 177:077
```

### ドットファイルの変更禁止

ドットファイルへの一般ユーザの上書きと作成、削除を禁止する。anonymousユーザの場合は、セキュリティ上の理由(.rhostsや.sshなど)でドットファイルへのアクセスはデフォルトで禁止されている

    # short option
    $ pure-ftpd -x

    # long option
    $ pure-ftpd --prohibitdotfileswrite

    # pure-ftpd.conf
    ProhibitDotFilesWrite

### ドットファイルのread禁止

前項の-xオプションの機能に加えて、ドットファイルを読むことも禁止する。~/.sshのようなドットで始まるディレクトリの場合はcdすることができなくなる

    # short option
    $ pure-ftpd -X

    # long option
    $ pure-ftpd --prohibitdotfilesread

    # pure-ftpd.conf
    ProhibitDotFilesRead

## 利便性

### アトミックなアップロード

アップロードするファイルが既に存在するときに、そのまま上書きせずにアップロードが終わってから入れ替える。このオプションはvirtual quotaと互換性がない


    # short option
    $ pure-ftpd -0

    # long option
    $ pure-ftpd --notruncate

    # pure-ftpd.conf
    NoTruncate

### FTPクライアントとの互換性

RFCに準拠しないFTPクライアントソフトとの互換性を優先する<br>
FFFTPのNLST問題をサーバ側での解決する場合などに有効

    # short option
    $ pure-ftpd -b

    # long option
    $ pure-ftpd --brokenclientscompatibility

    # pure-ftpd.conf
    BrokenClientsCompatibility

### ドットファイルのファイル一覧表示

クライアント側が-aオプションをつけなくてもファイル一覧表示時にデフォルトでドットファイルを表示する

    # short option
    $ pure-ftpd -D

    # long option
    $ pure-ftpd --displaydotfiles

    # pure-ftpd.conf
    DisplayDotFiles

### ホームディレクトリ自動作成

ユーザログイン時にホームディレクトリが存在しない場合に自動的に作成する

    # short option
    $ pure-ftpd -j

    # long option
    $ pure-ftpd --createhomedir

    # pure-ftpd.conf
    CreateHomeDir

### 操作ミス防止

ユーザが起こしがちな過ちを防ぐ。今のところ、ユーザがchmodで自らのファイルやディレクトリにアクセスできなくなるのを防止する

    # short option
    $ pure-ftpd -Z

    # long option
    $ pure-ftpd --customerproof

    # pure-ftpd.conf
    CustomerProof

## 負荷の制御など

### タイムアウト

タイムアウトまでの無通信時間の最大値を分単位で設定。デフォルトでは15分

    # short option
    $ pure-ftpd -I <time>

    # long option
    $ pure-ftpd --maxidletime <time>

    # pure-ftpd.conf
    MaxIdleTime        <time>

### アップロード抑制

ディスクの使用量が指定したパーセンテージを超えた場合に、それ以上のアップロードを禁止する

    # short option
    $ pure-ftpd -k <percentage>

    # long option
    $ pure-ftpd --maxdiskusagepct <percentage>

    # pure-ftpd.conf
    MaxDiskUsage        <percentage>

例
```
# ディスク使用量が95%を超えるとそれ以上のアップロードを禁止する
$ pure-ftpd -k 95
```

### ファイル一覧表示の数の抑制

ファイル一覧に表示するファイルの数と(-Rオプションによる再帰的表示時の)サブディレクトリの深度の上限を設定する。FTPクライアント側が特定ディレクトリ配下のファイル情報を再帰的に一気に取得するような仕様の場合は、この設定値を緩和する必要が生じる可能性がある。デフォルトでは2000:5

    # short option
    $ pure-ftpd -L <max files:max depth>

    # long option
    $ pure-ftpd --limitrecursion <max files:max depth>

    # pure-ftpd.conf
    LimitRecursion        <max files:max depth>

### virtual quota

virtual quotaを使用する。.ftpqutoaファイルが作成され、ユーザごとにホームディレクトリ内のファイル数の最大値と容量の最大値を制限する

    # short option
    $ pure-ftpd -n <max files:max size>

    # long option
    $ pure-ftpd --quota <max files:max size>

    # pure-ftpd.conf
    Quota        <max files:max size>

## 同時アクセス制限

### 同時接続FTPクライアント数の上限

FTPクライアントの同時接続数の上限をclientsに設定。デフォルトでは50。-pオプション使用時は、その範囲のポートの数の半分以下にすること

    # short option
    $ pure-ftpd -c <clients>

    # long option
    $ pure-ftpd --maxclientsnumber <clients>

    # pure-ftpd.conf
    MaxClientsNumber        <clients>

### 同時接続FTPクライアント数の上限

接続元IPアドレスあたりの同時接続数を指定する

    # short option
    $ pure-ftpd -C <clients>

    # long option
    $ pure-ftpd --maxclientsperip <clients>

    # pure-ftpd.conf
    MaxClientsPerIP        <clients>

### IPアドレスあたりの同時接続数

接続元IPアドレスあたりの同時接続数を指定する

    # short option
    $ pure-ftpd -C <clients>

    # long option
    $ pure-ftpd --maxclientsperip <clients>

    # pure-ftpd.conf
    MaxClientsPerIP        <clients>

### ユーザあたりの同時接続数

ユーザあたりの同時最大接続数、anonymousユーザの最大接続数を指定する

    # short option
    $ pure-ftpd -y <user:anon>

    # long option
    $ pure-ftpd --peruserlimits <var>user:anon</var>

    # pure-ftpd.conf
    PerUserLimits        <var>user:anon</var>

例
```
# 全体の上限が15セッション
# 同一IPからのアクセスの上限が5
# 同じユーザアカウントからのアクセスの上限が3
# anonymous接続の上限は20
$ pure-ftpd -y <3:20> -c <15> -C <5>
```

### 帯域制御（anonymous）

anonymousユーザの帯域幅をKB/s単位で制限する

    # short option
    $ pure-ftpd -t <bandwidth or [up]:[down]>

    # long option
    $ pure-ftpd --anonymousbandwidth <bandwidth or [up]:[down]>

    # pure-ftpd.conf
    AnonymousBandwidth        <bandwidth or [up]:[down]>

### 帯域制御（認証ユーザー）

全てのユーザの帯域幅をKB/s単位で制限する

    # short option
    $ pure-ftpd -T <bandwidth or [up]:[down]>

    # long option
    $ pure-ftpd --userbandwidth <bandwidth or [up]:[down]>

    # pure-ftpd.conf
    UserBandwidth        <bandwidth or [up]:[down]>

## ログ

### syslogにプロセスIDを出力

プロセスIDをSyslogへの出力に加える。-f &lt;none&gt;が指定された場合にはこのオプションは無視される

    # short option
    $ pure-ftpd -1

    # long option
    $ pure-ftpd --logpid

    # pure-ftpd.conf
    LogPID

### デバッグ用ログ出力

FTPクライアント側の全コマンドをSyslogに出力する。-d -dのように二重に指定するとサーバ側の応答も出力する

    # short option
    $ pure-ftpd -d

    # long option
    $ pure-ftpd --verboselog

    # pure-ftpd.conf
    VerboseLog

### Syslogのfacility設定

Syslogへ出力する際のfacilityを指定する。デフォルトではftp( or local2 )。noneを指定するとSyslogへの出力を行わない

    # short option
    $ pure-ftpd -f <facility>

    # long option
    $ pure-ftpd --syslogfacility <facility>

    # pure-ftpd.conf
    SyslogFacility        <facility>

### DNS名前解決の省略

FTPクライアントの名前解決を行わずにIPアドレスを出力する

    # short option
    $ pure-ftpd -H

    # long option
    $ pure-ftpd --dontresolve

    # pure-ftpd.conf
    DontResolve

### 転送ログ

転送ログを指定したファイル・フォーマットで出力する

    # short option
    $ pure-ftpd -O <format:file>

    # long option
    $ pure-ftpd --altlog <format:file>

    # pure-ftpd.conf
    AltLog        <format:file>

例
```
# Apache風の転送ログを出力する
$ pure-ftpd -O <var>clf:/var/log/pureftpd.log</var>
# 独自形式の転送ログを出力する
$ pure-ftpd -O <var>stats:/var/log/pureftpd.log</var>
# IIS風の転送ログを出力する
$ pure-ftpd -O <var>w3c:/var/log/pureftpd.log</var>
# xferlog形式(wu-ftpd等と同じ)で転送ログを出力する
$ pure-ftpd -O <var>xferlog:/var/log/pureftpd.log</var>
```

## AnonymousFTP

### Anonymous専用

Anonymous専用FTPサーバにする。anonymous以外のユーザはログインできない

    # short option
    $ pure-ftpd -e

    # long option
    $ pure-ftpd --anonymousonly

    # pure-ftpd.conf
    AnonymousOnly

### Anonymousのアップロード禁止

パーミッションに関わらずanonymousユーザのアップロードを禁止する

    # short option
    $ pure-ftpd -i

    # long option
    $ pure-ftpd --anonymouscantupload

    # pure-ftpd.conf
    AnonymousCantUpload

### 高負荷時のAnonymousダウンロード禁止

ロードアベレージが<load>を超えるときにanonymousユーザのダウンロードを禁止する。ファイル一覧表示とアップロードは可能

    # short option
    $ pure-ftpd -m <load>

    # long option
    $ pure-ftpd --maxload <load>

    # pure-ftpd.conf
    MaxLoad        <load>

### Anonymousのディレクトリ作成許可

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

### 管理用IPアドレス

管理用のIPアドレスを指定。このIPアドレスへアクセスしてきた場合は一般ユーザのみログインでき、他のIPアドレス以外へアクセスしてきた場合はanonymousユーザのみログインできる

    # short option
    $ pure-ftpd -V <ip>

    # long option
    $ pure-ftpd --trustedip <ip>

    # pure-ftpd.conf
    TrustedIP        <ip>

### 管理用IPアドレス

anonymousユーザに対して、ドットで始まる名前のファイルとディレクトリへのreadアクセスを許可する

    # short option
    $ pure-ftpd -z

    # long option
    $ pure-ftpd --allowdotfiles

    # pure-ftpd.conf
    AllowDotFiles

## NAT,パケットフィルタ

### passiveモード禁止

passiveモードを禁止する

    # short option
    $ pure-ftpd -N

    # long option
    $ pure-ftpd --natmode

    # pure-ftpd.conf
    NATmode

### passiveモード用のポート番号

passiveモードで使用するポートの範囲を指定する

    # short option
    $ pure-ftpd -p <min port:max port>

    # long option
    $ pure-ftpd --passiveportrange <min port:max port>

    # pure-ftpd.conf
    PassivePortRange        <min port:max port>

例
```
# 使用するポートの範囲を4000〜5000にする
$ pure-ftpd -O -p 4000:5000
```

### passiveモード用のポート番号

PASV/EPSV/SPSVコマンド(要するにpassiveモード)への応答に使うIPアドレスを指定する。DDNS利用時はホスト名を指定する

    # short option
    $ pure-ftpd -P <IP or Host>

    # long option
    $ pure-ftpd --forcepassiveip <IP or Host>

    # pure-ftpd.conf
    ForcePassiveIP        <IP or Host>

## Ratio

### anonymousのratio比率

anonymousユーザのratio比率を設定する。-q 1:5なら1MBのファイルを献上する見返りに5MBのファイルを入手できる

    # short option
    $ pure-ftpd -q <upload:download>

    # long option
    $ pure-ftpd --anonymousratio <upload:download>

    # pure-ftpd.conf
    AnonymousRatio        <upload:download>

### anonymousのratio比率

anonymousユーザ、一般ユーザの両方に対してratio比率を設定する。-aオプション使用時には該当のグループに属するユーザはこの制限は適用されない

    # short option
    $ pure-ftpd -Q <upload:download>

    # long option
    $ pure-ftpd --userratio <upload:download>

    # pure-ftpd.conf
    UserRatio        <upload:download>

## FXP

### FXP許可1

一般ユーザのFXPの使用を許可する

    # short option
    $ pure-ftpd -w

    # long option
    $ pure-ftpd --allowuserfxp

    # pure-ftpd.conf
    AllowUserFXP

### FXP許可2

一般ユーザ以外にanonymousユーザにもFXPの使用を許可する

    # short option
    $ pure-ftpd -W

    # long option
    $ pure-ftpd --allowanonymousfxp

    # pure-ftpd.conf
    AllowAnonymousFXP

## 文字コード

### サーバ側ファイル名の文字コード

サーバ側のファイル名の文字コードを指定する。iconvを利用しているので、&lt;charset&gt;の値は、EUC-JP CP932 ISO-2022-JP SJIS UTF-8 UTF-8-MAC等となる

    # short option
    $ pure-ftpd -8 <charset>

    # long option
    $ pure-ftpd --fscharset <charset>

    # pure-ftpd.conf
    FileSystemCharset        <charset>

### サーバ側ファイル名の文字コード

FTPクライアント側のファイル名のデフォルトの文字コードを指定する

    # short option
    $ pure-ftpd -9 <charset>

    # long option
    $ pure-ftpd --clientcharset <charset>

    # pure-ftpd.conf
    ClientCharset        <charset>

## その他

### ランダムメッセージ

ログイン時に&lt;file&gt;からランダムに選ばれたメッセージを表示する

    # short option
    $ pure-ftpd -F <file>

    # long option
    $ pure-ftpd --fortunesfile <file>

    # pure-ftpd.conf
    FortunesFile        <file>

### ファイル消失防止

ファイルの消失防止のためのオプション。ファイルの名前変更と削除を禁止し、ファイルのアップロードとアップロードのresumeは許可される。上書きについてはアップロード時のresumeのために許可されるので、-rオプションと組み合わせて使うとよい

    # short option
    $ pure-ftpd -K

    # long option
    $ pure-ftpd --keepallfiles

    # pure-ftpd.conf
    KeepAllFiles

### アップロード時の処理

pure-uploadscriptを有効にする

    # short option
    $ pure-ftpd -o

    # long option
    $ pure-ftpd --uploadscript

    # pure-ftpd.conf
    CallUploadScript

### 上書き事故防止

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
    $ pure-ftpd -v <name>

    # long option
    $ pure-ftpd --bonjour <name>

    # pure-ftpd.conf
    非対応
