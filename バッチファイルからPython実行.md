# バッチファイルから Python を実行する方法

Anaconda の環境を指定して Python を実行 (Windows)


実行したいバッチファイル例 (batch_file.bat)

```comannd
@echo off

python python_file.py

pause
```

## 1. Anaconda prompt を起動

## 2. Anaconda の使いたい環境を起動

例として、py36という環境を用いる場合

```comannd
conda activate py36
```

## 3. バッチファイルがあるフォルダへ移動

Anaconda prompt は、デフォルトで C:\Users\name がカレントディレクトリになっている

必要に応じて、バッチファイルのあるドライブへ移動

```comannd
cd /d D:

cd path\to\dir
```

## 4. バッチファイルの実行

```comannd
batch_file.bat
```