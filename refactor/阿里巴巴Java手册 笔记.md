>前一阵子，阿里巴巴出了一个java手册，作为行业标准的参考，学习一下。

## 命名规范
* 1、类名一律使用UpperCamelCase， 方法名、变量名、参数名一律使用LowerCamelCase

* 2、常量使用全部大写，下划线隔开    e.g. MAX_COUNT

* 3、抽象类使用Abstract或者Base开头。异常使用Exception结尾，测试类以Test结尾

* 4、POJO中的类名不要以is 开头，否则框架会引起序列化错误。

* 5、如果使用了设计模式，建议在类名中体现具体的设计模式。 e.g. OrderFactory、LoginProxy

* 6、枚举类型建议加上Enum后缀，枚举成员全部大写。  e.g. DealStatusEnum 【SUCCESS， FAILED, UNKNOW_REASON】

* 7、各层命名规范：
   *  A)Service、DAO命名规范：
       * 1）获取单个对象用get前缀
       * 2）获取多个对象，使用list前缀
       * 3）统计值的方法使用count做前缀
       * 4）插入方法，前缀：save， insert
       * 5）删除的方法的前缀：remove， delete
       * 6）修改的方法使用update前缀
   *  B）领域模型命名：
       * 1）数据对象： xxxDO 【对应数据库】
       * 2）数据传输对象xxxDTO 【业务领域相关】
       * 3）展示对象xxxVO
       * 4）POJO，是DO/DTO/BO/VO的统称，禁止命名xxxPOJO

## 常量定义
* 1、long，Long初始化的时候以L结尾

* 2、如果变量值仅在一定范围内变化用enum。如果还带有名称之外的延伸属性，必须使用Enum，下面的数字就是延伸信息。   e.g.
             public enum{
                 MONDAY(1), TUESDAY(2), WEDNESDAY(3), TUESDAY(4), FRIDAY(5), SATURDAY(6), SUNNDAY(7);
            }

## 格式规范

* 1、使用tab键，禁止使用四个空格代替。

* 2、单行查过120字符需要换行
    1）第二行相对第一行缩进四个空格，第三行不用继续缩进
    2）运算符与下一行在一起
    3）方法调用的点与下一行一起
    4）多个参数超长，逗号后面换行

OOP规范

* 1、所有的覆写函数都要使用@Override关键字

* 2、对外暴露的接口原则上面不允许修改方法的参数签名，避免接口调整产生的影响。接口过时的时候需要使用@Deprecated注解，并清晰的说明该采用的新接口是什么。

* 3、不要使用过是的类或者方法。

* 4、所有的包装类的对象之间的值的比较都用equals。
    【对于Integer来说，在-128~127之间的赋值，Integer对象是在IntegerCache.cache产生，会复用已经有的对象，这个区间的对象使用 == 是可以的，范围之外的数值比较都会在堆上面新建对象必须使用equals进行比较】

* 5、关于基本数据类型和包装类数据类型的使用标准入下
        1）多有的POJO的属性都要使用包装类【？？？？ WHY】,没有初始值需要在使用之前显式的赋值
        2）所有局部变量推荐使用基本数据类型
   
* 6、定义POJO的时候不要设置任何默认值

* 7、序列化类新增属性的时候不要修改serialVersionUID字段，避免反序列化失败

* 8、构造函数里面不要有任何的业务逻辑，若有初始化的操作，请写在init()方法里面

* 9、循环体内字符串的拼接一定要使用StringBuilder.appen。 因为每一次循环都会产生一个StringBuilder对象，十分消耗资源。

## 集合处理[p9]

* 1、ArrayList的subList方法不可以强制转化成ArrayList，否则抛ClassCastException异常。
      因为subList返回的是ArrayList的内部类subList，他只是ArrayList的一个视图。



