### 虽然没有强迫症，但是看着idea上面给我好多的warnings还是有点不高兴，今天刚好有空整理一下哪些地方idea建议我优化代码的。


## 1、Access can be private
This inspection reports all fields, methods or classes, found in the specified inspection scope, that may have their access modifier narrowed down。



只有类内部调用的方法，从public改成private【使可访问性最小化】。

## 2、Variable XXX is never used;

定义的变量没有用，忘记删了
## 3、Explicit type argument String, String can be replaced with <> 
warning details ：This inspection reports all new expressions with type arguments which can be replaced with diamond type <>
Such <> syntax is not supported under Java 1.6 or earlier JVM

在语言中添加泛型大大提高了编译时类型检查，并大大消除了对构造函数的需要【不用大量重载构造函数】。不幸的是，它还增加了声明的冗长，例如：
Map<String, String> smsParamsMap = new HashMap<String, String>();

如果可以忽略类型参数的第二次出现，并让编译器将其计算出来（“构造函数类型推断”），那就太好了。这将从声明中去除冗余，大大提高可读性和易用性【据说是Java 7中新加的特性】：
Map<String, String> smsParamsMap = new HashMap<>();

当然，也可以用google的工具包guava里面的工具类 Maps
Map<String, String> smsParamsMap = Maps.newHashMap();
同理ArrayList的新建也可以这样使用，可以看一下guava的API文档

## 4、variable 'xxx' initializer '""' is redundant.


这个地方打概是说这个String我给它初始化为空串  '' ，或者null，有点多余
这个String errMsg = ""; //声明了一个变量
errMsg = result.get("errMsg"); //后面的代码里面有明确的赋值语句，所以初始的时候赋值的那个空串就有点多余了。
关于为null，这个确实是多余了，因为不赋值也是null。

## 5、unused import statement【ctrl+shift+o, organize imports】


养成习惯，清理不用的包引用。

#  6、Can be replaced with collect call less... 
This inspection reports foreach loops which can be replaced with stream api calls.
Stream api is not available under Java 1.7 or earlier JVMs

【这个地方建议我用stream api替代foreach，可能是写法更加简洁。个人觉得lambda表达式只是书写上面比较简洁，但是理解上面可能不是很方便，而且对于性能没有丝毫提高。语法糖，就是将书写简化，但是JVM执行的时候还是将其转化为for循环】

## 7、Method 'completeTask' is too complex to analyze by data flow algorithm less
This inspection analyzes method control and data flow to report possible conditions that are always true or false, expressions whose value is statically proven to be constant, and situations that can lead to nullability contract violations.
Variables, method parameters and return values marked as @Nullable or @NotNull are treated as nullable (or not-null, respectively) and used during the analysis to check nullability contracts, e.g. report NullPointerException (NPE) errors that might be produced.
More complex contracts can be defined using @Contract annotation, for example:
@Contract("_, null -> null") — method returns null if its second argument is null
@Contract("_, null -> null; _, !null -> !null") — method returns null if its second argument is null and not-null otherwise
@Contract("true -> fail") — a typical assertFalse method which throws an exception if true is passed to it
The inspection can be configured to use custom @Nullable
@NotNull annotations (by default the ones from annotations.jar will be used)【weak warnings】

上面的代码就是idea给出的弱警告的地方，由于所有的审批通过都是调用这个地方，导致条件判断极多，后面优化可以将一些条件判断放到service中做，当然也可以将一些需要特殊处理判断的业务从这段代码中分出去，走新的方法，这样不至于所有的点通过的操作都非常慢，特别是有些地方需要批量的通过，造成使用体验不是很好。

【代码的圈复杂度有点高？ 反正idea这个地方建议我用 @Nullable or @NotNull做一些值为空的条件判断，减少代码的复杂性】