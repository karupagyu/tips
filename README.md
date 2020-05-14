# ■■■■■ 開発環境の構築

## python

- [Python 3.7 のインストール（Windows上）](https://www.kkaneko.jp/tools/win/python.html)
- [MSVC ビルドツール 2019 （Build Tools for Visual Studio 2019） のインストール（Windows 上）](https://www.kkaneko.jp/tools/win/buildtool.html)
- [Visual Studio Community 2019 vesion 16.2, MSVC ビルドツールのインストール（Windows 上）](https://www.kunihikokaneko.com/tools/win/vs2019.html)
- [用語説明](https://www.kkaneko.jp/tools/tools.html)
- [Python3.7をインストールしてpathを通して、pipでパッケージを入れる](https://karupoimou.hatenablog.com/entry/2019/04/29/064646)

## PATH設定

### Windows (コマンドプロンプト用)

- PATH確認：
`echo %PATH:;=&echo.%`
- PYTHONPATHにc:\hogeを追加：
`set PYTHONPATH=%PYTHONPATH%;C:\hoge`
- PYTHONPATHをPATHに追加：
`set PATH = %PATH%;%PYTHONPATH`

### Linux

1. 環境変数にパスを追加  
    `echo export PATH='/usr/local/bin:$PATH' >> ~/.bash_profile`  
    export PATH=/usr/local/bin:$PATH を User/ユーザー名/.bash_profile に書き込んでいます。
2. bashの設定を再読み込み  
    `source ~/.bash_profile`

## wget

Windowsは WSLで使える。  

- [-P]で保存先指定して取得：`wget -P [savedir] [http://***]`
- [wgetでこういう時はこうする!!](https://qiita.com/hirohiro77/items/b774908436ec032df719)

## Git

- [Git for Windows インストール](https://qiita.com/elu_jaune/items/280b4773a3a66c7956fe)
- [TortoiseGit セットアップ](https://qiita.com/SkyLaptor/items/6347f38c8c010f4d5bd2)
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

## vscode

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

## WSL

- [WSL (Windows Subsystem for Linux)の基本メモ](https://qiita.com/rubytomato@github/items/fdfc0a76e848442f374e)
- [Windowsで環境を極力汚さずにPythonを動かす方法 (WSL利用 Windows10)](https://qiita.com/rhene/items/ff11c7850a9a7617c50f)
- [pythonコマンドでpython3を実行したい(alias変更)](https://qiita.com/houtarou/items/c7fa8006eef9e30ffad5)
- wslランチャー : コマンドプロンプトでwslと入力しても起動できる

## Hyper-V / WSL2

- [WSL2とHyper-Vの関係](https://qiita.com/matarillo/items/ca1eecf8f9a3cd76f9ce)
- [WSL2インストール](https://www.geekfeed.co.jp/geekblog/wsl2-with-windows10-insider-preview-build)  
※WSL2は正式リリース前なので、導入するとWindowsが不安定になる可能性があります。(2020/4/1)

## CUDA (Windows)

- [NVIDIA CUDA ツールキット 10.1 のインストール（Windows 上）](https://www.kunihikokaneko.com/tools/win/cuda10.html)
- [nvidia-smiコマンドの詳細ついて](https://qiita.com/miyamotok0105/items/1b34e548f96ef7d40370)

## Terminal

- [ColorTool を使ってコンソールを見やすくする](https://qiita.com/yoshikingt/items/21d9e3fb8b8f22ab3476)
- [バッチ（.bat）をダブルクリックで実行後、ウィンドウを閉じないようにする](https://ameblo.jp/one-of-the-wnet/entry-10111695003.html)
- [vscodeのターミナルで自動コピーする方法](https://teratail.com/questions/177087)
- [WSLでマウス操作でコピー＆ペーストする方法](https://ex1.m-yabe.com/archives/3388)

## windows 10 (右クリック、共有フォルダ)

- [Windows10だけが、共有フォルダにアクセスできない原因と対処法](https://www.brain-network.ne.jp/qa/windows10-kyouyu-folder.html)
- [エクスプローラの詳細表示を変更](https://www.billionwallet.com/windows10/explorer-view.html)
- WSL起動のショートカット  
「Shift+右クリック」⇒「Linuxシェルをここに開く」

## windows 10 右クリック

- [右クリックの重いメニューを調べるには CCleaner を使用する](https://qiita.com/Q11Q/items/9fd5083ae71e32a577cd)
- [OneDriveのメニュー非表示](https://news.mynavi.jp/article/windows-460/)
- [レジストリで非表示にする](https://itjo.jp/windows/context-menu-shorten/)
- [SendToフォルダにショートカットを作成](https://www.tipsfound.com/windows10/07009)  
sendtoの場所 :  `C:\Users\%USERNAME%\AppData\Roaming\Microsoft\Windows\SendTo`

## pyenv / pip

- [Pythonで Pipenvを使う](https://narito.ninja/blog/detail/58/#pipfile)
- [pipでrequirements.txtを使ってパッケージ一括インストール](https://note.nkmk.me/python-pip-install-requirements/)

※pipenvより venvを使う方がいいかも

## VirtualBox

- [WSL上にXサーバをインストールしてGUIを実現する（VcXsrv編）](https://www.atmarkit.co.jp/ait/articles/1812/06/news040.html)
- [Windows10にVirtualBoxとUbuntuをインストール](https://qiita.com/pyon_kiti_jp/items/0be8ac17439abf418e48)

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

## Linux にインストールするパッケージ

- git : `sudo apt-get install git-all`

## jq (JSON整形ツール)

- [Windowsにinstall](https://qiita.com/amemolee/items/ec1f1f2eab1c4c25a2f9)
- [Linuxにinstall](https://qiita.com/rubytomato@github/items/fdfc0a76e848442f374e#jq)
- [使い方](https://qiita.com/takeshinoda@github/items/2dec7a72930ec1f658af)

## サクラエディタ

- [初期設定](https://proengineer.internous.co.jp/content/columnfeature/5348)
- 長いクエリ文を "&" で改行する方法
  - 置換ウインドウを開く(Ctrl + r)
  - 置換後の文字を「\r\n」にする。正規表現にチェックを付ける。

## Windows タッチキーボード

- iPadでリモデスAppからwindowsを操作する時に便利
- [表示方法]：タスクバー右クリック -> タッチキーボードボタンを表示
- [基本設定]：以下の機能をオン
  - 「タブレットモードでなく、キーボードが接続されていない場合に、タッチキーボードを表示する」
  - 多言語ヒント -> ヒントを表示する

# ■■■■■ クラウドサービス

## Github

public repogitory ならwikiが使える

# ■■■■■ コーディング

## pytorch

- [pyTorchでCNNsを徹底解説](https://qiita.com/mathlive/items/8e1f9a8467fff8dfd03c)
- [YOLO V3](http://starpentagon.net/analytics/yolo_v3_on_mac)
- [detectron2(windows)](https://github.com/conansherry/detectron2)

## python系

### pythonプロジェクトのおすすめフォルダ構成

- [VS CodeによるPython開発環境のテンプレ](https://qiita.com/kazetof/items/870d47d8f6b961e78acc)

### path

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

### cv2のインテリセンス

- [vscodeでcv2のインテリセンスを表示するされない問題](https://qiita.com/FXsimone/items/577e3924f40aa4a9d4ea)
- setting.jsonで pylintの引数に `--extension-pkg-whitelist=cv2` を設定する

### vscode (Remote WSL)

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

### pip インストールしたパッケージの場所を調べる

- `pip show [パッケージ名]`

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

# ■■■■■ エンターテイメント

- [Windows10パソコンにiTunesをインストールする方法](https://wifinomori.com/windows-itunes/)

# ■■■■■ その他

## Excel

- 100マス計算⇒ 複合参照 を使う  
例)　```=$A2+B$1```

# ■■■■■ Ubuntu

## [ワークスペース](https://www.pandanoir.info/entry/2018/02/21/193000)

## コーデックのインストール

`sudo apt-get -y install ubuntu-restricted-extras`

## 時刻設定

`sudo timedatectl set-local-rtc true`

## [man日本語設定](https://linuxfan.info/ubuntu-debian-ja-manpages)

- `sudo apt install -y manpages-ja manpages-ja-dev`
- `man date` 日本語になっていたらOK

## ダウンロードした.debファイル

- `/var/cache/apt/archives/` にキャッシュされています。このキャッシュをクリアするには、`sudo apt clean`を実行します。

## chrome インストール

```terminal
sudo sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list'
sudo wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
sudo apt update
sudo apt install google-chrome-stable
```
