---
title: lombok是什么
date: 2018-08-14 15:02:15
tags:
    - lombok
    - Java
categories: Java
---
### 简介

Project Lombok is a java library that automatically plugs into your editor and build tools, spicing up your java.
Never write another getter or equals method again. Early access to future java features such as val, and much more.

Lombok是一个可以通过简单的注解形式来帮助我们简化消除一些必须有但显得很臃肿的Java代码的工具，通过使用对应的注解，可以在编译源码的时候生成对应的方法。
### 为什么使用lombok
我们在开发过程中，通常都会定义大量的JavaBean，然后通过IDE去生成其属性的构造器、getter、setter、equals、hashcode、toString方法，当要增加属性或者对某个属性进行改变时，比如命名、类型等，都需要重新去生成上面提到的这些方法。这样重复的劳动没有任何意义，Lombok里面的注解可以轻松解决这些问题。
### features
* val: final 像动态语言一样，声明一个fianl的变量。
* var: 同JDK10
* @Data：注解在类上，将类提供的所有属性都添加get、set方法，并添加、equals、canEquals、hashCode、toString方法
* @Setter：注解在类上，为所有属性添加set方法、注解在属性上为该属性提供set方法
* @Getter：注解在类上，为所有的属性添加get方法、注解在属性上为该属性提供get方法
* @NotNull：在参数中使用时，如果调用时传了null值，就会抛出空指针异常
* @Synchronized 用于方法，可以锁定指定的对象，如果不指定，则默认创建一个对象锁定
* @Log作用于类，创建一个log属性
* @Builder：使用builder模式创建对象
* @NoArgsConstructor：创建一个无参构造函数
* @AllArgsConstructor：创建一个全参构造函数
* @ToString：创建一个toString方法
* @Accessors(chain = true)使用链式设置属性，set方法返回的是this对象。
* @RequiredArgsConstructor：创建对象, 例: 在class上添加@RequiredArgsConstructor(staticName = "of")会创建生成一个静态方法
* @UtilityClass:工具类
* @ExtensionMethod:设置父类
* @FieldDefaults：设置属性的使用范围，如private、public等，也可以设置属性是否被final修饰。
* @Cleanup: 关闭流、连接点。
* @EqualsAndHashCode：重写equals和hashcode方法。
* @toString：创建toString方法。
### 示例
```java
@Setter
@Getter
@Accessors(chain = true)
public class User {
    private String id;
    private String name;
    private Integer age;
}

public static void main(String[] args) {
    //使用@Accessors(chain = true)
    User userChain = new User();
    userChain.setId("1").setName("chain").setAge(1);
}
```

参考资料
* [官网](https://projectlombok.org/)
* [features](https://projectlombok.org/features/all)
* [lombok @Data](https://projectlombok.org/features/Data)
* [github](https://github.com/rzwitserloot/lombok)

