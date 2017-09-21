# PureFTPd起動時オプション及び設定項目の一覧 (version 1.0.21)

## 概要

PureFTPdの設定は、起動時にコマンドラインオプションとして指定するようになっています。しかしそれでは使い勝手が悪いので、一般的にはpure-ftpd.confに記述し、起動時にそれらの内容をコマンドラインオプションに変換する仕組みになっています。<br>
ここではpure-ftpd.confの指定と、コマンドラインオプションとの両方を併記しています。

## 記述について

- コマンド名はコンパイル時のデフォルト名である「pure-ftpd」とする。コマンド実行時にPATHが通っているかどうかについては考慮していない
- コマンド実行時のオプションは実際には多数のオプションが並ぶことになるが、ここでは見やすさのために説明対象のオプションのみを記すことにする
- コマンド実行時にroot権限が必要かどうかに関係なく、コマンドプロンプトは「$」で統一する
- 便宜上の簡潔さのため、pure-ftpd.confの記述内容とコマンド実行との併記については、CUI上の厳密さは無視することにした。

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


<div id="file">
 <h3>ファイルアクセス</h3>
 <dl>
  <dt id="TrustedGID">-a <var>gid</var></dt>
  <dd class="longopt">LongOption: --trustedgid <var>gid</var></dd>
  <dd class="conffile">pure-ftpd.conf: TrustedGID <var>gid</var></dd>
  <dd>rootと<var>gid</var>に指定したグループに所属するユーザ以外のユーザをchrootする。</dd>
  <dt id="ChrootEveryone">-A</dt>
  <dd class="longopt">LongOption: --chrooteveryone</dd>
  <dd class="conffile">pure-ftpd.conf: ChrootEveryone</dd>
  <dd>root以外の全ユーザをchrootする。</dd>
  <dt id="NoRename">-G</dt>
  <dd class="longopt">LongOption: --norename</dd>
  <dd class="conffile">pure-ftpd.conf: NoRename</dd>
  <dd>ファイルの移動、ファイル名変更を禁止する。</dd>
  <dt id="NoChmod">-R</dt>
  <dd class="longopt">LongOption: --nochmod</dd>
  <dd class="conffile">pure-ftpd.conf: NoChmod</dd>
  <dd>root以外のユーザによるchmodコマンドの使用を禁止する。</dd>
  <dt id="Umask">-U <var>umask file:umask dir</var></dt>
  <dd class="longopt">LongOption: --umask <var>umask file:umask dir</var></dd>
  <dd class="conffile">pure-ftpd.conf: Umask <var>umask file:umask dir</var></dd>
  <dd>ファイルとディレクトリ作成時のumaskを指定する。デフォルトは133と022。</dd>
  <dd class="sample">使用例：<dl>
   <dt>-U 177:077</dt>
   <dd>ファイルのumaskを177、ディレクトリのumaskを077にする</dd>
  </dl></dd>
  <dt id="ProhibitDotFilesWrite">-x</dt>
  <dd class="longopt">LongOption: --prohibitdotfileswrite</dd>
  <dd class="conffile">pure-ftpd.conf: ProhibitDotFilesWrite</dd>
  <dd>ドットファイルへの一般ユーザの上書きと作成、削除を禁止する。anonymousユーザの場合は、セキュリティ上の理由(.rhostsや.sshなど)でドットファイルへのアクセスはデフォルトで禁止されている。</dd>
  <dt id="ProhibitDotFilesRead">-X</dt>
  <dd class="longopt">LongOption: --prohibitdotfilesread</dd>
  <dd class="conffile">pure-ftpd.conf: ProhibitDotFilesRead</dd>
  <dd>上記の-xオプションの機能に加えて、ドットファイルを読むことも禁止する。~/.sshのようなドットで始まるディレクトリの場合はcdすることができなくなる。</dd>
 </dl>
</div>

