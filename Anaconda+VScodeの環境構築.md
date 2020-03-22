# Anaconda + VScode で Python-Opencv 環境構築 (Windows)

## 1. Anacondaを公式サイトからインストール
[Anaconda Distribution](https://www.anaconda.com/distribution/)

詳しいインストール手順は参考サイトが多くあるので、そちらを確認。

プロキシ下でなければ、2と3は飛ばしてください。

## 2. プロキシ設定の確認
会社のネットワークなどから、condaを使うときに必要です。
### 2.1 管理者権限でPowerShellを表示
タスクバーから検索すると見つかります。

### 2.2 PowerShellにて、下記コマンドを実行し、netshプロンプトを起動
```console:console
netsh
```

### 2.3 netshプロンプトにて、下記コマンドを実行し、netsh winhttpプロンプトを起動
```console:console
winhttp
```

### 2.4 netsh winhttpプロンプトにて、下記コマンドを実行
```console:console
show proxy
```
現在のプロキシ設定に関する情報が表示されます。

後ほど、 .condarc を書くときに必要なのでメモ。

## 3.  .condarc の作成
### 3.1 適当なテキストファイル（temp.txtなど）を作成
### 3.2 作成したファイルの名前をPowerShellで .condarc に変更
```console:console
ren temp.txt .condarc
```

### 3.3 .condarc にプロキシの設定を追記
```python
proxy_servers:
    http: http://（調べたドメイン）:（調べたポート番号）
    https: https://（調べたドメイン）:（調べたポート番号）
```
以下、書き方の例。
```python
proxy_servers:
    http: http://temp.co.jp:0000
    https: https://temp.co.jp:0000
```

### 3.4 .condarc をAnacondaフォルダ直下に置く
以下のコマンドで、Anacondaの場所を確認することができます。
```console:console
conda info
```

### 3.5 以下コマンドを Anaconda Prompt で実行
プロキシ設定が反映されたか確認できます。

Anaconda Prompt もタスクバーから検索すると見つかります。
```console:console
conda config --show
```
3.3で書いた内容が表示されていたら、プロキシの設定は完了です。

## 4. 仮想環境の作成
Anaconda自体にも"base"と呼ばれる環境は入ってます。

しかし、その環境が壊れてしまうとAnaconda自体を再インストールする必要が出てくるので、

仮想環境を作ったほうが無難です。

### 4.1 仮想環境を作る
Anacondaプロンプトにて、下記コマンドを実行。
```console:console
conda create -n （仮想環境名） python=（作りたいPythonのバージョン）
```
以下、仮想環境名をpy36、pythonのバージョンを3.6、としたときの例。
```console:console
conda create -n py36 python=3.6
```

### 4.2 仮想環境の起動
Anacondaプロンプトにて、下記コマンドを実行。
```console:console
conda activate py36
```

### 4.3 Opencv のインストール（ここ重要）
ライブラリのインストールには、2つの方法があります。
```
・Anaconda Navigatorを利用してインストール

・Anacondaプロンプトを利用してインストール
```
Anaconda Navigator を利用してインストールすることで以下のメリットがあります。
```
・ライブラリ間の整合性の管理を行ってくれる

・VScodeでソースコードを実行したときに、"DLL error" が起きなかった（体験談）
```

Anaconda Navigator はタスクバーから検索すると見つかります。

詳しいインストール方法は参考サイトが多くあるので、そちらを確認。

ちなみに、Anacondaプロンプトでプログラムを実行する場合、この工程で終了して問題ありません。

## 5. 環境変数の設定
### 5.1 コントロールパネルを起動
コントロールパネルはタスクバーから検索すると見つかります。

### 5.2 "システムとセキュリティ" を選択

### 5.3 "システム" を選択

### 5.4 "システムの詳細設定" を選択

### 5.5 "環境変数" を選択

### 5.6 変数内の "Path" を編集

### 5.7 以下のパスを "環境変数名" の編集に追加
```
C:\Path\to\anaconda3\（仮想環境名）
C:\Path\to\anaconda3\（仮想環境名）\Scripts
C:\Path\to\anaconda3\（仮想環境名）\Library\bin
```
以下、仮想環境名をpy36としたときの例。
```
C:\Path\to\anaconda3\py36
C:\Path\to\anaconda3\py36\Scripts
C:\Path\to\anaconda3\py36\Library\bin
```
### 5.8 OKでウィンドウを閉じる
☓でウィンドウを閉じると環境変数の変更が反映されない。

## 6. VScode のインストール
以下サイトから、Windows用のインストーラーをダウンロード。

[Download Visual Studio Code](https://code.visualstudio.com/download)

詳しいインストール手順は参考サイトが多くあるので、そちらを確認。

## 7. VScodeの設定

### 7.1 VScodeの左下の歯車マークから設定を選択

### 7.2 "設定の検索" から "Python: Python Path" を選択

### 7.3 利用する仮想環境の "python.exe" までのパスを記入
```
C:\Path\to\anaconda3\（仮想環境名）\python.exe
```

以上で、VScodeでプログラムの実行、デバッグも可能になります。

