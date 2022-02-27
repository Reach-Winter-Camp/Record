# Reach中绝对值的计算

Reach官方库提供了`abs(i)`这个函数来计算`i`的绝对值，然而计算的`i`是`int`类型，结果返回的是`UInt`类型。

[原文链接](https://docs.reach.sh/rsh/compute/#rsh_abs)

> `abs(i)` returns the absolute value of an `Int`, The return value is of type `UInt`.

而在Reach程序中我们定义的数往往使用的是`UInt`类型，那么在计算绝对值前，我们应该先转换为`int`类型。

利用Reach官方库提供的`int(Bool, UInt)`函数或者前面添加`+`,`-`号来进行`UInt`到`int`的类型转换。

[原文链接](https://docs.reach.sh/rsh/compute/#rsh_int)

> `int(Bool, UInt)` is shorthand for defining an `int `record. You may also use the `+` and `-` unary operators to declare integers instead of `UInt`s.

```js
int(Pos, 4);	// 表示 4
int(Neg, 4);	// 表示 -4
-4 				// 表示 4 : Int类型
 4				// 表示 4 : UInt类型
```

## 例子：

我们现在有3个数字`num1`,`num2`和`target`都是`UInt`类型，我们想比较下`num1`与`num2`谁与`target`在数值上更接近，就用以下代码实现：

```js
const temp1 = int(Pos, num1);
const temp2 = int(Pos, num2);
const tempTarget = int(Pos, target);

const Distance1 = abs(isub(temp1, tempTarget));
const Distance2 = abs(isub(temp2, tempTarget));
```

其中`isub(x, y)`是Reach官方库提供的对2个`int`类型的数的差值计算。

[原文链接](https://docs.reach.sh/rsh/compute/#rsh_int)

> `isub(x, y)` subtracts the `Int` `y` from the `Int` `x`.