<div id="compat">
 <h3>利便性</h3>
 <dl>
  <dt id="NoTruncate">-0</dt>
  <dd class="longopt">LongOption: --notruncate</dd>
  <dd class="conffile">pure-ftpd.conf: NoTruncate</dd>
  <dd>アップロードするファイルが既に存在するときに、そのまま上書きせずにアップロードが終わってから入れ替える。このオプションはvirtual quotaと互換性がない。</dd>
  <dt id="BrokenClientsCompatibility">-b</dt>
  <dd class="longopt">LongOption: --brokenclientscompatibility</dd>
  <dd class="conffile">pure-ftpd.conf: BrokenClientsCompatibility</dd>
  <dd>RFCに準拠しないFTPクライアントソフトとの互換性を優先する。FFFTPのデフォルトの設定のNLSTの問題をサーバ側での解決にも有効</dd>
  <dt id="DisplayDotFiles">-D</dt>
  <dd class="longopt">LongOption: --displaydotfiles</dd>
  <dd class="conffile">pure-ftpd.conf: DisplayDotFiles</dd>
  <dd>クライアント側が-aオプションをつけなくてもファイル一覧表示時にデフォルトでドットファイルを表示する</dd>
  <dt id="CreateHomeDir">-j</dt>
  <dd class="longopt">LongOption: --createhomedir</dd>
  <dd class="conffile">pure-ftpd.conf: CreateHomeDir</dd>
  <dd>ユーザログイン時にホームディレクトリが存在しない場合に自動的に作成する</dd>
  <dt id="CustomerProof">-Z</dt>
  <dd class="longopt">LongOption: --customerproof</dd>
  <dd class="conffile">pure-ftpd.conf: CustomerProof</dd>
  <dd>ユーザが起こしがちな過ちを防ぐ。今のところ、ユーザがchmodで自らのファイルやディレクトリにアクセスできなくなるのを防止する。</dd>
 </dl>
</div>

<div id="resouce">
 <h3>負荷の制御など</h3>
 <dl>
  <dt id="MaxIdleTime">-I <var>time</var></dt>
  <dd class="longopt">LongOption: --maxidletime <var>time</var></dd>
  <dd class="conffile">pure-ftpd.conf: MaxIdleTime <var>time</var></dd>
  <dd>タイムアウトまでの無通信時間の最大値を分単位で設定。デフォルトでは15分</dd>
  <dt id="MaxDiskUsage">-k <var>percentage</var></dt>
  <dd class="longopt">LongOption: --maxdiskusagepct <var>percentage</var></dd>
  <dd class="conffile">pure-ftpd.conf: MaxDiskUsage <var>percentage</var></dd>
  <dd>ディスクの使用量が指定したパーセンテージを超えた場合に、それ以上のアップロードを禁止する。</dd>
  <dd class="sample">使用例：<dl>
   <dt>-k 95</dt>
   <dd>ディスク使用量が95%を超えるとそれ以上のアップロードを禁止する</dd>
  </dl></dd>
  <dt id="LimitRecursion">-L <var>max files:max depth</var></dt>
  <dd class="longopt">LongOption: --limitrecursion <var>max files:max depth</var></dd>
  <dd class="conffile">pure-ftpd.conf: LimitRecursion <var>max files:max depth</var></dd>
  <dd>ファイル一覧に表示するファイルの数と(-Rオプションによる再帰的表示時の)サブディレクトリの深度の上限を設定する。デフォルトでは2000:5。</dd>
  <dt id="Quota">-n <var>max files:max size</var></dt>
  <dd class="longopt">LongOption: --quota <var>max files:max size</var></dd>
  <dd class="conffile">pure-ftpd.conf: Quota <var>max files:max size</var></dd>
  <dd>virtual quotasを使用する。.ftpqutoaファイルが作成され、ユーザごとにホームディレクトリ内のファイル数の最大値と容量の最大値を制限する。</dd>
 </dl>
</div>

