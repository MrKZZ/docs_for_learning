## python 中编码问题的解决：

参考相关博客：https://liujiacai.net/blog/2016/06/30/python2-encoding/

python2中字符串有两种字符类型，str和Unicode，区别是：

str is text representation in bytes, unicode is text representation in characters.

在 Python 2 中的`str`类型相当于其他语言的`byte`类型。

```python
>>> "你好"
'\xe4\xbd\xa0\xe5\xa5\xbd'
```

`在 Python 2 如果想表示 `unicode` 类型，有下面三种方式：

```python
>>> u"你好"
u'\u4f60\u597d'
>>> "你好".decode("utf8")
u'\u4f60\u597d'
>>> unicode("你好", "utf8")
u'\u4f60\u597d'
```

python2中默认编码为ascii，如果str与unicode相互转化时，如果没有明确指定编码方式就会默认使用这个编码。（实际上python中对于字符串的编码包含一中默认ascii编码以及两种str与unicode编码）

![屏幕快照 2019-03-21 下午1.53.48](/Users/kangzhezhou/Desktop/屏幕快照 2019-03-21 下午1.53.48.png)