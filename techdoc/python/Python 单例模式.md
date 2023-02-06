# Python 单例模式

[toc]

类别：属于创建型模式
目的：保证一个类仅有一个实例，并提供一个访问它的全局访问点

**benefit**

- To limit concurrent access to a shared resource.
- To create a global point of access for a resource.
- To create just one instance of a class, throughout the lifetime of a program.

## Python 单例模式的实现

**单例模式的三种实现方式**

- Module-level Singleton
- Classic Singleton
- Borg Singleton

### **Module-level Singleton**

通过模块文件的方式实现，一个模块本身就是一个单例

### **Classic Singleton**

Classic Singleton creates an instance only if there is no instance created so far; otherwise, it will return the instance that is already created

```python
class SingletonClass(object):
    def __new__(cls):
        if not hasattr(cls, "instance"):
            cls.instance = super(SingletonClass, cls).__new__(cls)
        return cls.instance
    
singleton = SingletonClass()
new_singleton = SingletonClass()

print(singleton is new_singleton)
print(id(singleton))
print(id(new_singleton))
```

### **Borg Singleton**

> Borg singleton is a design pattern in Python that allows state sharing for different instances.

在不同的实例中共享状态

```python
class BorgSingleton(object):
    _share_borg_stage = {}

    def __new__(cls, *args, **kwargs):
        obj = super(BorgSingleton,cls).__new__(cls, *args, **kwargs)
        obj.__dict__ = cls._share_borg_stage
        return obj
    
borg = BorgSingleton()
borg.shared_variable = "Shared Variable"

class ChildBorg(BorgSingleton):
    pass

childBorg = ChildBorg()
print(childBorg is borg)
print(childBorg.shared_variable)
```

## 单例模式的应用

Let’s list a few of the use cases of a singleton class. They are as follows:

- Managing a database connection
- Global point access to writing log messages
- File Manager
- Print spooler









