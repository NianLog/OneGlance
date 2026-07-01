# 设计模式

## 目录

1. [设计模式概述](#设计模式概述)
2. [创建型模式](#创建型模式)
3. [结构型模式](#结构型模式)
4. [行为型模式](#行为型模式)

## 设计模式概述

### 设计模式是什么

设计模式是软件设计中常见问题的通用解决方案。它们是经过验证的、可复用的设计经验。

### 设计原则

| 原则 | 说明 |
|------|------|
| 开闭原则 | 对扩展开放，对修改关闭 |
| 里氏代换原则 | 子类可以替换父类 |
| 依赖倒转原则 | 面向接口编程，不要面向实现编程 |
| 接口隔离原则 | 使用多个专用接口，不要使用单一的总接口 |
| 迪米特法则 | 最少知识原则，一个对象应该对其他对象有最少的了解 |

## 创建型模式

### 单例模式（Singleton）

确保一个类只有一个实例，并提供一个全局访问点。

```python
class Singleton:
    _instance = None
    
    def __new__(cls):
        if cls._instance is None:
            cls._instance = super().__new__(cls)
        return cls._instance

# 使用
s1 = Singleton()
s2 = Singleton()
print(s1 is s2)  # True
```

### 工厂模式（Factory）

定义一个创建对象的接口，让子类决定实例化哪个类。

```python
# 简单工厂
class Factory:
    @staticmethod
    def create_product(type):
        if type == 'A':
            return ProductA()
        elif type == 'B':
            return ProductB()

# 工厂方法
class AbstractFactory:
    def create_product(self):
        pass

class FactoryA(AbstractFactory):
    def create_product(self):
        return ProductA()
```

### 建造者模式（Builder）

将一个复杂对象的构建与它的表示分离。

```python
class Builder:
    def __init__(self):
        self.product = Product()
    
    def build_part_a(self):
        self.product.add_part('A')
        return self
    
    def build_part_b(self):
        self.product.add_part('B')
        return self
    
    def get_result(self):
        return self.product
```

## 结构型模式

### 适配器模式（Adapter）

将一个类的接口转换成客户希望的另一个接口。

```python
# 类适配器
class Adapter(Target, Adaptee):
    def request(self):
        return self.specific_request()

# 对象适配器
class Adapter(Target):
    def __init__(self):
        self.adaptee = Adaptee()
    
    def request(self):
        return self.adaptee.specific_request()
```

### 装饰器模式（Decorator）

动态地给对象添加一些额外的职责。

```python
class Component:
    def operation(self):
        pass

class ConcreteComponent(Component):
    def operation(self):
        return "具体操作"

class Decorator(Component):
    def __init__(self, component):
        self.component = component
    
    def operation(self):
        return self.component.operation()

class ConcreteDecorator(Decorator):
    def operation(self):
        return f"装饰({super().operation()})"
```

### 代理模式（Proxy）

为其他对象提供一种代理以控制对这个对象的访问。

```python
class RealSubject:
    def request(self):
        return "真实请求"

class Proxy:
    def __init__(self):
        self.real = RealSubject()
    
    def request(self):
        # 可以在调用真实对象前后做一些处理
        print("代理：准备请求")
        result = self.real.request()
        print("代理：请求完成")
        return result
```

## 行为型模式

### 观察者模式（Observer）

定义对象间的一种一对多的依赖关系。

```python
class Observer:
    def update(self, message):
        pass

class Subject:
    def __init__(self):
        self.observers = []
    
    def attach(self, observer):
        self.observers.append(observer)
    
    def detach(self, observer):
        self.observers.remove(observer)
    
    def notify(self, message):
        for observer in self.observers:
            observer.update(message)
```

### 策略模式（Strategy）

定义一系列算法，把它们一个个封装起来，并使它们可相互替换。

```python
class Strategy:
    def execute(self, data):
        pass

class StrategyA(Strategy):
    def execute(self, data):
        return f"策略A处理{data}"

class StrategyB(Strategy):
    def execute(self, data):
        return f"策略B处理{data}"

class Context:
    def __init__(self, strategy):
        self.strategy = strategy
    
    def set_strategy(self, strategy):
        self.strategy = strategy
    
    def execute_strategy(self, data):
        return self.strategy.execute(data)
```

### 模板方法模式（Template Method）

定义一个操作中的算法骨架，而将一些步骤延迟到子类中。

```python
class AbstractClass:
    def template_method(self):
        self.step1()
        self.step2()
        self.hook()
    
    def step1(self):
        pass
    
    def step2(self):
        pass
    
    def hook(self):  # 钩子方法，子类可选重写
        pass

class ConcreteClass(AbstractClass):
    def step1(self):
        print("步骤1实现")
    
    def step2(self):
        print("步骤2实现")
```
