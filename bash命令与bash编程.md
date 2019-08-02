# bash命令

#### a. `export`

显示所有的环境变量，如果你想获取某个变量的详细信息，使用 `echo $VARIABLE_NAME`.

```
export
```

Example:

```bash
$ export
SHELL=/bin/zsh
AWS_HOME=/Users/adnanadnan/.aws
LANG=en_US.UTF-8
LC_CTYPE=en_US.UTF-8
LESS=-R

$ echo $SHELL
/usr/bin/zsh
```



#### b. `whereis`

whereis使用**系统自动构建的数据库来搜索可执行文件**，源文件和手册页面。

```
whereis name
```

Example:

```bash
$ whereis php
/usr/bin/php
```



#### c. `which`

它在**环境变量PATH指定的目录中搜索可执行文件**。此命令将打印可执行文件的完整路径。

```
which program_name 
```

Example:

```bash
$ which php
/c/xampp/php/php
```



#### d. `cat`

它可以在UNIX或Linux下用于以下目的。

- 在屏幕上显示文本文件
- **复制文本文件**
- 合并文本文件
- 创建新的文本文件

```bash
cat filename
cat file1 file2 
cat file1 file2 > newcombinedfile
```



#### e. `tail`

输出最后10行文件。**用于 -f 在文件增长时输出附加数据**。

```bash
tail filename
```



#### f. `diff`

比较文件，并列出他们的差异。

```bash
diff filename1 filename2
```



#### g. `grep`

查找文件内的文本。您可以使用grep搜索与一个或多个正则表达式匹配的文本行，并仅输出匹配的行。

```bash
grep pattern filename
```

Example:

```
$ grep admin /etc/passwd
_kadmin_admin:*:218:-2:Kerberos Admin Service:/var/empty:/usr/bin/false
_kadmin_changepw:*:219:-2:Kerberos Change Password Service:/var/empty:/usr/bin/false
_krb_kadmin:*:231:-2:Open Directory Kerberos Admin Service:/var/empty:/usr/bin/false
```

您还可以通过使用`-i`选项强制grep忽略单词大小写。`-r`可用于搜索指定目录下的所有文件，例如：

```
$ grep -r admin /etc/
```

