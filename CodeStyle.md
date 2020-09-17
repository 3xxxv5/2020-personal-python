# CodeStyle

* ### 缩进

用4个空格来缩进代码

绝对不要用tab, 也不要tab和空格混用. 对于行连接的情况, 你应该要么垂直对齐换行的元素(见 :ref:`行长度 <line_length>` 部分的示例), 或者使用4空格的悬挂式缩进(这时第一行不应该有参数):
```
Yes:   # 与起始变量对齐
       foo = long_function_name(var_one, var_two,
                                var_three, var_four)

       # 字典中与起始值对齐
       foo = {
           long_dictionary_key: value1 +
                                value2,
           ...
       }

       # 4 个空格缩进，第一行不需要
       foo = long_function_name(
           var_one, var_two, var_three,
           var_four)

       # 字典中 4 个空格缩进
       foo = {
           long_dictionary_key:
               long_dictionary_value,
           ...
       }
```
```
No:    # 第一行有空格是禁止的
      foo = long_function_name(var_one, var_two,
          var_three, var_four)

      # 2 个空格是禁止的
      foo = long_function_name(
        var_one, var_two, var_three,
        var_four)

      # 字典中没有处理缩进
      foo = {
          long_dictionary_key:
              long_dictionary_value,
              ...
      }
```

* ### 命名规则
module_name, package_name, ClassName, method_name, ExceptionName, function_name, GLOBAL_VAR_NAME, instance_var_name, function_parameter_name, local_var_name.
应该避免的名称:
```
* 单字符名称, 除了计数器和迭代器.
* 包/模块名中的连字符(-)
* 双下划线开头并结尾的名称(Python保留, 例如__init__)
```
总体原则，新编代码必须按下面命名风格进行，现有库的编码尽量保持风格。
    1. 尽量单独使用小写字母‘l’，大写字母‘O’等容易混淆的字母。
    2. 模块命名尽量短小，使用全部小写的方式，可以使用下划线。
    3. 包命名尽量短小，使用全部小写的方式，不可以使用下划线。
    4. 类的命名使用CapWords的方式，模块内部使用的类采用_CapWords的方式。
    5. 异常命名使用CapWords+Error后缀的方式。
    6. 全局变量尽量只在模块内有效，类似C语言中的static。实现方法有两种，一是all机制;二是前缀一个下划线。
    7. 函数命名使用全部小写的方式，可以使用下划线。
    8. 常量命名使用全部大写的方式，可以使用下划线。
    9. 类的属性-方法和变量命名使用全部小写的方式，可以使用下划线。
    10. 类的属性有3种作用域public、non-public和subclass API，可以理解成C++中的public、private、protected，non-public属性前，前缀一条下划线。
    11. 类的属性若与关键字名字冲突，后缀一下划线，尽量不要使用缩略等其他方式。
    12. 为避免与子类属性命名冲突，在类的一些属性前，前缀两条下划线。比如：类Foo中声明__a,访问时，只能通过Foo._Foo__a，避免歧义。如果子类也叫Foo，那就无能为力了。
    13. 类的方法第一个参数必须是self，而静态方法第一个参数必须是cls。

* ### 行长度
每行不超过80个字符

以下情况除外：

长的导入模块语句
注释里的URL
不要使用反斜杠连接行。

Python会将 圆括号, 中括号和花括号中的行隐式的连接起来 , 你可以利用这个特点. 如果需要, 你可以在表达式外围增加一对额外的圆括号。
```
推荐: foo_bar(self, width, height, color='black', design=None, x='foo',
             emphasis=None, highlight=0)

     if (width == 0 and height == 0 and
         color == 'red' and emphasis == 'strong'):
```
如果一个文本字符串在一行放不下, 可以使用圆括号来实现隐式行连接:
```
x = ('这是一个非常长非常长非常长非常长 '
     '非常长非常长非常长非常长非常长非常长的字符串')
```
在注释中，如果必要，将长的URL放在一行上。
```
Yes:  # See details at
      # http://www.example.com/us/developer/documentation/api/content/v2.0/csv_file_name_extension_full_specification.html
```
```
No:  # See details at
     # http://www.example.com/us/developer/documentation/api/content/\
     # v2.0/csv_file_name_extension_full_specification.html
```


* ### 空行
顶级定义之间空两行, 方法定义之间空一行

顶级定义之间空两行, 比如函数或者类定义. 方法定义, 类定义与第一个方法之间, 都应该空一行. 函数或方法中, 某些地方要是你觉得合适, 就空一行.

* ### 注释规则
    总体原则，错误的注释不如没有注释。所以当一段代码发生变化时，第一件事就是要修改注释！注释必须使用英文，最好是完整的句子，首字母大写，句后要有结束符，结束符后跟两个空格，开始下一句。如果是短语，可以省略结束符。
    1. 块注释，在一段代码前增加的注释。在‘#’后加一空格。段落之间以只有‘#’的行间隔。比如：
    ```
    # Description : Module config.
    #
    # Input : None
    #
    #Output : None
    ```
    2. 行注释，在一句代码后加注释。比如：(但是这种方式尽量少使用)
    ```
    x = x + 1       # Increment x
    ```
    3. 避免无谓的注释。

* ### 空格原则
按照标准的排版规范来使用标点两边的空格

括号内不要有空格.

按照标准的排版规范来使用标点两边的空格
```
Yes: spam(ham[1], {eggs: 2}, [])
```
```
No:  spam( ham[ 1 ], { eggs: 2 }, [ ] )
```
不要在逗号, 分号, 冒号前面加空格, 但应该在它们后面加(除了在行尾)。
```
Yes: if x == 4:
         print x, y
     x, y = y, x
```
```
No:  if x == 4 :
         print x , y
     x , y = y , x
```
参数列表, 索引或切片的左括号前不应加空格.
```
Yes: spam(1)

no: spam (1)

Yes: dict['key'] = list[index]

No:  dict ['key'] = list [index]
```
在二元操作符两边都加上一个空格, 比如赋值(=), 比较(==, <, >, !=, <>, <=, >=, in, not in, is, is not), 布尔(and, or, not). 至于算术操作符两边的空格该如何使用, 需要你自己好好判断. 不过两侧务必要保持一致.
```
Yes: x == 1

No:  x<1
```
当'='用于指示关键字参数或默认参数值时, 不要在其两侧使用空格.
```
Yes: def complex(real, imag=0.0): return magic(r=real, i=imag)

No:  def complex(real, imag = 0.0): return magic(r = real, i = imag)
```
不要用空格来垂直对齐多行间的标记, 因为这会成为维护的负担(适用于:, #, =等):
```
Yes:
     foo = 1000  # 注释
     long_name = 2  # 注释不需要对齐

     dictionary = {
         "foo": 1,
         "long_name": 2,
         }
```
```
No:
     foo       = 1000  # 注释
     long_name = 2     # 注释不需要对齐

     dictionary = {
         "foo"      : 1,
         "long_name": 2,
         }
```

* ### 其他规则
    文档描述:
    1. 为所有的共有模块、函数、类、方法写docstrings；非共有的没有必要，但是可以写注释（在def的下一行）。
    2. 如果docstring要换行，参考如下例子,详见PEP 257
    ```
    """
    Return a foobang
    Optional plotz says to frobnicate the bizbaz first.
    """
    ```
