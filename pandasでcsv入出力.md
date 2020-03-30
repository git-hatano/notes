# Pandas で csvファイルの入出力

## 初めに
```python
import pandas as pd
import openpyxl
```

## 入力
基本的な方法
```python
df = pd.read_csv('input.csv')
```

1行目をヘッダとして読み込まない場合
```python
df = pd.read_csv('input.csv', header=None)
```

csvに日本語を含む場合
```python
df = pd.read_csv('input.csv', encoding='SHIFT-JIS')
```

列数が行によって一定ではない場合
```python
def int_colIndex(column_name):
    #列名'A'を'1'に変換
    return openpyxl.utils.column_index_from_string(column_name)

#必要な列までの列名を作成
start_col = int_colIndex('A')
end_col = int_colIndex('N')
column_name = range(start_col-1, end_col+1)

df = pd.read_csv('input.csv', header=None, names=column_name)
```


## 出力
csv形式で出力
```python
#header, index: 列名, 行名の有無を指定
df.to_csv('output.csv', header=True, index=False)
```

Excelで開いたときに，文字化けしないように出力
```python
df.to_csv('output.csv', encoding='utf_8_sig', header=True, index=False)
```

xlsx形式で出力
```python
df.to_excel('output.xlsx', header=True, index=False)
```

## Tips
Pandasの行・列数は，0から始まる

Openpyxlの行・列数は，1から始まる