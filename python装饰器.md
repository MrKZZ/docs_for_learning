# python装饰器

装饰器本质上是一个python函数或者是类，可以让其他函数在不需要作任何修改的前提下增加额外的功能。

```python
def foo():
    print("foo")

def bar(func):
    func()

bar(foo)	
```

举例如下：

```python
def foo():
    print('i am foo')
    
def use_logging(func):
    logging.warn("%s is running" % func.__name__)
    func()

use_logging(foo)
```

这样做逻辑上是没问题的，功能是实现了，但是我们调用的时候不再是调用真正的业务逻辑 foo 函数，而是换成了 use_logging 函数，这就破坏了原有的代码结构， 现在我们不得不每次都要把原来的那个 foo 函数作为参数传递给 use_logging 函数，那么有没有更好的方式的呢？当然有，答案就是装饰器。

```python
def use_logging(func):

    def wrapper():
        logging.warn("%s is running" % func.__name__)
        return func()   # 把 foo 当做参数传递进来时，执行func()就相当于执行foo()
    return wrapper

def foo():
    print('i am foo')

foo = use_logging(foo)  # 因为装饰器 use_logging(foo) 返回的时函数对象 wrapper，这条语句相当于  foo = wrapper
foo()                   # 执行foo()就相当于执行 wrapper()
```

use_logging 就是一个装饰器，它一个普通的函数，它把执行真正业务逻辑的函数 func 包裹在其中，看起来像 foo 被 use_logging 装饰了一样，use_logging 返回的也是一个函数，这个函数的名字叫 wrapper。在这个例子中，函数进入和退出时 ，被称为一个横切面，这种编程方式被称为面向切面的编程。

上面的实现方式转换成装饰器就是这样的：

```python
def use_logging(func):

    def wrapper():
        logging.warn("%s is running" % func.__name__)
        return func()
    return wrapper

@use_logging				 #相当于foo = use_logging(foo)
def foo():
    print("i am foo")

foo()
```

这里调用foo，相当于调用use_logging(func)，并将函数本身当参数传入。



