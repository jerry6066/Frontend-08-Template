# 学习笔记

## AST

AST，Abstract Syntax Tree，抽象语法树：以树的形式展示语法结构。首先通过词法分析生成token，每个token是不可拆分的最小单元。根据token使用LL递归得到AST。

```javascript
let regexp = /([0-9\.]+)|([ \t]+)|([\r\n]+)|(\*)|(\/)|(\+)|(\-)/g;
```

JavaScript中正则表达式写在`//`中间，比如`/abc/`，多个候选目标用`|`隔开。上述正则表达式表示匹配数字/小数点`([0-9\.]+)`，或者空格tab`([ \t]+)`，或者换行`([\r\n]+)`，或者加减乘除`(\*)|(\/)|(\+)|(\-)`。在正则表达式后面加`g`表示全局搜索：将在整个字符串中查找并返回所有匹配结果。

在有global的标识位（g）下，`RegExp`对象是有状态的，把上次匹配成功的位置记录在`lastIndex`中，可以使用`exec()`对单个字符串多次匹配。

四则运算分析：

```
<Expression>::=<AdditiveExpression><EOF> // <EOF>为终结符
// AE可以是ME，或者AE加/减ME
<AdditiveExpression>::=
	<MultiplicativeExpression> |
	<AdditiveExpression><+><MultiplicativeExpression> |
	<AdditiveExpression><-><MultiplicativeExpression>

// ME可以是一个数字，或者ME乘/除一个数字
<MultiplicativeExpression>::=
	<Number> |
	<MultiplicativeExpression><*><Number> |
	<MultiplicativeExpression></><Number>

```



