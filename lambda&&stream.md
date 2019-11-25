## Lambda表达式

### 一、Lambda表达式简介

**什么是lambda表达式？**

lambda就是一个匿名函数

**为什么要使用lambda表达式？**

lambda表达式可以对一个接口进行非常简洁的实现

**Lambda对接口的要求？**

虽然可以使用Lambda表达式对某些接口进行简单的实现，但并不是所有的接口都可以用Lambda表达式来实现，要求接口中定义的必须要实现的抽象方法只能是一个

**@FunctionalInterface**

修饰函数式接口的，接口中的抽象方法只有一个