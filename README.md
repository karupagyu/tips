# ■ 開発環境の構築 (windows)

## 環境変数の設定方法

コマンドプロンプト用

- PATH確認：
`echo %PATH:;=&echo.%`
- PYTHONPATHにc:\hogeを追加：
`set PYTHONPATH=%PYTHONPATH%;C:\hoge`
- PYTHONPATHをPATHに追加：
`set PATH = %PATH%;%PYTHONPATH`

## python

- [Python 3.7 のインストール（Windows上）](https://www.kkaneko.jp/tools/win/python.html)
- [MSVC ビルドツール 2019 （Build Tools for Visual Studio 2019） のインストール（Windows 上）](https://www.kkaneko.jp/tools/win/buildtool.html)
- [Visual Studio Community 2019 vesion 16.2, MSVC ビルドツールのインストール（Windows 上）](https://www.kunihikokaneko.com/tools/win/vs2019.html)
- [用語説明](https://www.kkaneko.jp/tools/tools.html)
- [Python3.7をインストールしてpathを通して、pipでパッケージを入れる](https://karupoimou.hatenablog.com/entry/2019/04/29/064646)

## CUDA

- [NVIDIA CUDA ツールキット 10.1 のインストール（Windows 上）](https://www.kunihikokaneko.com/tools/win/cuda10.html)
- [nvidia-smiコマンドの詳細ついて](https://qiita.com/miyamotok0105/items/1b34e548f96ef7d40370)

## WSL

- [WSL (Windows Subsystem for Linux)の基本メモ](https://qiita.com/rubytomato@github/items/fdfc0a76e848442f374e)
- [Windowsで環境を極力汚さずにPythonを動かす方法 (WSL利用 Windows10)](https://qiita.com/rhene/items/ff11c7850a9a7617c50f)
- [pythonコマンドでpython3を実行したい(alias変更)](https://qiita.com/houtarou/items/c7fa8006eef9e30ffad5)
- wslランチャー : コマンドプロンプトでwslと入力しても起動できる

### WSL からWindowsのバイナリを実行する方法

- [WSL から Windows側のGUIアプリを実行](https://laboradian.com/run-win-gui-exe-from-wsl)
- [WSLでWindowsのバイナリを実行する方法](https://sekailab.com/wp/2019/03/10/execute-windows-binary-on-wsl)
    1. vim ~/.bashrc
    2. python on Windows 側のaliasコメント反映 (下記の設定コードをコピペ)
    3. source ~/.bashrc

    ```python
    # alias pip='pip3'
    ##### python on Windows
    alias pip='/mnt/c/Python/Python37/Scripts/pip.exe'
    alias pipenv='/mnt/c/Python/Python37/Scripts/pipenv.exe'
    alias python='/mnt/c/Python/Python37/python.exe'

    # WSLの環境変数をexportで設定しても python.exe はWindowsの環境変数を参照するため、
    # この方法の使い道はあまりない
    ```

## Git

- [Git for Windows インストール](https://qiita.com/elu_jaune/items/280b4773a3a66c7956fe)
- [TortoiseGit セットアップ](https://qiita.com/SkyLaptor/items/6347f38c8c010f4d5bd2)

## VSCode

- [拡張機能 おすすめ](https://qiita.com/EbXpJ6bp/items/4b87a092a3d6a0ecf595)
- [拡張機能 24 選](https://qiita.com/sensuikan1973/items/74cf5383c02dbcd82234)
- [VS CodeでMarkdownをプレビューするには？](https://www.atmarkit.co.jp/ait/articles/1804/20/news030.html)  
［プレビュー のセキュリティ設定を変更］：VS Codeでは安全でないコンテンツ（HTTPSを使用していない外部サイトにある画像ファイルへのリンク、スクリプトなど）を表示しないようになっているので、この設定を変更する。
- インストール済み拡張機能一覧表示  
`code --list-extensions | xargs -L 1 echo code --install-extension`
- [インテリセンスが効かないときは、setting.jsonを編集する](https://qiita.com/kusanoiskuzuno/items/fc6a32ef32dd9500f746)
  - 外部モジュールのパス指定
  - インテリセンスエンジン（jedi）をFalseにする

    ```json
    {
        "python.autoComplete.extraPaths": [
            "c:/python/python37/lib/site-packages/"
        ],
        "python.jediEnabled": false
    }
    ```

### VSCode (Remote WSL)

- **WSL / VirtualBoxのlinux環境ではGPU サポートしてない!**  
- CPU利用のみのlinux実行環境のアプリ開発をする場合は、  
あると便利なので以下に情報を残しておく
- [Remote Development を快適に使う トラブルシュート編](https://qiita.com/kaishuu0123/items/d16eca8e973fc4f0ad07)
- [Remote Developmentを使ってSSH接続したEC2上のファイルを編集](https://dev.classmethod.jp/articles/vs-code-remote-development-ec2/)
- [VSCodeのRemote WSLでWSLを快適に使う](https://qiita.com/nj_ryoo0/items/a42c47436b77310f5430)
    1. WSLターミナルで編集したいdirに移動⇒```code .```入力⇒vscode起動
    2. vscode->拡張機能->WSL:UBUNTU-18.04が増えている
    3. LOCAL側でinstallを促されている拡張機能をinstall->vscode再起動
    4. vscode->拡張機能->WSL:UBUNTU-18.04 に色々install済になる

### [VSCodeでデバッガに引数を渡す方法](https://www.kabegiwablog.com/entry/2019/10/13/100000)

1. 実行->構成の追加-> launch.jsonが開く  
1. そこに"args":["--name", "hoge"],のように引数入力  
1. オプション付き引数を複数指定する場合、一行ずつargs:を追加  

    ```python
    "args": [
        "${file}," // 追加(アクティブなファイルのパス)
        100,
        "hoge"
        ]
    ```

## Terminal

- [ColorTool を使ってコンソールを見やすくする](https://qiita.com/yoshikingt/items/21d9e3fb8b8f22ab3476)
- [バッチ（.bat）をダブルクリックで実行後、ウィンドウを閉じないようにする](https://ameblo.jp/one-of-the-wnet/entry-10111695003.html)
- [vscodeのターミナルで自動コピーする方法](https://teratail.com/questions/177087)
- [WSLでマウス操作でコピー＆ペーストする方法](https://ex1.m-yabe.com/archives/3388)

## サクラエディタ

- [初期設定](https://proengineer.internous.co.jp/content/columnfeature/5348)
- 長いクエリ文を "&" で改行する方法
  - 置換ウインドウを開く(Ctrl + r)
  - 置換後の文字を「\r\n」にする。正規表現にチェックを付ける。

## 共有フォルダのアクセス

- [Windows10だけが、共有フォルダにアクセスできない原因と対処法](https://www.brain-network.ne.jp/qa/windows10-kyouyu-folder.html)
- [エクスプローラの詳細表示を変更](https://www.billionwallet.com/windows10/explorer-view.html)
- WSL起動のショートカット  
「Shift+右クリック」⇒「Linuxシェルをここに開く」

## 右クリックのカスタマイズ

- [右クリックの重いメニューを調べるには CCleaner を使用する](https://qiita.com/Q11Q/items/9fd5083ae71e32a577cd)
- [OneDriveのメニュー非表示](https://news.mynavi.jp/article/windows-460/)
- [レジストリで非表示にする](https://itjo.jp/windows/context-menu-shorten/)
- [SendToフォルダにショートカットを作成](https://www.tipsfound.com/windows10/07009)  
    sendtoの場所 :  `C:\Users\%USERNAME%\AppData\Roaming\Microsoft\Windows\SendTo`

## jq

- JSON整形ツール
- [Windowsにinstall](https://qiita.com/amemolee/items/ec1f1f2eab1c4c25a2f9)
- [Linuxにinstall](https://qiita.com/rubytomato@github/items/fdfc0a76e848442f374e#jq)
- [使い方](https://qiita.com/takeshinoda@github/items/2dec7a72930ec1f658af)

## タッチキーボード

- iPadでリモデスAppからwindowsを操作する時に便利
- [表示方法]：タスクバー右クリック -> タッチキーボードボタンを表示
- [基本設定]：以下の機能をオン
  - 「タブレットモードでなく、キーボードが接続されていない場合に、タッチキーボードを表示する」
  - 多言語ヒント -> ヒントを表示する

## Hyper-V / WSL2

- WSL2は正式リリース前なので、導入するとWindowsが不安定になる可能性があります。(2020/4/1)
- [WSL2とHyper-Vの関係](https://qiita.com/matarillo/items/ca1eecf8f9a3cd76f9ce)
- [WSL2インストール](https://www.geekfeed.co.jp/geekblog/wsl2-with-windows10-insider-preview-build)  

## VirtualBox

- [WSL上にXサーバをインストールしてGUIを実現する（VcXsrv編）](https://www.atmarkit.co.jp/ait/articles/1812/06/news040.html)
- [Windows10にVirtualBoxとUbuntuをインストール](https://qiita.com/pyon_kiti_jp/items/0be8ac17439abf418e48)

# ■ Ubuntuインストール

## Dual Boot

1. 準備
    - Bios設定変更
        - 高速スタートアップ：無効化
        - セキュアブート：無効化
    - RufusでLiveUSB作成
1. [構築手順](https://www.pc-koubou.jp/magazine/35542)
    - Windows側で事前にパーティション操作はしないこと！
1. [最初にやること](https://sicklylife.jp/ubuntu/1804/settings.html#gnome-initial-setup)
    - ディレクトリを英語表記にする
    - [コマンドラインにおいてカレントディレクトリ名のみを表示](https://www.iandprogram.net/entry/2015/09/11/181208)
    - [GRUBの起動順序の変更方法](https://qiita.com/OldS9l/items/dc84f8912fc3d86f646a)
    - [ソフトウェアとアップデート](https://plaza.rakuten.co.jp/shinshunomori/6011/)

# ■ 開発環境の構築 (Ubuntu)

## CUDA install

```shell
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/cuda-ubuntu1804.pin
sudo mv cuda-ubuntu1804.pin /etc/apt/preferences.d/cuda-repository-pin-600
wget http://developer.download.nvidia.com/compute/cuda/10.1/Prod/local_installers/cuda-repo-ubuntu1804-10-1-local-10.1.243-418.87.00_1.0-1_amd64.deb
sudo dpkg -i cuda-repo-ubuntu1804-10-1-local-10.1.243-418.87.00_1.0-1_amd64.deb
sudo apt-key add /var/cuda-repo-10-1-local-10.1.243-418.87.00/7fa2af80.pub
sudo apt-get update
sudo apt-get -y install cuda
```

## windowsOSパーティションの自動マウント

- [参考HP](https://lab4ict.com/system/archives/1565)

    ```shell
    sudo fdisk -l   # Device確認
    sudo blkid /dev/nvme0n1p3　#UUID, Type確認
    sudo vi /etc/fstab # 起動時に読まれるfstabを編集
        UUID=*****   /media/[username]/Windows   ntfs    default 0       0

    sudo mkdir /media/[username]/Windows # マウントポイント作成
    sudo mount /media/[username]/Windows # マウント
    df -Th |grep /media/[username]/Windows # できたか確認
    # マウントできると `/media/[username]/gachan/Windows` で見れる
    ```

## cifsによるNASの自動マウント

- [参考HP1](https://blog.infra-se.net/?p=46)
- [参考HP2](https://qiita.com/dyony/items/b91e531ca6f50b480b2e)

1. NASのuser,pwdファイル保存

    ```shell
    sudo apt install cifs-utils
    sudo vi /home/username/.smbcredentials  # NASのuser,pwdファイル保存
    username=USER
    password=PASSWORD
    sudo chmod 400 /home/username/.smbcredentials # 所有者のみreadonly
    ```

2. 起動時に読まれるfstabを編集

   - `sudo vi /etc/fstab` で開き、以下の一行を追加

    ```shell
    //192.168.**.**/data/    /media/[username]/Ls3_data/ cifs    credentials=/home/[username]/.smbcredentials,vers=1.0       0       0

    # vers=1.0 : 古いbaffalo機器の場合
    # vers=3.0 : 共有フォルダの共有元がWindows 10 の場合
    ```

3. 正しくマウントできるかチェック
   - `sudo mount -a`

## cifsによるNASの一時マウント

- baffalo linkstation の場合  
`sudo mount -t cifs -o username=admin,vers=1.0 //192.168.11.9/data /mnt/ls3_data`

## PATH設定方法

1. 環境変数にパスを追加  
    `echo export PATH='/usr/local/bin:$PATH' >> ~/.bash_profile`  
    export PATH=/usr/local/bin:$PATH を User/ユーザー名/.bash_profile に書き込んでいます。
2. bashの設定を再読み込み  
    `source ~/.bash_profile`

### 起動中のGnome端末内のみでPATH設定

- 起動中のGnome端末内で **export** コマンドでPATH設定すればいい
- 起動中のGnome端末内で 反映されたPATH一覧は、`export -p` で確認できる

### Gnome端末を起動したまま、GNOME Shellを再起動

- (Alt + F2) → r → Enter

## ショートカット

- Super + D : 全てのウィンドウを最小化

## [ワークスペース](https://www.pandanoir.info/entry/2018/02/21/193000)

## 時刻設定

- `sudo timedatectl set-local-rtc true`

## [man日本語設定](https://linuxfan.info/ubuntu-debian-ja-manpages)

- `sudo apt install -y manpages-ja manpages-ja-dev`
- `man date` 日本語になっていたらOK

## [gufw (ファイアーウォール)](https://sicklylife.jp/ubuntu/1804/gufw.html)

## ダウンロードした.debファイル

- `/var/cache/apt/archives/` にキャッシュされています。このキャッシュをクリアするには、`sudo apt clean`を実行します。

## Gnome端末

- テキストのコピペ
  - [参考HP](https://kledgeb.blogspot.com/2016/01/gnome-3.html)
    - 単語をダブルクリックすると、その単語全体が選択されます。
    - 選択したい行をトリプルクリックすると、その行全体が選択されます。
- ターミナルのカレントをファイルマネージャーで開く  
    `nautilus -w`

# ■ Linuxでインストールするパッケージ

## コーデック

- `sudo apt-get -y install ubuntu-restricted-extras`

## git

- `sudo apt-get install git-all`

## atom

- [インストール方法(apt)](https://www.bioerrorlog.work/entry/install-atom-on-ubuntu)

## spotify

- [インストール方法(apt)](https://www.spotify.com/されますjp/download/linux/)

## chrome

- インストール方法(apt)

    ```shell
    sudo sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list'
    sudo wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
    sudo apt update
    sudo apt install google-chrome-stable
    ```

## microsoftリポジトリの登録

- 以下、[公式HP](https://docs.microsoft.com/ja-jp/windows-server/administration/linux-package-repository-for-microsoft-software) に載っている方法を記載している

    ```shell
    sudo apt install apt-transport-https # aptでhttpsアクセスするために必要
    # 以下をそのままコピペ
    sudo curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > ~/Desktop/microsoft.gpg
    sudo cp ~/Desktop/microsoft.gpg /etc/apt/trusted.gpg.d/
    cd /
    sudo curl https://packages.microsoft.com/config/ubuntu/20.04/prod.list -o microsoft-prod.list
    cat sources.list.d/microsoft-prod.list
    # 正しく登録されているか確認
    sudo apt update
    ```

- sudo apt update で 以下のようなWarningが出た場合の対処法
  *Warning: ターゲット Packages (main/binary-amd64/Packages) は /etc/apt/sources.list:57 と /etc/apt/sources.list.d/microsoft-prod.list:1 で複数回設定されています*  

  1. `/etc/apt/source.list.d/microsoft-prod.list` を残す
  1. `/etc/apt/source.list` 側の microsoft**** の2行をviで削除
  1. `sudo apt update` で正しいか確認

### apt リポジトリ構成ファイルの場所

- `/etc/apt/sources.list.d`

## code (vscode)

- 先に、上記のmicrosoftリポジトリのaptに登録しておくこと
- [公式HP](https://code.visualstudio.com/docs/setup/linux) に載っている方法で aptでインストールするのが良い
- 何をやっているか知りたい場合は、こちらの[投稿](https://qiita.com/yoshiyasu1111/items/e21a77ed68b52cb5f7c8) を見るとよい

    ```shell
    # マイクロソフトのリポジトリを登録する
    sudo sh -c 'echo "deb [arch=amd64 signed-by=/etc/apt/trusted.gpg.d/microsoft.gpg] https://packages.microsoft.com/repos/vscode stable main" > /etc/apt/sources.list.d/vscode.list'
    # インストール
    sudo apt install code
    # codeのバージョン表示
    apt list code
    ```

### cv2のインテリセンス

- [vscodeでcv2のインテリセンスを表示するされない問題](https://qiita.com/FXsimone/items/577e3924f40aa4a9d4ea)
- setting.jsonで pylintの引数に `--extension-pkg-whitelist=cv2` を設定する

## snap版パッケージ

- ***snap版は日本語入力ができないので、atomやvscodeは aptでインストールしたほうが良い***
- snap版をインストールしたパッケージ一覧
    `snap list`

## apt-get updateでエラーが出た場合の対処法

- [参考HP](https://hombre-nuevo.com/linux/linux0020/)

## git操作方法

### Gnome端末上の操作

- [Git_for_Linux インストール](
https://employment.en-japan.com/engineerhub/entry/2017/01/31/110000)
- [Git_for_Linux コマンド早見表](https://qiita.com/kohga/items/dccf135b0af395f69144)
- よくやる操作一例  
`ssh github`  
`git clone git@github.com:karupagyu/tips.git`  
tipsリポジトリ内にディレクトリ移動  
`git pull`  `git fetch`   `git add [file]`  
コード編集。MarkdownLintの警告がないように書く。  
`git diff`  
`git commit -a`
`git push`

### VSCode上のGit操作

- [基本操作](https://qiita.com/mnao305/items/b3c5f5943066a0bb8e2e)
- [初期設定](https://qiita.com/y-tsutsu/items/2ba96b16b220fb5913be#git%E3%81%AE%E5%88%9D%E6%9C%9F%E8%A8%AD%E5%AE%9A)
- [初期設定していないとコミット時にエラーが出ます](https://qiita.com/jesus_isao/items/63557eba36819faa4ad9#%E3%81%88%E3%81%A3%E3%82%B3%E3%83%9F%E3%83%83%E3%83%88%E3%81%A7%E3%81%8D%E3%81%AA%E3%81%84%E3%82%93%E3%81%A0%E3%81%91%E3%81%A920190511%E8%BF%BD%E8%A8%98)

## ubuntuで iphone をusbカメラにする

- 準備
  - iphone側 : [アプリをインストール](https://www.dev47apps.com/)
  - ubuntu側 : [このページ](https://www.dev47apps.com/droidcam/linuxx/)のinstall手順に従ってインストール

    ```shell
    sudo apt install linux-headers-`uname -r`
    # `uname -r` : 現在のカーネルバージョンを返すコマンドが実行されます。
    ```

- 接続
  - [日本語で簡単に接続手順が書いてある](https://qiita.com/ssssssssok1/items/dcb61db415f00f43c4771)
  - iphone側 : アプリを起動
  - ubuntu側 : Terminal で `droidcam` と入力 → Phone IP, Portを入力

    ```none
    Found driver: /dev/video4 (fd:12)
    connecting to 192.168.11.11:4747
    ```

    このような表示が出る。  
    この場合、camno=4なので、cv2.VideoCapture(4) で画像取得できる

## update-alternatives

- 必要になったときのために、設定方法を残しておく

    ```shell
    sudo apt install update-alternatives
    which update-alternatives
    echo export PATH='/usr/bin/update-alternatives:$PATH' >> ~/.bash_profile
    echo $PATH
    source ~/.bash_profile
    ```

# ■ コマンド

## apt

- apt-getでパッケージをアンインストール

```shell
sudo apt-get install [パッケージ名]
sudo apt-get remove [パッケージ名]  # 設定ファイルを残す場合
sudo apt-get --purge remove [パッケージ名] # 設定ファイル&依存関係にあるパッケージも完全に削除する場合
```

## pip

- [pipでrequirements.txtを使ってパッケージ一括インストール](https://note.nkmk.me/python-pip-install-requirements/)

- pip インストールしたパッケージの場所を調べる
    `pip show [パッケージ名]`

## wget

Windowsは WSLで使える。  

- [-P]で保存先指定して取得：`wget -P [savedir] [http://***]`
- [wgetでこういう時はこうする!!](https://qiita.com/hirohiro77/items/b774908436ec032df719)

## イントラ内の使用IP一覧表示

- `iwconfig`
- `sudo arp-scan -l --interface wlp62s0`

## pyenv

- pipenvより venvを使う方がいいかも
- [Pythonで Pipenvを使う](https://narito.ninja/blog/detail/58/#pipfile)
- pipenvでLockingが終わらないときの対処法
  - Pipfile.lockを生成しないで仮想環境にパッケージインストール  
    `pipenv install --skip-lock`

# ■ コーディング

## webアプリ開発ライブラリ

- jQuery 簡単
- React 本格的

### GUI ツール

- PyQt (パイキュート) : QtというC++のGUIツールキットをPythonで使えるようにしたもの

## yield

- return文でそのまま値を返す関数を作ったとします。一度に大きなリストが返ってくるような関数だと、たくさんのメモリを一度に消費してしまうことになります。
- そのようなときは、yieldを使う事でその莫大な量の戻り値を小分けにして返すことが出来ます。これによって関数の実行をその都度中断し、少量ずつデータを返す事でメモリの消費量を抑えることが出来るようになります。

## webスクレイピング

- [スクレイピングを行う前に確認すること](https://tech-camp.in/note/technology/48812/)
- [Webスクレイピング前に確認すべき10問](https://note.com/octoparsejapan/n/n4101e2260003)

## pytorch

- [pyTorchでCNNsを徹底解説](https://qiita.com/mathlive/items/8e1f9a8467fff8dfd03c)
- [YOLO V3](http://starpentagon.net/analytics/yolo_v3_on_mac)
- [detectron2(windows)](https://github.com/conansherry/detectron2)

## python系

### pythonプロジェクトのおすすめフォルダ構成

- [VS CodeによるPython開発環境のテンプレ](https://qiita.com/kazetof/items/870d47d8f6b961e78acc)

### コード上でのpathの書き方

- [パスの書き方色々](https://qiita.com/ymdymd/items/d758110d429f72bc10fb)
- [Pythonでimportの対象ディレクトリのパスを確認・追加](https://note.nkmk.me/python-import-module-search-path/)
- カレントディレクトリをimport対象に追加(コードの先頭に書く)  
`sys.path.append(os.getcwd())`

### lint(リント)

- ソースコードの記述に対し、警告を行う静的解析処理のこと
- 言語毎にツールがある
- pythonは、pylint > pep8(ぺぺエイト) > flake8 (左ほど警告ルールが厳しい)
- vscodeは、python拡張機能をインストールしたらpylintが入る
- [pylint のメッセージを抑制する](https://qiita.com/stat/items/eb74bb26190759f87a05)

### Markdown

- [書き方](https://qiita.com/shizuma/items/8616bbe3ebe8ab0b6ca1)
- Qiitaのマークダウン記法は、標準のMarkdown Preview で確認
- Githubのマークダウン記法は、Markdown Preview Enhanced で確認
- vscodeの拡張機能 Markdownlint を使おう。書き方を自然と覚えます。
- 無視させたい警告は、 setting.json に下記例のように編集する

    ```json
    "markdownlint.config": {
            "single-title" : false
        },
    ```

# ■ クラウドサービス

## Github

public repogitory ならwikiが使える

## box.net

10GBまで無料

# ■ エンターテイメント

- [Windows10パソコンにiTunesをインストールする方法](https://wifinomori.com/windows-itunes/)

# ■ その他

## Excel

- 100マス計算⇒ 複合参照 を使う  
例)　```=$A2+B$1```
