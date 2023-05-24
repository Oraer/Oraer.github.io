> 计算皮尔逊系数遇到错误TypeError: No loop matching the specified signature and casting was found for ufunc add

```
TypeError: No loop matching the specified signature and casting
was found for ufunc add
```

from scipy.stats import pearsonr

当我计算pearsonr系数时，报错如下：

```
pear = pearsonr(y_test, y_pred)
print("\n pearsonor:", pear)
```



```
TypeError: No loop matching the specified signature and casting
was found for ufunc add
```

究其原因：是因为多了一个维度导致的

`y_pred`的shape为（127,1）

```py
y_pred.shape
>> (127, 1)
```

(.., 1)是根本原因，使用np.squeeze()将这个维度移出就能这解决这个问题

```
np.squeeze(y_pred).shape
(127,)
```

