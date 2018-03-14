# 设计模式

##  组合模式

### 1. 定义

> 将对象组合成树形结构以表示‘部分-整体’的层次结构。组合模式使得用户对单个对象和组合对象的使用具有一致性

### 2. 结构图

![组合模式](./组合模式.png)

### 3. 使用的场合

- 需求中体现了部分与整体的层次结构
- 希望用户可以忽略组合对象和单个对象的不同，统一地使用组合结构中的所有对象

### 4. 优点

- 组合模式可以让用户一致地使用组合结构和单个对象

## 迭代器模式

### 1. 定义

> 提供一种方法顺序访问一个聚合对象的各个元素，而又不暴露该对象的内部表示

### 2. 结构图

![迭代器模式](./迭代器模式.png)

### 3. 使用的场合

- 一个聚集对象，不管对象是什么都需要遍历时，应该考虑使用迭代器模式
- 需要对聚集对象有多种方式遍历时

### 4. 优点

- 分离了集合对象的遍历行为，抽象出一个迭代器类来负责，这样既可以不暴露集合的内部结构，又让外部代码透明地访问集合内部数据。

## 单例模式

### 1. 定义

> 保证一个类仅有一个实例，并提供一个访问它的全局访问点
>
> 通常我们可以声明一个全局变量使得一个对象被访问，但不能阻止你实例化多个对象，最好的方法是，让类本身负责保存它的唯一实例，这个类可以保证没有其他实例可以被创建，而且他可以提供一个访问该实例的方法。

### 2. 结构图

![单例模式](./单例模式.png)

### 3. 优点

- 保证类只有唯一的实例
- 因为只有一个实例，所以可以控制用户怎样访问以及何时访问它

### 4. 多线程时的单例

- 使用锁来处理

  ```java
  class Singleton{
    public  static Singleton singleton;
    private static final Object object=new Object();
    private Singleton(){}
    public static Singleton getInstance(){
        if(singleton==null){
            synchronized(object){
                if(singleton==null){
                    singleton=new Singleton();
                }
            }
        }
      return singleton;
    } 
  }
  ```

### 5. 懒汉式加载和饿汉式加载

- 懒汉式单例：在第一次被引用时才会实例化，会有多线程访问的安全问题

  ```java
  class Singleton{
    public static Singleton singleton;
    private Singleton(){}
    public static Singleton getInstance(){
        if(singleton==null){
            singleton=new Singleton();
        }
      return singleton;
    }
  }
  ```

- 饿汉式单例：在类被加载时就将自己实例化,会提前占用系统资源

  ```java
  class Singleton{
    public static final Singleton singleton=new Singleton();
    private Singleton(){}
    public static Singleton getInstance(){
        return singleton;
    }
  }
  ```

## 桥接模式

### 1. 定义

>将抽象部分与它的实现部分分离，使它们都可以独立地变化。
>
>实现系统可能有多角度分类，每一种分类都有可能变化，那么就把多角度分离出来让它们独立变化，减少它们之间的耦合

### 2. 结构图

![桥接模式](./桥接模式.png)

### 3. 使用的场合

- 当需要从多角度去分类实现对象，而继承会造成大量的类增加，不能满足开放-封闭原则时，考虑使用桥接模式

### 4. 优点

- 减少类之间的耦合

## 

# 面向对象设计原则

## 1. 组合/聚合复用原则

> 尽量使用组合/聚合，尽量不要使用类继承

- 聚合：表示一种弱的“拥有“关系，体现的是A对象可以包含B对象，但B对象不是A对象的一部分；
- 组合：表示一种强的”拥有“关系，体现了严格的部分和整体的关系，部分和整体的生命周期一致。