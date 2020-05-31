# Pandas でよく使う操作

## 初めに
```python
import pandas as pd
```

## csvの読み込み
```python
df = pd.read_csv('input.csv')
```

### 初めの5行，終わりの3行を表示
```python
print(df.head())
print(df.head(3))
```

### 列名，行名をリスト形式で取得
```python
indexs_list = df.index
columns_list = df.columns
```

### 各列のデータ型を取得
```python
print(df.dtypes)
```

### 列数，行数を取得
```python
row, col = df.shape[:]
```

### データ（数値や文字）を座標値で取得し、結果を代入
```python
row = 0
col = 0

data = df.iloc[row, col]
df.iloc[row, col] = data
```

### 特定の列を一括で計算し、結果を代入
```python
df['col'] = df['col']*2
```

### 特定の列を抽出
```python
# 1列のとき
df = df['col1']

# 2列のとき
df = df[['col1', 'col2']]
```

### dfに新しい列を追加し、初期化
```python
df['new_col'] = None
```

### 特定の列に他の列を代入
```python
df['new_col'] = df['col1'] + df['col2']
```

***

### 条件を満たす行を抽出
for文で探索する手間を省ける
```python
#'col'列で値が10の行はTrue
mask = (df['col'] == 10)
df = df[mask]
```

### 特定の列で条件を満たす行に値を代入
```python
#'col1'列で値が12より大きいとき，col2に0を代入
mask = (df['col1'] > 12)
df.loc[mask, 'col2'] = 0
```

### 特定の列でデータの重複がある行を削除
```python
#重複行がTrue
mask_duplicate = df.duplicated(subset='col')
#'~'は否定，重複行がFalse
df = df[~mask_duplicate]
```

***

### indexの割り振り直し
```python
df = df.reset_index()
```

### 特定の列をindexにする
```python
df = df.set_index('col', inplace=True)
```

### 列名の変更
辞書形式（変更前：変更後）で記述
```python
df = df.rename(columns={'before1': 'After1', 'before2': 'After2'})
```

### 列の順番変更
```python
new_colname = ['col3', 'col2', 'col1']
df = df.loc[:, new_colname]
```

***

### 統計量の算出
```python
#平均
mean = df.mean()
#分散
var = df.var()
#相関係数
corr = df.corr()
#データの概要
print(df.describe())
```

***

### 特定の列を削除
```python
df = df.drop('col', axis=1)
```

### 欠損値のある行を削除
```python
df = df.dropna()
```

### 欠損値の補完
```python
mean = df.mean()
df_fillna = df.fillna(mean)
```

### 列単位で欠損値の個数をカウント
```python
count_na = df.isnull().sum()
```

***

### numpyのDataframe化
```python
np_array = np.array([1,2,3], [4,5,6])
column_list = ['col1', 'col2']
df_new = pd.DataFrame(data=np_array, columns=column_list)
```

### Dataframeのnumpy化
```python
np_array = df.values
```