<div id="concurrency">
 <h3>同時アクセス制限</h3>
 <dl>
  <dt id="MaxClientsNumber">-c <var>clients</var></dt>
  <dd class="longopt">LongOption: --maxclientsnumber <var>clients</var></dd>
  <dd class="conffile">pure-ftpd.conf: MaxClientsNumber <var>clients</var></dd>
  <dd> FTPクライアントの同時接続数の上限をclientsに設定。デフォルトでは50。-pオプション使用時は、その範囲のポートの数の半分以下にすること。</dd>
  <dt id="MaxClientsPerIP">-C <var>clients</var></dt>
  <dd class="longopt">LongOption: --maxclientsperip  <var>clients</var></dd>
  <dd class="conffile">pure-ftpd.conf: MaxClientsPerIP <var>clients</var></dd>
  <dd> 接続元IPアドレスあたりの同時接続数を指定する。</dd>
  <dt id="PerUserLimits">-y <var>user:anon</var></dt>
  <dd class="longopt">LongOption: --peruserlimits <var>user:anon</var></dd>
  <dd class="conffile">pure-ftpd.conf: PerUserLimits <var>user:anon</var></dd>
  <dd>ユーザあたりの同時最大接続数、anonymousユーザの最大接続数を指定する。</dd>
  <dd class="sample">使用例：<dl>
   <dt>-y <var>3:20</var> -c <var>15</var> -C <var>5</var></dt>
   <dd>全体の上限が15セッション<br />同一IPからのアクセスの上限が5<br />同じユーザアカウントからのアクセスの上限が3<br />anonymous接続の上限は20。</dd>
 </dl>
</div>

<div id="bandwidth">
 <h3>帯域制御</h3>
 <dl>
  <dt id="AnonymousBandwidth">-t <var>bandwidth or [up]:[down]</var></dt>
  <dd class="longopt">LongOption: --anonymousbandwidth <var>bandwidth or [up]:[down]</var></dd>
  <dd class="conffile">pure-ftpd.conf: AnonymousBandwidth <var>bandwidth or [up]:[down]</var></dd>
  <dd>anonymousユーザの帯域幅をKB/s単位で制限する。</dd>
  <dt id="UserBandwidth">-T <var>bandwidth or [up]:[down]</var></dt>
  <dd class="longopt">LongOption: --userbandwidth <var>bandwidth or [up]:[down]</var></dd>
  <dd class="conffile">pure-ftpd.conf: UserBandwidth <var>bandwidth or [up]:[down]</var></dd>
  <dd>全てのユーザの帯域幅をKB/s単位で制限する。</dd>
 </dl>
</div>

<div id="log">
 <h3>ログ</h3>
 <dl>
  <dt id="LogPID">-1</dt>
  <dd class="longopt">LongOption: --logpid</dd>
  <dd class="conffile">pure-ftpd.conf: LogPID</dd>
  <dd>PIDをSyslogへの出力に加える。-f <var>none</var>が指定された場合にはこのオプションは無視される</dd>
  <dt id="VerboseLog">-d</dt>
  <dd class="longopt">LongOption: --verboselog</dd>
  <dd class="conffile">pure-ftpd.conf: VerboseLog</dd>
  <dd>FTPクライアント側の全コマンドをSyslogに出力する。-d -dのように二重に指定するとサーバ側の応答も出力する。</dd>
  <dt id="SyslogFacility">-f <var>facility</var></dt>
  <dd class="longopt">LongOption: --syslogfacility <var>facility</var></dd>
  <dd class="conffile">pure-ftpd.conf: SyslogFacility <var>facility</var></dd>
  <dd>Syslogへ出力する際のfacilityを指定する。デフォルトではftp( or local2 )。noneを指定するとSyslogへの出力を行わない</dd>
  <dt id="DontResolve">-H</dt>
  <dd class="longopt">LongOption: --dontresolve</dd>
  <dd class="conffile">pure-ftpd.conf: DontResolve</dd>
  <dd>FTPクライアントの名前解決を行わないのでDNSアクセスの手間を省略できる。Syslogへの出力ではFTPクライアントのホスト名ではなくIPアドレスを出力する。</dd>
  <dt id="AltLog">-O <var>format:file</var></dt>
  <dd class="longopt">LongOption: --altlog <var>format:file</var></dd>
  <dd class="conffile">pure-ftpd.conf: AltLog <var>format:file</var></dd>
  <dd>転送ログを指定したファイルに指定したフォーマットで出力する。</dd>
  <dd class="sample">使用例：<dl>
   <dt>-O <var>clf:/var/log/pureftpd.log</var></dt>
   <dd>Apache likeな転送ログを出力する</dd>
   <dt>-O <var>stats:/var/log/pureftpd.log</var></dt>
   <dd>独自形式の転送ログを出力する</dd>
   <dt>-O <var>w3c:/var/log/pureftpd.log</var></dt>
   <dd>IIS likeな転送ログを出力する</dd>
   <dt>-O <var>xferlog:/var/log/pureftpd.log</var></dt>
   <dd>昔ながらのxferlog形式で転送ログを出力する</dd>
  </dl></dd>
 </dl>
