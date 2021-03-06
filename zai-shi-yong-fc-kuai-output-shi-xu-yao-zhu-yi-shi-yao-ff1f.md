对于FC的使用，另一个常见的错误是对输出的错误处理：导致这个错误的原因还是对FC认识的不清楚。再次强调：相比较于FB，FC是一个没有存储空间的逻辑块。如果没有数据被写至FC的OUT参数，FC将会输出一个随机值！对于FB，因为其可以使用背景数所块来存储OUT参数的数值，即使某次调用没有对OUT参数进行写操作，OUT参数依然可以输出上一次的旧值。

下面的程序将说明这一点：

程序原本的目的：

* 在OB1中调用两次FC22，将MW0，MW2作为输入参数，DB1.DBX0.0，DB1.DBX0.1分别作为输出参数赋给FC22。
* FC22检测当输入大于10时，置位输出为1
* FC22检测当输入小于-10时，复位输出为0
* FC22的输出动作死区为-10至10

此程序乍看起来是没有错误的，但是，如果OB1中调用了两次FC22，而且MW2位于死区（-10至10）之间时，MW0的数值改变将不仅仅改变DB1.DBX0.0的状态，同时会影响输出DB1.DBX0.1的数值。

![](/assets/屏幕快照 2017-10-01 下午7.38.05.png)

图1 FC和序输出编程错误举例

**故障分析:**

在上面的例五，OB1中调用了两次FC22，而且MW2们于死区（-10至10）之间时，其输出在FC22没有被赋值，DB1.DBX0.1正常情况下不应当改变数值。但是在本例中，MW0的数值改变将不仅仅改变DB1.DBX0.0的状态，同时会影响输出DB1.DBX0.1的数值。如图2。

![](/assets/屏幕快照 2017-10-01 下午7.40.42.png)

图2 FC程序佃出编程错误结果

**结论：**

对于FC的输出变量，必须要在每次执行FC时赋给一个确定的值，否则输出有可能会佃出一个随机值。下列用法都是错误的。

* 将输出变量用于上升、下降沿指令
* 将输出变量用于自保持逻辑
* 输出变量未在所在程序段中赋值

**建议：**

* 用IN/OUT变量代替OUTPUT变量
* 不论何时调用块时，FC中的OUT参数都必须被赋值。



