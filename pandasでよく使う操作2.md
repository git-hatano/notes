# Pandas でよく使う操作 2

## 初めに
```python
import pandas as pd
```

## csvの読み込み
```python
df = pd.read_csv('input.csv')
```

### for 文を使わずに、各要素に関数を適用
組み込み関数、自作関数どちらも可能
```python
# 各要素にスペースが含まれていたら削除
df["column_name"] = df["column_name"].map(lambda x: x.replace(" ", ""))

# xがパスで、ファイル名だけほしいとき
df["file_name"] = df["file_path"].map(lambda x: x.split("/")[-1])

# 複数の引数も可能
def add_seven(num1, num2):
    return num1 + num2

df["column_name"] = df["column_name"].map(lambda x: add_zero(x, 7))
```

### numpyの配列は、そのままDataFrameに代入可能
代入先のdfと同じ、行数である必要
```python
df["numpy_array"] = np.array([1,2,3,4])
```