</div>

<div id="anonymous">
 <h3>AnonymousFTP</h3>
 <dl>
  <dt id="AnonymousOnly">-e</dt>
  <dd class="longopt">LongOption: --anonymousonly</dd>
  <dd class="conffile">pure-ftpd.conf: AnonymousOnly</dd>
  <dd>Anonymous専用FTPサーバにする。anonymous以外のユーザはログインできない</dd>
  <dt id="AnonymousCantUpload">-i</dt>
  <dd class="longopt">LongOption: --anonymouscantupload</dd>
  <dd class="conffile">pure-ftpd.conf: AnonymousCantUpload</dd>
  <dd>パーミッションに関わらずanonymousユーザのアップロードを禁止する</dd>
  <dt id="MaxLoad">-m <var>load</var></dt>
  <dd class="longopt">LongOption: --maxload <var>load</var></dd>
  <dd class="conffile">pure-ftpd.conf: MaxLoad <var>load</var></dd>
  <dd>ロードアベレージが<var>load</var>を超えるときにanonymousユーザのダウンロードを禁止する。ファイル一覧表示とアップロードは可能</dd>
  <dt id="AnonymousCanCreateDirs">-M</dt>
  <dd class="longopt">LongOption: --anonymouscancreatedirs</dd>
  <dd class="conffile">pure-ftpd.conf: AnonymousCanCreateDirs</dd>
  <dd>anonymousユーザのディレクトリ作成を許可する</dd>
  <dt id="AntiWarez">-s</dt>
  <dd class="longopt">LongOption: --antiwarez</dd>
  <dd class="conffile">pure-ftpd.conf: AntiWarez</dd>
  <dd>anonymousユーザが「ftp」ユーザ所有のファイルのダウンロードを禁止する。warezサイト化防止のためのオプション。</dd>
  <dt id="TrustedIP">-V <var>ip</var></dt>
  <dd class="longopt">LongOption: --trustedip <var>ip</var></dd>
  <dd class="conffile">pure-ftpd.conf: TrustedIP <var>ip</var></dd>
  <dd>管理用のIPアドレスを指定。このIPアドレスへアクセスしてきた場合は一般ユーザのみログインでき、他のIPアドレス以外へアクセスしてきた場合はanonymousユーザのみログインできる。</dd>
  <dt id="AllowDotFiles">-z</dt>
  <dd class="longopt">LongOption: --allowdotfiles</dd>
  <dd class="conffile">pure-ftpd.conf: AllowDotFiles</dd>
  <dd> anonymousユーザに対して、ドットで始まる名前のファイルとディレクトリへのreadアクセスを許可する。</dd>
 </dl>
</div>

<div id="nat">
 <h3>NAT,パケットフィルタ</h3>
 <dl>
  <dt id="NATmode">-N</dt>
  <dd class="longopt">LongOption: --natmode</dd>
  <dd class="conffile">pure-ftpd.conf: NATmode</dd>
  <dd>passiveモードを禁止する</dd>
  <dt id="PassivePortRange">-p <var>min port:max port</var></dt>
  <dd class="longopt">LongOption: --passiveportrange <var>min port:max port</var></dd>
  <dd class="conffile">pure-ftpd.conf: PassivePortRange <var>min port:max port</var></dd>
  <dd>passiveモードで使用するポートの範囲を指定する</dd>
  <dd class="sample">使用例：<dl>
   <dt>-p 4000:5000</dt>
   <dd>使用するポートの範囲を4000〜5000にする</dd>
  </dl></dd>
  <dt id="ForcePassiveIP">-P <var>IP or Host</var></dt>
  <dd class="longopt">LongOption: --forcepassiveip  <var>IP or Host</var></dd>
  <dd class="conffile">pure-ftpd.conf: ForcePassiveIP <var>IP or Host</var></dd>
  <dd>PASV/EPSV/SPSVコマンド(要するにpassiveモード)への応答に使うIPアドレスを指定する。DDNS利用時はホスト名を指定する。</dd>
 </dl>
</div>

