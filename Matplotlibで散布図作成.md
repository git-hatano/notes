# Matplotlib で散布図作成


### はじめに
```python
# 必須
import matplotlib.pyplot as plt
import seaborn as sns
sns.set()

# 適宜
import numpy as np
import pandas as pd
```

### 2次元散布図
例として、サンプルが[y, x, label]という形式で、
POSITIVEクラスとNEGATIVEクラスで色分けした散布図の作成
```python
POSITIVE = 1
NEGATIVE = -1

def plot_scatter_2d(df, out_path):
    # numpy配列に変換 [y, x, label]
    data_array = df.values()
    INDEX_Y = 0
    INDEX_X = 1
    LABEL = 2

    # グラフを埋め込むエリアの宣言
    fig = plt.figure()
    # 1,1,1：figを1×1に分割したときの1つ目 
    ax = fig.add_subplot(1,1,1)

    # 散布図設定(色分けしたい分用意)
    # POSITIVE
    ax.scatter(data_array[data_array[:, LABEL]==POSITIVE][:,INDEX_X],
               data_array[data_array[:, LABEL]==POSITIVE][:,INDEX_Y],
               alpha=0.1, c="red", label="Positive")
    # NEGATIVE
    ax.scatter(data_array[data_array[:, LABEL]==NEGATIVE][:,INDEX_X],
               data_array[data_array[:, LABEL]==NEGATIVE][:,INDEX_Y],
               alpha=0.1, c="blue", label="Negative")

    # 書式の設定
    ax.set_title("Scatter plot 2D")
    ax.set_xlabel("x", color="red")
    ax.set_ylabel("y", color="red")
    ax.legend()

    # 散布図の保存
    fig.savefig(out_path)

```


### 3次元散布図
例として、サンプルが[y, x, z, label]という形式で、
POSITIVEクラスとNEGATIVEクラスで色分けした散布図の作成
```python
from mpl_toolkits.mplot3d import Axes3D


POSITIVE = 1
NEGATIVE = -1

def plot_scatter_3d(df, out_path):
    # numpy配列に変換 [y, x, z, label]
    data_array = df.values()
    INDEX_Y = 0
    INDEX_X = 1
    INDEX_Z = 2
    LABEL = 3

    # グラフを埋め込むエリアの宣言
    fig = plt.figure()

    # 図1: 3次元散布図
    # figを2×2に分割したときの1つ目(左上)
    ax1 = fig.add_subplot(2,2,1)

    # 散布図設定(色分けしたい分用意)
    # POSITIVE
    ax1.scatter(xs=data_array[data_array[:, LABEL]==POSITIVE][:,INDEX_X],
                ys=data_array[data_array[:, LABEL]==POSITIVE][:,INDEX_Y],
                zs=data_array[data_array[:, LABEL]==POSITIVE][:,INDEX_Z],
                alpha=0.1, c="red", label="Positive")
    # NEGATIVE
    ax1.scatter(xs=data_array[data_array[:, LABEL]==NEGATIVE][:,INDEX_X],
                ys=data_array[data_array[:, LABEL]==NEGATIVE][:,INDEX_Y],
                zs=data_array[data_array[:, LABEL]==NEGATIVE][:,INDEX_Z],
                alpha=0.1, c="blue", label="Negative")
    # 書式の設定
    ax1.set_title("Scatter plot 3D")
    ax1.set_xlabel("x", color="red")
    ax1.set_ylabel("y", color="red")
    ax1.set_zlabel("z", color="red")
    ax1.legend()


    # 図2: 2次元散布図(x-y)
    # figを2×2に分割したときの2つ目(右上)
    ax2 = fig.add_subplot(2,2,2)
    #POSITIVE
    ax2.scatter(data_array[data_array[:, LABEL]==POSITIVE][:,INDEX_X],
                data_array[data_array[:, LABEL]==POSITIVE][:,INDEX_Y],
                alpha=0.1, c="red", label="Positive")
    # NEGATIVE
    ax2.scatter(data_array[data_array[:, LABEL]==NEGATIVE][:,INDEX_X],
                data_array[data_array[:, LABEL]==NEGATIVE][:,INDEX_Y],
                alpha=0.1, c="blue", label="Negative")
    # 書式の設定
    ax2.set_xlabel("x", color="red")
    ax2.set_ylabel("y", color="red")
    ax2.legend()


    # 図3: 2次元散布図(x-z)
    # figを2×2に分割したときの3つ目(左下)
    ax3 = fig.add_subplot(2,2,3)
    #POSITIVE
    ax3.scatter(data_array[data_array[:, LABEL]==POSITIVE][:,INDEX_X],
                data_array[data_array[:, LABEL]==POSITIVE][:,INDEX_Z],
                alpha=0.1, c="red", label="Positive")
    # NEGATIVE
    ax3.scatter(data_array[data_array[:, LABEL]==NEGATIVE][:,INDEX_X],
                data_array[data_array[:, LABEL]==NEGATIVE][:,INDEX_Z],
                alpha=0.1, c="blue", label="Negative")
    # 書式の設定
    ax3.set_xlabel("x", color="red")
    ax3.set_ylabel("z", color="red")
    ax3.legend()


    # 図4: 2次元散布図(y-z)
    # figを2×2に分割したときの4つ目(右下)
    ax4 = fig.add_subplot(2,2,4)
    #POSITIVE
    ax4.scatter(data_array[data_array[:, LABEL]==POSITIVE][:,INDEX_Y],
                data_array[data_array[:, LABEL]==POSITIVE][:,INDEX_Z],
                alpha=0.1, c="red", label="Positive")
    # NEGATIVE
    ax4.scatter(data_array[data_array[:, LABEL]==NEGATIVE][:,INDEX_Y],
                data_array[data_array[:, LABEL]==NEGATIVE][:,INDEX_Z],
                alpha=0.1, c="blue", label="Negative")
    # 書式の設定
    ax4.set_xlabel("y", color="red")
    ax4.set_ylabel("z", color="red")
    ax4.legend()

    # 散布図の保存
    fig.savefig(out_path)

```