# ■ 開発環境の構築 (windows)

## 環境変数の設定方法

コマンドプロンプト用

- PATH 確認：
  `echo %PATH:;=&echo.%`
- PYTHONPATH に c:\hoge を追加：
  `set PYTHONPATH=%PYTHONPATH%;C:\hoge`
- PYTHONPATH を PATH に追加：
  `set PATH = %PATH%;%PYTHONPATH`

## python

- [Python 3.7 のインストール（Windows 上）](https://www.kkaneko.jp/tools/win/python.html)
- [MSVC ビルドツール 2019 （Build Tools for Visual Studio 2019） のインストール（Windows 上）](https://www.kkaneko.jp/tools/win/buildtool.html)
- [Visual Studio Community 2019 vesion 16.2, MSVC ビルドツールのインストール（Windows 上）](https://www.kunihikokaneko.com/tools/win/vs2019.html)
- [用語説明](https://www.kkaneko.jp/tools/tools.html)
- [Python3.7 をインストールして path を通して、pip でパッケージを入れる](https://karupoimou.hatenablog.com/entry/2019/04/29/064646)

## CUDA

- [NVIDIA CUDA ツールキット 10.1 のインストール（Windows 上）](https://www.kunihikokaneko.com/tools/win/cuda10.html)
- [nvidia-smi コマンドの詳細ついて](https://qiita.com/miyamotok0105/items/1b34e548f96ef7d40370)

## WSL

- [WSL (Windows Subsystem for Linux)の基本メモ](https://qiita.com/rubytomato@github/items/fdfc0a76e848442f374e)
- [Windows で環境を極力汚さずに Python を動かす方法 (WSL 利用 Windows10)](https://qiita.com/rhene/items/ff11c7850a9a7617c50f)
- [python コマンドで python3 を実行したい(alias 変更)](https://qiita.com/houtarou/items/c7fa8006eef9e30ffad5)
- wsl ランチャー : コマンドプロンプトで wsl と入力しても起動できる

### WSL から Windows のバイナリを実行する方法

- [WSL から Windows 側の GUI アプリを実行](https://laboradian.com/run-win-gui-exe-from-wsl)
- [WSL で Windows のバイナリを実行する方法](https://sekailab.com/wp/2019/03/10/execute-windows-binary-on-wsl)

  1. vim ~/.bashrc
  2. python on Windows 側の alias コメント反映 (下記の設定コードをコピペ)
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

- [ショートカット](http://kquoe2.hatenablog.com/entry/2019/03/07/081019)
- [拡張機能 おすすめ](https://qiita.com/EbXpJ6bp/items/4b87a092a3d6a0ecf595)
- [拡張機能 24 選](https://qiita.com/sensuikan1973/items/74cf5383c02dbcd82234)
- [拡張機能 (web 系多め)](https://qiita.com/ri-zhi/items/1befd705600cc764359e)
- インストール済み拡張機能一覧表示  
  `code --list-extensions | xargs -L 1 echo code --install-extension`
- [Terminal カラーをカスタマイズするには？](https://glitchbone.github.io/vscode-base16-term/)
- [Markdown をプレビューするには？](https://www.atmarkit.co.jp/ait/articles/1804/20/news030.html)  
  ［プレビュー のセキュリティ設定を変更］：VS Code では安全でないコンテンツ（HTTPS を使用していない外部サイトにある画像ファイルへのリンク、スクリプトなど）を表示しないようになっているので、この設定を変更する。
- [cv2 のインテリセンスが表示されないときは？](https://qiita.com/FXsimone/items/577e3924f40aa4a9d4ea)

  - setting.json を編集  
    `"python.linting.pylintArgs": ["--extension-pkg-whitelist=cv2"]` を追加  
    `"python.linting.pylintEnabled": false` で OK

- [VSCode インテリセンスが効かないときは、setting.json を編集する](https://qiita.com/kusanoiskuzuno/items/fc6a32ef32dd9500f746)

  - 外部モジュールのパス指定
  - インテリセンスエンジン（jedi）を False にする

    ```json
    {
      "python.autoComplete.extraPaths": [
        "c:/python/python37/lib/site-packages/"
      ],
      "python.jediEnabled": false
    }
    ```

- 不要な snippet の無効化
  - 方法 1
    - 拡張機能`python extended`を無効化する
  - 方法 2
    1. 拡張機能`Control Snippets`をインストール
    2. コマンドパレットに control snippet と入力
    3. python extended をオフ

### VSCode (Remote WSL)

- **WSL / VirtualBox の linux 環境では GPU サポートしてない! (2020.04.01 時点)**
- CPU 利用のみの linux 実行環境のアプリ開発をする場合は、  
  あると便利なので以下に情報を残しておく
- [Remote Development を快適に使う トラブルシュート編](https://qiita.com/kaishuu0123/items/d16eca8e973fc4f0ad07)
- [Remote Development を使って SSH 接続した EC2 上のファイルを編集](https://dev.classmethod.jp/articles/vs-code-remote-development-ec2/)
- [VSCode の Remote WSL で WSL を快適に使う](https://qiita.com/nj_ryoo0/items/a42c47436b77310f5430)
  1. WSL ターミナルで編集したい dir に移動 ⇒`code .`入力 ⇒vscode 起動
  2. vscode->拡張機能->WSL:UBUNTU-18.04 が増えている
  3. LOCAL 側で install を促されている拡張機能を install->vscode 再起動
  4. vscode->拡張機能->WSL:UBUNTU-18.04 に色々 install 済になる

## Terminal

- [ColorTool を使ってコンソールを見やすくする](https://qiita.com/yoshikingt/items/21d9e3fb8b8f22ab3476)
- [バッチ（.bat）をダブルクリックで実行後、ウィンドウを閉じないようにする](https://ameblo.jp/one-of-the-wnet/entry-10111695003.html)
- [vscode のターミナルで自動コピーする方法](https://teratail.com/questions/177087)
- [WSL でマウス操作でコピー＆ペーストする方法](https://ex1.m-yabe.com/archives/3388)

## サクラエディタ

- [初期設定](https://proengineer.internous.co.jp/content/columnfeature/5348)
- 長いクエリ文を "&" で改行する方法
  - 置換ウインドウを開く(Ctrl + r)
  - 置換後の文字を「\r\n」にする。正規表現にチェックを付ける。

## 共有フォルダのアクセス

- [Windows10 だけが、共有フォルダにアクセスできない原因と対処法](https://www.brain-network.ne.jp/qa/windows10-kyouyu-folder.html)
- [エクスプローラの詳細表示を変更](https://www.billionwallet.com/windows10/explorer-view.html)
- WSL 起動のショートカット  
  「Shift+右クリック」⇒「Linux シェルをここに開く」

## 右クリックのカスタマイズ

- [右クリックの重いメニューを調べるには CCleaner を使用する](https://qiita.com/Q11Q/items/9fd5083ae71e32a577cd)
- [OneDrive のメニュー非表示](https://news.mynavi.jp/article/windows-460/)
- [レジストリで非表示にする](https://itjo.jp/windows/context-menu-shorten/)
- [SendTo フォルダにショートカットを作成](https://www.tipsfound.com/windows10/07009)  
   sendto の場所 : `C:\Users\%USERNAME%\AppData\Roaming\Microsoft\Windows\SendTo`

## jq

- JSON 整形ツール
- [Windows に install](https://qiita.com/amemolee/items/ec1f1f2eab1c4c25a2f9)
- [Linux に install](https://qiita.com/rubytomato@github/items/fdfc0a76e848442f374e#jq)
- [使い方](https://qiita.com/takeshinoda@github/items/2dec7a72930ec1f658af)

## タッチキーボード

- iPad でリモデス App から windows を操作する時に便利
- [表示方法]：タスクバー右クリック -> タッチキーボードボタンを表示
- [基本設定]：以下の機能をオン
  - 「タブレットモードでなく、キーボードが接続されていない場合に、タッチキーボードを表示する」
  - 多言語ヒント -> ヒントを表示する

## Hyper-V / WSL2

- WSL2 は正式リリース前なので、導入すると Windows が不安定になる可能性があります。(2020/4/1)
- [WSL2 と Hyper-V の関係](https://qiita.com/matarillo/items/ca1eecf8f9a3cd76f9ce)
- [WSL2 インストール](https://www.geekfeed.co.jp/geekblog/wsl2-with-windows10-insider-preview-build)

## VirtualBox

- [WSL 上に X サーバをインストールして GUI を実現する（VcXsrv 編）](https://www.atmarkit.co.jp/ait/articles/1812/06/news040.html)
- [Windows10 に VirtualBox と Ubuntu をインストール](https://qiita.com/pyon_kiti_jp/items/0be8ac17439abf418e48)

# ■ Ubuntu インストール

## Dual Boot

1. 準備
   - Bios 設定変更
     - 高速スタートアップ：無効化
     - セキュアブート：無効化
   - Rufus で LiveUSB 作成
1. [構築手順](https://www.pc-koubou.jp/magazine/35542)
   - Windows 側で事前にパーティション操作はしないこと！
1. [最初にやること](https://sicklylife.jp/ubuntu/1804/settings.html#gnome-initial-setup)
   - ディレクトリを英語表記にする
   - [コマンドラインにおいてカレントディレクトリ名のみを表示](https://www.iandprogram.net/entry/2015/09/11/181208)
   - [GRUB の起動順序の変更方法](https://qiita.com/OldS9l/items/dc84f8912fc3d86f646a)
   - [ソフトウェアとアップデート](https://plaza.rakuten.co.jp/shinshunomori/6011/)

## 日本語への対応

- [Japanese Team のパッケージレポジトリを追加](https://www.ubuntulinux.jp/japanese)
- 以下のコマンドを実行し、GPG 鍵とレポジトリを追加

  Ubuntu 20.04 LTS の場合:

  ```shell
  wget -q https://www.ubuntulinux.jp/ubuntu-ja-archive-keyring.gpg -O- | sudo apt-key add -
  wget -q https://www.ubuntulinux.jp/ubuntu-jp-ppa-keyring.gpg -O- | sudo apt-key add -
  sudo wget https://www.ubuntulinux.jp/sources.list.d/focal.list -O /etc/apt/sources.list.d/ubuntu-ja.list
  sudo apt update
  ```

# ■ 開発環境の構築 (Ubuntu)

## python3.7

- Ubuntu デフォルトのリポジトリよりも最新版がリリースされる PPA リポジトリを apt に登録する方法でインストール
- [How to Install Python 3.7 on Ubuntu 18.04](https://phoenixnap.com/kb/how-to-install-python-3-ubuntu)

## CUDA install

- [How to install CUDA on Ubuntu 20.04](https://linuxconfig.org/how-to-install-cuda-on-ubuntu-20-04-focal-fossa-linux)

  ```shell
  wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/cuda-ubuntu1804.pin
  sudo mv cuda-ubuntu1804.pin /etc/apt/preferences.d/cuda-repository-pin-600
  wget http://developer.download.nvidia.com/compute/cuda/10.1/Prod/local_installers/cuda-repo-ubuntu1804-10-1-local-10.1.243-418.87.00_1.0-1_amd64.deb
  sudo dpkg -i cuda-repo-ubuntu1804-10-1-local-10.1.243-418.87.00_1.0-1_amd64.deb
  sudo apt-key add /var/cuda-repo-10-1-local-10.1.243-418.87.00/7fa2af80.pub
  sudo apt-get update
  sudo apt-get -y install cuda
  ```

## windowsOS パーティションの自動マウント

- [参考 HP](https://lab4ict.com/system/archives/1565)

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

## cifs による NAS の自動マウント

- [参考 HP1](https://blog.infra-se.net/?p=46)
- [参考 HP2](https://qiita.com/dyony/items/b91e531ca6f50b480b2e)

1. NAS の user,pwd ファイル保存

   ```shell
   sudo apt install cifs-utils
   sudo vi /home/username/.smbcredentials  # NASのuser,pwdファイル保存
   username=USER
   password=PASSWORD
   sudo chmod 400 /home/username/.smbcredentials # 所有者のみreadonly
   ```

2. 起動時に読まれる fstab を編集

   - `sudo vi /etc/fstab` で開き、以下の一行を追加

   ```shell
   //192.168.**.**/data/    /media/[username]/Ls3_data/ cifs    credentials=/home/[username]/.smbcredentials,vers=1.0       0       0

   # vers=1.0 : 古いbaffalo機器の場合
   # vers=3.0 : 共有フォルダの共有元がWindows 10 の場合
   ```

3. 正しくマウントできるかチェック
   - `sudo mount -a`

## cifs による NAS の一時マウント

- baffalo linkstation の場合  
  `sudo mount -t cifs -o username=admin,vers=1.0 //192.168.11.9/data /mnt/ls3_data`

## PATH 設定方法

1. 環境変数にパスを追加  
   `echo export PATH='/usr/local/bin:$PATH' >> ~/.bash_profile`  
   export PATH=/usr/local/bin:\$PATH を User/ユーザー名/.bash_profile に書き込んでいます。
2. bash の設定を再読み込み  
   `source ~/.bash_profile`

### 起動中の Gnome 端末内のみで PATH 設定

- 起動中の Gnome 端末内で **export** コマンドで PATH 設定すればいい
- 起動中の Gnome 端末内で 反映された PATH 一覧は、`export -p` で確認できる

### Gnome 端末を起動したまま、GNOME Shell を再起動

- (Alt + F2) → r → Enter

## ショートカット

| ショートカット                    | 機能                               |
| --------------------------------- | ---------------------------------- |
| Super + D                         | 全てのウィンドウを最小化           |
| Ctrl + L                          | フォルダウィンドウをパス表示に変更 |
| Ctrl + Shift + T                  | ブラウザで最近閉じたタブの復元     |
| コマンドパレット上で ReloadWindow | VSCode のリロード                  |
| Ctrl + Shift + I (Linux)          | コード整形                         |
| Shift + Alt + F (Windows)         | コード整形                         |

## マウスの中クリックによる貼り付け無効化

- Tweaks ⇒ キーボードとマウス ⇒ 中クリックによる貼り付け OFF

## [ワークスペース](https://www.pandanoir.info/entry/2018/02/21/193000)

## 時刻設定

- `sudo timedatectl set-local-rtc true`

## [man 日本語設定](https://linuxfan.info/ubuntu-debian-ja-manpages)

- `sudo apt install -y manpages-ja manpages-ja-dev`
- `man date` 日本語になっていたら OK

## [gufw (ファイアーウォール)](https://sicklylife.jp/ubuntu/1804/gufw.html)

## ダウンロードした.deb ファイル

- `/var/cache/apt/archives/` にキャッシュされています。このキャッシュをクリアするには、`sudo apt clean`を実行します。

## Gnome 端末

- テキストのコピペ
  - [参考 HP](https://kledgeb.blogspot.com/2016/01/gnome-3.html)
    - 単語をダブルクリックすると、その単語全体が選択されます。
    - 選択したい行をトリプルクリックすると、その行全体が選択されます。
- ターミナルのカレントをファイルマネージャーで開く  
   `nautilus -w`
  'Ricty Diminished'"

# ■ Linux でインストールするパッケージ

## 省電力ツール

- `sudo apt install tlp`
- `sudo tlp start`

## Synaptic

- Debian パッケージ管理システムである APT の GUI ツール
- `sudo apt install synaptic`
- `synaptic`で起動

## 未使用パッケージの削除

- `sudo apt autoclean`
- `sudo apt clean`
- `sudo apt autoremove`

## コーデック

- `sudo apt-get -y install ubuntu-restricted-extras`

## git

- `sudo apt-get install git-all`

### Gimp

- `sudo apt install gimp`

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

## microsoft リポジトリの登録

- 以下、[公式 HP](https://docs.microsoft.com/ja-jp/windows-server/administration/linux-package-repository-for-microsoft-software) に載っている方法を記載している

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

- sudo apt update で 以下のような Warning が出た場合の対処法
  _Warning: ターゲット Packages (main/binary-amd64/Packages) は /etc/apt/sources.list:57 と /etc/apt/sources.list.d/microsoft-prod.list:1 で複数回設定されています_

  1. `/etc/apt/source.list.d/microsoft-prod.list` を残す
  1. `/etc/apt/source.list` 側の microsoft\*\*\*\* の 2 行を vi で削除
  1. `sudo apt update` で正しいか確認

### apt リポジトリ構成ファイルの場所

- `/etc/apt/sources.list.d`

## code (vscode)

- 先に、上記の microsoft リポジトリの apt に登録しておくこと
- [公式 HP](https://code.visualstudio.com/docs/setup/linux) に載っている方法で apt でインストールするのが良い
- 何をやっているか知りたい場合は、こちらの[投稿](https://qiita.com/yoshiyasu1111/items/e21a77ed68b52cb5f7c8) を見るとよい

  ```shell
  # マイクロソフトのリポジトリを登録する
  sudo sh -c 'echo "deb [arch=amd64 signed-by=/etc/apt/trusted.gpg.d/microsoft.gpg] https://packages.microsoft.com/repos/vscode stable main" > /etc/apt/sources.list.d/vscode.list'
  # インストール
  sudo apt install code
  # codeのバージョン表示
  apt list code
  ```

## snap 版パッケージ

- **_snap 版は日本語入力ができないので、atom や vscode は apt でインストールしたほうが良い_**
- snap 版をインストールしたパッケージ一覧
  `snap list`

## apt-get update でエラーが出た場合の対処法

- [参考 HP](https://hombre-nuevo.com/linux/linux0020/)

## git 操作方法

### Gnome 端末上の操作

- [Git_for_Linux インストール](https://employment.en-japan.com/engineerhub/entry/2017/01/31/110000)
- [Git_for_Linux コマンド早見表](https://qiita.com/kohga/items/dccf135b0af395f69144)
- よくやる操作一例  
  `ssh github`  
  `git clone git@github.com:karupagyu/tips.git`  
  tips リポジトリ内にディレクトリ移動  
  `git pull` `git fetch` `git add [file]`  
  コード編集。MarkdownLint の警告がないように書く。  
  `git diff`  
  `git commit -a`
  `git push`

### VSCode 上の Git 操作

- [基本操作](https://qiita.com/mnao305/items/b3c5f5943066a0bb8e2e)
- [初期設定](https://qiita.com/y-tsutsu/items/2ba96b16b220fb5913be#git%E3%81%AE%E5%88%9D%E6%9C%9F%E8%A8%AD%E5%AE%9A)
- [初期設定していないとコミット時にエラーが出ます](https://qiita.com/jesus_isao/items/63557eba36819faa4ad9#%E3%81%88%E3%81%A3%E3%82%B3%E3%83%9F%E3%83%83%E3%83%88%E3%81%A7%E3%81%8D%E3%81%AA%E3%81%84%E3%82%93%E3%81%A0%E3%81%91%E3%81%A920190511%E8%BF%BD%E8%A8%98)

## ubuntu で iphone を usb カメラにする

- 準備

  - iphone 側 : [アプリをインストール](https://www.dev47apps.com/)
  - ubuntu 側 : [このページ](https://www.dev47apps.com/droidcam/linuxx/)の install 手順に従ってインストール

    ```shell
    sudo apt install linux-headers-`uname -r`
    # `uname -r` : 現在のカーネルバージョンを返すコマンドが実行されます。
    ```

- 接続

  - [日本語で簡単に接続手順が書いてある](https://qiita.com/ssssssssok1/items/dcb61db415f00f43c4771)
  - iphone 側 : アプリを起動
  - ubuntu 側 : Terminal で `droidcam` と入力 → Phone IP, Port を入力

    ```none
    Found driver: /dev/video4 (fd:12)
    connecting to 192.168.11.11:4747
    ```

    このような表示が出る。  
    この場合、camno=4 なので、cv2.VideoCapture(4) で画像取得できる

## 利用できる Web カメラの情報を取得する

- [参考 HP](https://leico.github.io/TechnicalNote/Linux/webcam-usage)

  - `sudo apt install v4l-utils`
  - `v4l2-ctl --list-devices`

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

- apt-get でパッケージをアンインストール

```shell
sudo apt-get install [パッケージ名]
sudo apt-get remove [パッケージ名]  # 設定ファイルを残す場合
sudo apt-get --purge remove [パッケージ名] # 設定ファイル&依存関係にあるパッケージも完全に削除する場合
```

## pip

- [pip で requirements.txt を使ってパッケージ一括インストール](https://note.nkmk.me/python-pip-install-requirements/)

- pip インストールしたパッケージの場所を調べる
  `pip show [パッケージ名]`

## wget

Windows は WSL で使える。

- [-P]で保存先指定して取得：`wget -P [savedir] [http://***]`
- [wget でこういう時はこうする!!](https://qiita.com/hirohiro77/items/b774908436ec032df719)

## イントラ内の使用 IP 一覧表示

- `iwconfig`
- `sudo arp-scan -l --interface wlp62s0`

## pyenv

- pipenv より venv を使う方がいいかも
- [Python で Pipenv を使う](https://narito.ninja/blog/detail/58/#pipfile)
- pipenv で Locking が終わらないときの対処法
  - Pipfile.lock を生成しないで仮想環境にパッケージインストール  
    `pipenv install --skip-lock`

# ■ コーディング

## web アプリ開発ライブラリ

- jQuery 簡単

  - ２つの利用方法
    - ダウンロードしたファイルを読み込む
    - [CDN を使用して読み込む](https://programmercollege.jp/column/9353/)

- React 本格的
- `Web 制作者のためのおすすめ Chrome 拡張 15` で検索

## GUI ツール

- PyQt (パイキュート) : Qt という C++の GUI ツールキットを Python で使えるようにしたもの

## アノテーションツール

- [VoTT](https://github.com/microsoft/VoTT)

  - [VoTT v2.1.0 を使用して画像のアノテーション（教師データの作成）を行う](https://qiita.com/clerk67/items/8e7207284037dcf1f9ec)

- labelingImg
  - [Annotation ツール比較：labelImg と VoTT](https://www.nakasha.co.jp/future/ai/annotation_tool.html)
  - 動画は vott がよい yolo 形式にするのが大変？

## yield

- return 文でそのまま値を返す関数を作ったとします。一度に大きなリストが返ってくるような関数だと、たくさんのメモリを一度に消費してしまうことになります。
- そのようなときは、yield を使う事でその莫大な量の戻り値を小分けにして返すことが出来ます。これによって関数の実行をその都度中断し、少量ずつデータを返す事でメモリの消費量を抑えることが出来るようになります。

## web スクレイピング

- [スクレイピングを行う前に確認すること](https://tech-camp.in/note/technology/48812/)
- [Web スクレイピング前に確認すべき 10 問](https://note.com/octoparsejapan/n/n4101e2260003)

## BeatuifulSoup

- 使用例

  ```python
  r = requests.get(url)
  soup= BeautifulSoup(r.text,"html.parser")
  soup.select('.tile')[0].string
  ```

## FlikerAPI

## pytorch

- [pyTorch で CNNs を徹底解説](https://qiita.com/mathlive/items/8e1f9a8467fff8dfd03c)
- [YOLO V3](http://starpentagon.net/analytics/yolo_v3_on_mac)
- [detectron2(windows)](https://github.com/conansherry/detectron2)

## python 系

### python プロジェクトのおすすめフォルダ構成

- [VS Code による Python 開発環境のテンプレ](https://qiita.com/kazetof/items/870d47d8f6b961e78acc)

### 改行コードの一括置換

- [参考 HP](https://qiita.com/June8715/items/24307ee467baee51387e)

### コード上での path の書き方

- [パスの書き方色々](https://qiita.com/ymdymd/items/d758110d429f72bc10fb)
- [Python で import の対象ディレクトリのパスを確認・追加](https://note.nkmk.me/python-import-module-search-path/)
- カレントディレクトリを import 対象に追加(コードの先頭に書く)  
  `sys.path.append(os.getcwd())`

### vscode デバッグ構成ファイル(launch.json) の編集

- 実行 ⇒ 構成を開く ⇒ launch.json が開く
- 定義済み変数を使うと、楽にパスを設定できる  
  [このページ内](https://qiita.com/ShortArrow/items/dc0c8cacd696154510f1) の引用元 vscode 公式ページに詳しく書かれている
- `Ctrl + Space` で設定可能な属性候補を表示

```json
"configurations": [
  {
    //アクティブなファイルを実行する
    "program": "${file}",
    // 実行時のカレントディレクトリを変更する
    "cwd": "${workspaceFolder}/hogedir/hogedir",
    // オプション引数を設定する
    "args": [ "--modelpath", "******.pth", "--config", "*****.json" ]
  }
]
```

### lint(リント)

- ソースコードの記述に対し、警告を行う静的解析処理のこと
- 言語毎にツールがある
- python は、pylint > pep8(ぺぺエイト) > flake8 (左ほど警告ルールが厳しい)
- vscode は、python 拡張機能をインストールしたら pylint が入る
- [pylint のメッセージを抑制する](https://qiita.com/stat/items/eb74bb26190759f87a05)

### Markdown

- [書き方](https://qiita.com/shizuma/items/8616bbe3ebe8ab0b6ca1)
- Qiita のマークダウン記法は、標準の Markdown Preview で確認
- Github のマークダウン記法は、Markdown Preview Enhanced で確認
- vscode の拡張機能 Markdownlint を使おう。書き方を自然と覚えます。
- 無視させたい警告は、 setting.json に下記例のように編集する

```json
"markdownlint.config": {
        "single-title" : false
    },
```

### コーディング環境

- [コーディング規約 (PEP8)](https://qiita.com/simonritchie/items/bb06a7521ae6560738a7)
- [コード解析ツール](https://qiita.com/psychoroid/items/2c2acc06c900d2c0c8cb)
  - 静的解析: flake8、自動整形: autopep8
- [Docstring](https://qiita.com/11ohina017/items/118b3b42b612e527dc1d)
  - Google スタイル --> Sphinx 　で ドキュメント生成
  - vscode Docstring """ を入力でスケルトン生成される
- [型ヒント](https://docs.python.org/ja/3/library/typing.html)
- 関数アノテーション
  - 関数の引数に型指定しておくと、補完が効く
- [mypy](https://mypy.readthedocs.io/en/stable/common_issues.html)

### vscode 基本設定

- setting.json を編集

  ```json
  {
    // Font..
    "workbench.iconTheme": "vscode-icons",
    "editor.fontSize": 12,
    "editor.fontFamily": "Consolas, Meiryo, 'Courier New', monospace",
    "window.zoomLevel": 0,
    "terminal.integrated.shell.linux": "/usr/bin/bash",
    "files.eol": "\n", // デフォルト改行コード LF

    // Indent, Spaces, Colors
    "trailing-spaces.showStatusBarMessage": false,
    "trailing-spaces.includeEmptyLines": false,
    "trailing-spaces.logLevel": "log",
    "editor.renderIndentGuides": false,
    "[html]": {
      "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    // Markdown
    "markdownlint.config": {
      "single-title": false
      //"ol-prefix" : false
    },
    "markdownShortcuts.icons.image": true,
    "markdownShortcuts.icons.link": true,
    "instantmarkdown.autoOpenBrowser": false,
    "markdown.preview.fontSize": 10,
    "markdown.preview.fontFamily": "-apple-system, BlinkMacSystemFont, 'Segoe WPC', 'Segoe UI', 'Ubuntu', 'Droid Sans', sans-serif, 'Ricty Diminished'",
    "files.autoSave": "off",

    // Select a color theme
    // https://glitchbone.github.io/vscode-base16-term/
    // [theme: Hopscotch]
    "workbench.colorCustomizations": {
      "terminal.background": "#322931",
      "terminal.foreground": "#B9B5B8",
      "terminalCursor.background": "#B9B5B8",
      "terminalCursor.foreground": "#B9B5B8",
      "terminal.ansiBlack": "#322931",
      "terminal.ansiBlue": "#1290BF",
      "terminal.ansiBrightBlack": "#797379",
      "terminal.ansiBrightBlue": "#1290BF",
      "terminal.ansiBrightCyan": "#149B93",
      "terminal.ansiBrightGreen": "#8FC13E",
      "terminal.ansiBrightMagenta": "#C85E7C",
      "terminal.ansiBrightRed": "#DD464C",
      "terminal.ansiBrightWhite": "#FFFFFF",
      "terminal.ansiBrightYellow": "#FDCC59",
      "terminal.ansiCyan": "#149B93",
      "terminal.ansiGreen": "#8FC13E",
      "terminal.ansiMagenta": "#C85E7C",
      "terminal.ansiRed": "#DD464C",
      "terminal.ansiWhite": "#B9B5B8",
      "terminal.ansiYellow": "#FDCC59"
    },

    // 非表示にするファイル
    "files.exclude": {
      "**/.git": true,
      "**/.vscode": true,
      "**/__pycache__": true,
      "**/.DS_Store": true,
      "**/*.pyc": true,
      "**/bin": true,
      "**/*.o": true,
      "**/*.obj": true,
      "**/*.ilk": true,
      "**/*.pdb": true,
      "**/*.tlog": true,
      "**/*.idb": true,
      "**/*.dll": true
    },

    // Intellisense
    "python.jediEnabled": false,
    "editor.suggestSelection": "recentlyUsedByPrefix",
    "vsintellicode.modify.editor.suggestSelection": "automaticallyOverrodeDefaultValue",
    "python.linting.pylintArgs": ["--extension-pkg-whitelist=cv2"], // cv2インテリセンス有効化のため

    // Linting
    "python.linting.pylintEnabled": false,
    "python.linting.flake8Enabled": true,
    "python.linting.lintOnSave": true,
    "editor.rulers": [100, 120], // 100,120列目に縦線を入れる
    // "python.linting.flake8Args": ["--ignore=E501"],

    "python.linting.flake8Args": ["--max-line-length=120"],
    "python.formatting.autopep8Args": ["--ignore=E501"],
    "editor.formatOnType": true,
    "editor.formatOnSave": true,
    "path-autocomplete.extensionOnImport": true,
    "python.dataScience.sendSelectionToInteractiveWindow": true,
    "vsintellicode.sql.completionsEnabled": false,

    // Linting.mypy
    "python.linting.mypyEnabled": true,
    "python.linting.mypyArgs": [
      "--ignore-missing-imports",
      "--follow-imports=silent",
      "--show-column-numbers",
      "--cache-dir=/home/gachan/.cache/mypy_cache" // 設定しない場合、プロジェクト毎にキャッシュが生成される
    ]
  }
  ```

### 関数変数の命名

- [便利なページ](https://nelog.jp/programming-words)
- [よく使う英単語](https://qiita.com/Ted-HM/items/7dde25dcffae4cdc7923)
- [よく使う英単語まとめ](https://arakan-pgm-ai.hatenablog.com/entry/2019/04/15/000000)

### jupyter-notebook

- [vscode コマンドパレットで起動](https://dev.classmethod.jp/articles/visual-studio-code-jupyter-notebook/)
  - `Python: Create Blank New Jupyter Notebook`

### numpy.view によるサブクラス化

- [参考元](https://numpy.org/doc/stable/user/basics.subclassing.html#module-numpy.doc.subclassing)

### flask

- [Flask 基本](https://tanuhack.com/category/python/flask/)
- [サンプルコード 1](https://github.com/akmamun/camera-live-streaming)
- [サンプルコード 2](https://medium.com/datadriveninvestor/video-streaming-using-flask-and-opencv-c464bf8473d6)

- [ここで](https://blog.miguelgrinberg.com/post/video-streaming-with-flask/page/10) ジェネレーター関数が複数の結果を順番に返すことができることがわかります。Flask は、ジェネレーター関数のこの特性を使用してストリーミングを実装します。

- Live Streaming コード解説
  - [1](https://qiita.com/sti320a/items/3cdafb737d2c16fbaa51)
  - [2](https://qiita.com/Gyutan/items/1f81afacc7cac0b07526)
- これからは fastapi ?
- flask の起動

  - `http://127.0.0.1:5000/` だとローカル PC からしか接続できない
  - `--host=0.0.0.0`だと、同じネットワーク内の全ての PC で Listen することができます。

- flask を HTTPS 化する
  - [HTTPS 化する場所のわかりやすい説明](https://python.ms/flask-via-tls/)
  - [1](http://motojapan.hateblo.jp/entry/2017/12/14/083635#flask%E4%B8%8A%E3%81%A7HTTPS%E3%82%B5%E3%83%BC%E3%83%90%E3%83%BC%E8%B5%B7%E5%8B%95)
  - [2](https://qiita.com/tomboyboy/items/122dfdb41188176e45b5)

### WebRTC

- [公式](https://webrtc.org/)
- Firefox で動くが chorme で動かない場合、chrome に `chrome://flags/` と入力し必要な機能を Enable にする
- アプリがカメラとマイクへのアクセスを可能にする JavaScript API（getUserMedia）

### MessagePack for Python

- `pip install -U msgpack-python`
- `pip install msgpack-numpy`

### ZMQ

- [ガイドブック](https://www.cuspy.org/diary/2015-05-07-zmq/zguide-ja.pdf)

### imutils

- 基本的な画像処理関数を OpenCV の関数を組み合わせて作られたモジュール
- [使い方](https://github.com/jrosebr1/imutils)

# ■ 用語解説

### npm

- Node.js のパッケージを管理するもの。Node Package Manager の略

### Node.js

- JavaScript は本来クライアントサイドで動く言語で HTML で書かれたページに動きをつけたりするのに対して、Node.js はサーバサイドで動く JavaScript である。
- 非同期型のイベント駆動の JavaScript 環境で、たくさんの接続を同時に処理することができます。

### react.js

- JavaScript で書かれたライブラリ。react.js をインクルードして使う。
  （MVC で言うところの）View のみを担当する。
- JavaScript のコード中に（PHP の様に）「HTML タグ(っぽいもの)」を書ける。

### Heroku

- クラウド上のサーバの一種 です。
- 簡単にサーバをたてられて、Web サイトを作れます。
- 厳密には、PaaS（Platform as a Service: アプリケーションを実行するためのプラットフォームをインターネットを介して提供するサービス）の一種です。
- サーバや OS、データベースなどのプラットフォームを、インターネットを介して利用することができます。
- heroku の一番良いところは、ほぼ 無料 で使える点です。
- プライベートで利用する分には無料プランで十分済むので、自分はプライベートでよく使っています。
- [Heroku を使いこなす術](https://qiita.com/fuwamaki/items/f7752eb7a2727660239f)

### リバースプロキシ

- [参考元](https://www.kagoya.jp/howto/network/reverse-proxy/)
  ![img](https://www.kagoya.jp/howto/wp-content/uploads/202004a05.png)
  - **インターネットと Web サーバーの間に設置**
    - インターネットからは、あたかも Web サーバーに直接アクセスしているかようになります。
  - **Web サーバーを複数設置可能**
    - 複数ある Web サーバーをリバースプロキシが振り分けるため、各 Web サーバーの負担が軽くなり、安定したサービスを継続して提供できます。
  - **防御壁（ファイアウォール）として機能する**

### tqdm

- コンソールにプログレスバー表示できる python パッケージ

### eel

- GUI を HTML/CSS/JavaScript の WEB 技術で作ることができる Python の GUI ライブラリ
- Electron ライクな GUI ライブラリで、Numpy や Pandas などデータ処理に秀でている

### WebSocket

- WebSocket 通信とは
  - コンピュータネットワーク用のプロトコルのひとつで、リアルタイムかつ**双方向な通信**を実現するためのプロトコルです。
  - コネクション確立時に従来の HTTP 通信から WebSocket へのプロトコルの upgrade を要求し、1 度コネクションが確立されると、「ws://」あるいは「wss://」から始まる URI スキーム上でクライアント・サーバ間のデータのやりとりを連続して行うことができます。
- HTTP 通信との違い

  - HTTP 通信がリクエストを出す度に新しくコネクションを確立しなければならないのに対し、WebSocket 通信は一度コネクションを確立させると、クライアント・サーバ間のデータのやり取りを連続して行うことができます。
  - また、HTTP よりも軽量なヘッダを扱うことから、通信コストが低く、よりリアルタイム性の高いプロトコルであると言えます。
  - そのため、利用例としては、複数の人と同時に対戦するゲームや SNS などリアルタイム性が求められるアプリケーションに多く見られます。

### WSGI（ウィズギー）

- [参考元](https://qiita.com/sti320a/items/828d7bceabea5f363ad1)
- Python で Web アプリケーションと Web サーバーを接続する際に考案されたインターフェース定義
- Python の Web フレームワークごとに、サーバーと接続するためのインターフェースが異なっていたため、接続できるサーバーが制限されるという事態が生じてしまった
- インターフェースを統一して、どのフレームワークでも同じように各種サーバーに接続できるようにしよう、ということで生まれたのが WSGI

### Werkzeug（ヴェルクツォイク）

- flask にも使われている非常にシンプルな WSGI ユーティリティライブラリ
- WSGI に準拠したアプリケーションを簡単に作ることができる

# ■ クラウドサービス

## Github

public repogitory なら wiki が使える

## box.net

10GB まで無料

# ■ エンターテイメント

- [Windows10 パソコンに iTunes をインストールする方法](https://wifinomori.com/windows-itunes/)

# ■ その他

## Excel

- 100 マス計算 ⇒ 複合参照 を使う
  例)　`=$A2+B$1`

## google 検索

- "　"で囲むキーワードは、必ず検索結果に含まれる
