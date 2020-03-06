# Anaconda & VScode で Python環境構築 (Windows)

## 1. Anacondaを公式サイトからインストール
[Anaconda Distribution](https://www.anaconda.com/distribution/)

詳しいインストール手順は参考サイトが多くあるので、そちらをググって確認。

プロキシ下でなければ、2と3は飛ばしてください。

## 2. プロキシ設定の確認
会社のネットワークなどから、condaを使うときに必要です。
### 2.1 管理者権限でPowerShellを表示
タスクバーから検索すると見つかります。

### 2.2 下記コマンドを実行し、netshプロンプトを起動
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

### 3.4 以下コマンドを Anaconda Prompt で実行
プロキシ設定が反映されたか確認できます。

Anaconda Prompt もタスクバーから検索すると見つかります。
```console:console
conda config --show
```
3.3で書いたようになっていたら、プロキシの設定は完了です。