# Numpy学习笔记简单汇总

参考资料（references）:

- 1.numpy-100 exercises:[GitHub - rougier/numpy-100: 100 numpy exercises (with solutions)](https://github.com/rougier/numpy-100)

- 2.官方文档offical documentation

- 3.https://hakk.gg/numpy-illustrated-the-visual-guide-to-numpy/

**基本性质**

- .ndim,  .shape, .size, .dtype, .itemsize, .data

**如何创建**

```python
(1)
import numpy as np
arr = np.array([1,2,3,4], dtype=np.float)

(2)
np.zeros((3,4)) #二维数组
np.ones((2,3,4),dtype=np.int) #三维数组

还有：zeros_like, ones_like, empty, empty_like

(3)
np.arange(0,10,2) #0-10，+2一步
np.linspace(0,2,9) #0-2按照9等分

（4）
np.random.randint(0.10,3)#uniform0-10
np.random.rand(3)#uniform0-1
np.random.randn(3)#normal miu=1 sigma=0
np.random.uniform(1,10,3)#uniform1-10
np.random.normal(5,2,3)#normal miu=1 sigma=0
```

**运算**

主要是关注矩阵运算的点乘 也即dot()，这在机器学习矩阵运算里面必备

```python
# 加减乘除
# np.sqrt(); np.exp(); np.log()
# np.dot(); np.cross()
# np.sin(),np.arcsin()
# np.hypot()

# np.floor()
# np.ceil()
# np.round()


# .max()
# .min()
# .sum()
# .var()
# .argmax() -> return the index
# .argmin() ->返回的是Index
# .mean()
# .std()
# both std and var ignore Bessel’s correction,
# 如果要修正的话，就要指定自由度，也即在后面加上自由度参数delta degress of freedom

res1, res2, res3, res4 = [], [], [], []
for i in range(1000):
    a = np.random.randn(100)
    res1.append(a.std())
    res2.append(a.std(ddof=1))
    res3.append(a.std(ddof=1.5))
    res4.append(a.std(ddof=2))
```

```python
np.argmin(x) #最小值的索引
np.argmax(x) #最大值的索引
np.random.shuffle() #打乱数组顺序
np.sort(x) #数组排序
np.argsort(x) #按大小排序后对应的原数组的索引
np.partition(l,3)#把小于3 的放在前面，大于3的放在后面，但不进行排序
np.argpartition(l,3)#把小于3 的放在前面，大于3的放在后面，但不进行排序,返回的是索引
```

**索引**

```python
import numpy as np
a = np.arange(1,6)
a[1], a[2:4], a[-2:], a[::2], a[[1,3,4]]
#结果：(2, array([3, 4]), array([4, 5]), array([1, 3, 5]), array([2, 4, 5]))

np.where()
```

```python
# fancy indexing
np.sum(x <= 3) #小于等于3 的个数
np.sum(X % 2 == 0, axis=0) #能整除2 的每列的个数
np.sum(X % 2 == 0, axis=1) #能整除2 的每行的个数
np.any(x == 0) #是否存在x=0
np.all(x >= 0) #是否每个值都大于等于0
```

**一维和二维的数据转换**

![](https://miro.medium.com/max/788/1*d9j1sDyzpBXLxK11vU-Mtw.png)





**三维数据**

(z,y,x). The first index is the number of the plane, then the coordinates go in that plane

在图片中的数据就是(y,x,z),plane是在最后一个值上面显示，以下是通常3D数组和图片的数组不一样的地方：

![](https://miro.medium.com/max/788/1*NNm3gGO8sEinq6JYlI84dg.png)



**einsum函数非常重要！！**

![](https://miro.medium.com/max/788/1*uGKflexdelNxiireoI8YJw.png)

简单介绍einsum函数： https://mp.weixin.qq.com/s/m4H6vLLaFFoD9hkMULzvQA



*(update loading......)*
