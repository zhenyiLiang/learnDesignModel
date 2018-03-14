# 设计模式

## 19. 组合模式

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