`-w` 只搜索单词。有关`grep`详细信息，请查看以下[链接](https://www.cyberciti.biz/faq/grep-in-bash)。



#### h. `wc`

告诉你一个文件中有多少行，多少单词和多少字符。

```
wc filename
```

Example:

```
$ wc demo.txt
7459   15915  398400 demo.txt
```

`7459` 是行数, `15915` 是单词数， `398400` 是字符数.



#### i. `tr`

翻译或删除字符

*example.txt*

```
Hello World Foo Bar Baz!
```

*把所有小写字母变成为大写*

```bash
cat example.txt | tr 'a-z' 'A-Z' 
HELLO WORLD FOO BAR BAZ!
```

*把所有的空格变成换行符*

```bash
cat example.txt | tr ' ' '\n'
Hello
World
Foo
Bar
Baz!
```



#### j. `quota`

显示您的磁盘配额。

```
quota -v
```



#### k. `uname`

显示内核信息。

```
uname -a
```



#### l. `ps`

列出您的进程。

```
ps -u yourusername
```



# Bash Shell Programming

## bash中的变量：

在bash中创建变量与其他语言类似。没有数据类型。bash中的变量可以包含数字，字符，字符串等。您无需声明变量，只需为其引用分配一个值即可创建它。

Example:

```
str="hello world"
```

上面的一行创建一个变量str并给它赋值“hello world”。通过`$`放在变量名的开头来检索变量的值。

Example:

```
echo $str   # hello world
```

像其他语言一样，bash也有数组。数组是包含多个值的变量。数组的大小没有最大限制。bash中的数组为零。第一个元素被索引为元素0.在bash中创建数组有几种方法。以下给出了哪些。

Examples:

```zsh
array[0] = val
array[1] = val
array[2] = val
array=([2]=val [0]=val [1]=val)
array(val val val)
```

## bash中的函数：

几乎与任何编程语言一样，您可以使用函数以更逻辑的方式对代码段进行分组，或者实践递归的神圣艺术。声明函数只是编写函数my_func {my_code}的问题。调用一个函数就像调用另一个程序一样，你只需要写上它的名字。

```bash
functname {
    shell commands
}
```

Example:

```bash
#!/bin/bash
function hello {
   echo world!
}
hello      #这里调用函数hello

function say {
    echo $1   #这里的$1表示第一个参数
}
say "hello world!"   #这里调用函数，并且传递参数“hello world”
```

当您运行上述示例时，该hello函数将输出“world！”。上述两个功能`hello`和`say`是相同的。主要区别是功能`say`。此功能打印其接收到的第一个参数。函数内的参数以与给脚本的参数相同的方式进行处理。

## bash中的条件语句：

bash中的条件语句与其他编程语言相似。条件有许多形式，如最基本的形式是`if`表达式`then`语句，其中语句只有在表达式为真时执行。

if语句的单分支：

```bash
if [ expression ]; then #这里的expression与中括号两端必须要有空格
    语句1 - n
fi
```

if语句的双分支：

```bash
if [ expression ]; then #这里的expression与中括号两端必须要有空格
    语句
else
    语句
fi
```

if语句的多分支：

```bash
if [ expression ]; then #这里的expression与中括号两端必须要有空格
    语句1
elif [ expression ]; then
		语句2
else
		语句3
fi
```

有时，如果条件变得混乱，所以你可以使用相同的条件`case statements`。

```bash
case expression in
    pattern1 )
        statements ;;
    pattern2 )
        statements ;;
    ...
esac
```

### bash语句中的条件组合：

```bash
statement1 && statement2  # 两边的条件都为true
statement1 || statement2  # 其中一边为true

str1=str2       # str1 匹配 str2
str1!=str2      # str1 不匹配 str2
str1<str2       # str1 是否小于 str2
str1>str2       # str1 是否大于 str2
-n str1         # str1 不为空(长度大于 0)
-z str1         # str1 为空(长度为 0)

-a file         # 文件存在 
-d file         # 文件存在，是一个目录 
-e file         # 文件存在; 相同的-a 
-f file         # 文件存在，是一个常规文件（即不是目录或其他特殊类型的文件） 
-r file         # 你有读权限 
-r file         # 文件存在，不为空 
-w file         # 你有写权限 
-x file         # 你有文件的执行权限

file1 -nt file2     # file1 is newer than file2
file1 -ot file2     # file1 is older than file2

-lt     # 小于 
-le     # 小于或等于 
-eq     # 等于
-ge     # 大于或等于 
-gt     # 大于
-ne     # 不等于
```



## bash中的循环：

`for` 语法:

```bash
for x := 1 to 10 do
begin
  statements
end

for name [in list]
do
  statements that can use $name
done

for (( initialisation ; ending condition ; update ))
do
  statements...
done
```

`while` 语法:

```bash
while condition; do
  statements
done
```

`until` 语法:

```bash
until condition; do
  statements
done
```



## bash中参数的传递

\$* 与 \$@ 区别：

- 相同点：都是引用所有参数。
- 不同点：只有在双引号中体现出来。假设在脚本运行时写了三个参数 1、2、3，，则 " * " 等价于 "1 2 3"（传递了一个参数），而 "@" 等价于 "1" "2" "3"（传递了三个参数）。

```bash
#!/bin/bash
# author:菜鸟教程
# url:www.runoob.com

echo "-- \$* 演示 ---"
for i in "$*"; do
    echo $i
done

echo "-- \$@ 演示 ---"
for i in "$@"; do
    echo $i
done
```

执行脚本，输出结果如下所示：

```bash
$ chmod +x test.sh 
$ ./test.sh 1 2 3
-- $* 演示 ---
1 2 3
-- $@ 演示 ---
1
2
3
```

### Shell 特殊参数解释

首先来看几个特殊变量：$0, $#, $*, $@, $?, $$, $_

```bash
#!/bin/bash
echo $0    # 当前脚本的文件名（间接运行时还包括绝对路径）。
echo $n    # 传递给脚本或函数的参数。n 是一个数字，表示第几个参数。例如，第一个参数是 $1 。
echo $#    # 传递给脚本或函数的参数个数。
echo $*    # 传递给脚本或函数的所有参数。
echo $@    # 传递给脚本或函数的所有参数。被双引号 (" ") 包含时，与 $* 不同，下面将会讲到。
echo $?    # 上个命令的退出状态，或函数的返回值。
echo $$    # 当前 Shell 进程 ID。对于 Shell 脚本，就是这些脚本所在的进程 ID。
echo $_    # 上一个命令的最后一个参数
echo $!    # 后台运行的最后一个进程的 ID 号
```

现在保存为一个脚本，然后加上几个参数运行：

```bash
$ ./test.sh test test1 test2 test3 test4
```

返回如下：

```bash
./test.sh                      # $0
                               # $n
5                              # $#
test test1 test2 test3 test4   # $*
test test1 test2 test3 test4   # $@
0                              # $?
12305                          # $$
12305                          # $_
                               # $!
```



### 将命令的执行结果赋值给变量，如下所示：

```bash
var='pwd'
echo $var
```

此时输出：

```
/home/tobyZhao
```

### 或者也可以使用$(...)来实现同样的功能：

```bash
var=$(pwd)
echo $var
```



## 输出重定向

重定向一般通过在命令间插入特定的符号来实现。特别的，这些符号的语法如下所示:

```bash
command1 > file1
```

上面这个命令执行command1然后将输出的内容存入file1。

注意任何file1内的已经存在的内容将被新内容替代。如果要将新内容添加在文件末尾，请使用>>操作符。

### 实例

执行下面的 who 命令，它将命令的完整的输出重定向在用户文件中(users):

```bash
$ who > users
```

执行后，并没有在终端输出信息，这是因为输出已被从默认的标准输出设备（终端）重定向到指定的文件。

你可以使用 cat 命令查看文件内容：

```bash
$ cat users
_mbsetupuser console  Oct 31 17:35 
tianqixin    console  Oct 31 17:35 
tianqixin    ttys000  Dec  1 11:33 
```

输出重定向会覆盖文件内容，请看下面的例子：

```
$ echo "菜鸟教程：www.runoob.com" > users
$ cat users
菜鸟教程：www.runoob.com
$
```

如果不希望文件内容被覆盖，可以使用 >> 追加到文件末尾，例如：

```
$ echo "菜鸟教程：www.runoob.com" >> users
$ cat users
菜鸟教程：www.runoob.com
菜鸟教程：www.runoob.com
$
```



## 输入重定向

和输出重定向一样，Unix 命令也可以从文件获取输入，语法为：

```bash
command1 < file1
```

这样，本来需要从键盘获取输入的命令会转移到文件读取内容。

注意：输出重定向是大于号(>)，输入重定向是小于号(<)。

### 实例

接着以上实例，我们需要统计 users 文件的行数,执行以下命令：

```
$ wc -l users
       2 users
```

也可以将输入重定向到 users 文件：

```
$  wc -l < users
       2 
```

注意：上面两个例子的结果不同：第一个例子，会输出文件名；第二个不会，因为它仅仅知道从标准输入读取内容。

```
command1 < infile > outfile
```

**同时替换输入和输出，执行command1，从文件infile读取内容，然后将输出写入到outfile中。**

### 重定向深入讲解

一般情况下，每个 Unix/Linux 命令运行时都会打开三个文件：

- 标准输入文件(stdin)：stdin的文件描述符为0，Unix程序默认从stdin读取数据。
- 标准输出文件(stdout)：stdout 的文件描述符为1，Unix程序默认向stdout输出数据。
- 标准错误文件(stderr)：stderr的文件描述符为2，Unix程序会向stderr流中写入错误信息。

默认情况下，command > file 将 stdout 重定向到 file，command < file 将stdin 重定向到 file。

如果希望 stderr 重定向到 file，可以这样写：

```
$ command 2 > file
```

如果希望 stderr 追加到 file 文件末尾，可以这样写：

```
$ command 2 >> file
```

**2** 表示标准错误文件(stderr)。

如果希望将 stdout 和 stderr 合并后重定向到 file，可以这样写：

```
$ command > file 2>&1

或者

$ command >> file 2>&1
```

如果希望对 stdin 和 stdout 都重定向，可以这样写：

```
$ command < file1 >file2
```

command 命令将 stdin 重定向到 file1，将 stdout 重定向到 file2。



