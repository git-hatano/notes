# condaでよく使うコマンド例

## Anaconda のインストール場所の確認
```console:console
conda config --show
```

## 仮想環境を作る
```console:console
conda create -n （仮想環境名） python=（作りたいPythonのバージョン）
```
以下、仮想環境名をpy36、pythonのバージョンを3.6、としたときの例。
```console:console
conda create -n py36 python=3.6
```

## 仮想環境の起動
```console:console
conda activate py36
```

## 仮想環境内のライブラリを確認
```console:console
conda list
```

## ライブラリのインストール
```console:console
conda install (ライブラリ名)
```

## 仮想環境の終了
仮想環境の切替時などに利用。
```console:console
conda deactivate
```

## 仮想環境の削除
挙動がおかしくなったときお世話になる。
```console:console
conda remove -n py36
```