<div id="ratio">
 <h3>Ratio</h3>
 <dl>
  <dt id="AnonymousRatio">-q <var>upload:download</var></dt>
  <dd class="longopt">LongOption: --anonymousratio <var>upload:download</var></dd>
  <dd class="conffile">pure-ftpd.conf: AnonymousRatio <var>upload:download</var></dd>
  <dd>anonymousユーザのratio比率を設定する。-q 1:5なら1MBのファイルを献上する見返りに5MBのファイルを入手できる。</dd>
  <dt id="UserRatio">-Q <var>upload:download</var></dt>
  <dd class="longopt">LongOption: --userratio <var>upload:download</var></dd>
  <dd class="conffile">pure-ftpd.conf: UserRatio <var>upload:download</var></dd>
  <dd>anonymousユーザ、一般ユーザの両方に対してratio比率を設定する。-aオプション使用時には該当のグループに属するユーザはこの制限は適用されない。</dd>
 </dl>
</div>

<div id="fxp">
 <h3>FXP</h3>
 <dl>
  <dt id="AllowUserFXP">-w</dt>
  <dd class="longopt">LongOption: --allowuserfxp</dd>
  <dd class="conffile">pure-ftpd.conf: AllowUserFXP</dd>
  <dd>一般ユーザのFXPの使用を許可する</dd>
  <dt id="AllowAnonymousFXP">-W</dt>
  <dd class="longopt">LongOption: --allowanonymousfxp</dd>
  <dd class="conffile">pure-ftpd.conf: AllowAnonymousFXP</dd>
  <dd>一般ユーザ以外にanonymousユーザにもFXPの使用を許可する</dd>
 </dl>
</div>

<div id="japanese">
 <h3>日本語</h3>
 <dl>
  <dt id="FileSystemCharset">-8</dt>
  <dd class="longopt">LongOption: --fscharset <var>charset</var></dd>
  <dd class="conffile">pure-ftpd.conf: FileSystemCharset <var>charset</var></dd>
  <dd>サーバ側のファイル名の文字コードを指定する。</dd>
  <dd>iconvを利用しているので、<var>charset</var>の値は、EUC-JP CP932 ISO-2022-JP SJIS UTF-8 UTF-8-MAC等・・・</dd>
  <dt id="ClientCharset">-9</dt>
  <dd class="longopt">LongOption: --clientcharset <var>charset</var></dd>
  <dd class="conffile">pure-ftpd.conf: ClientCharset <var>charset</var></dd>
  <dd>クライアント側のファイル名のデフォルトの文字コードを指定する</dd>
 </dl>
</div>

<div id="misc">
 <h3>その他</h3>
 <dl>
  <dt id="FortunesFile">-F <var>file</var></dt>
  <dd class="longopt">LongOption: --fortunesfile <var>file</var></dd>
  <dd class="conffile">pure-ftpd.conf: FortunesFile <var>file</var></dd>
  <dd>ログイン時に<var>file</var>からランダムに選ばれたメッセージを表示する。</dd>
  <dt id="KeepAllFiles">-K</dt>
  <dd class="longopt">LongOption: --keepallfiles</dd>
  <dd class="conffile">pure-ftpd.conf: KeepAllFiles</dd>
  <dd>ファイルの消失防止のためのオプション。ファイルの名前変更と削除を禁止し、ファイルのアップロードとアップロードのresumeは許可される。上書きについてはアップロード時のresumeのために許可されるので、-rオプションと組み合わせて使うとよい。</dd>
  <dt id="CallUploadScript">-o</dt>
  <dd class="longopt">LongOption: --uploadscript</dd>
  <dd class="conffile">pure-ftpd.conf: CallUploadScript</dd>
  <dd>pure-uploadscriptを使う。</dd>
  <dt id="AutoRename">-r</dt>
  <dd class="longopt">LongOption: --autorename</dd>
  <dd class="conffile">pure-ftpd.conf: AutoRename</dd>
  <dd>ファイルのアップロード時に、すでに同名のファイルが同じディレクトリに存在する時に上書きせずにxyz.1、xyz.2などとする。</dd>
  <dt id="Bonjour">-v <var>name</var></dt>
  <dd class="longopt">LongOption: --bonjour <var>name</var></dd>
  <dd class="conffile">pure-ftpd.conf: なし</dd>
  <dd>Bonjour名を<var>name</var>に設定する。</dd>
 </dl>
</div>
