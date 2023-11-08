# Object Oriented Concepts

Documentation on miscellaneous concepts in Object Oriented programming
With particular reference to Python constructs

## Class vs Static methods and variables

For what is a static variable, see [static variables](./programming_concepts.md#static)

In Python, a static variable is a variale shared among all instances of a class, rather than being unique to each instance, sometimes referred to as a class variable because it belongs to the class itself rather than any particular instance of the class.

  * allocated memory once only when the first object for the class is created
  * created outside of methods but inside the class
  * accessed through a class but not directly with an instance?

*Example*

```
class CSStudent:

    stream='cse'
    def __init(self,name,roll):
        self.name=name
        self.roll=roll

a=CSStudent('Geek',1)
b=CSStudent('Nerd',2)

print(a.stream)
a.stream='ece'
print(a.stream)
# BUT
print(CSStudent.stream)
# However 
CSSTudent.stream='mech'
print(a.stream)
print(b.stream)
```

outputs

```
cse
ece
cse
mech
mech
```


For a good reference about the distinction between static and class methods see
[here](https://sparkbyexamples.com/python/python-difference-between-staticmethod-and-classmethod/)

### static methods
A staticmethod in Python is a special type of method that's 

  * defined inside a class
  
  * related to the class

  * does **NOT** have access to any instance or class data

So such a method is not bound to any specific instance of the class and can be called on the class itself without the need of an instance.
It's used to define a utility function that is related to the class but doesn't require access to any instance or class data.

For static method the syntax is
```
class C:
    @staticmethod
    def f(arg1, arg2, ...): ...
```
I.e. use the staticmethod decorator

### class methods
A `classmethod` is a type of method that is defined inside a class and is related to the class as a whole rather than a specific instance.

similar to a staticmethod, but it can access and modify the class itself.
It takes the class otself as its first argument.

*Example*

```
class MyClass:
    counter=0

    def __init__(self, name):
        self.name=name
        MyClass.counter += 1

    @classmethod
    def display_count(cls):
        print("The count is :", cls.counter)

obj1 = MyClass('Al')
obj2 = MyClass('Bob')

MyClass.display_count() # output is 2
```

### Mixin
Refernce can be found [here](https://www.pythontutorial.net/python-oop/python-mixin/)
See also [here](https://dev.to/bikramjeetsingh/write-composable-reusable-python-classes-using-mixins-6lj)
A `mixin` is a `class` that provides method implementations for reuse by multiple related child classes. But the inheritance is not implying an 'is-a' relationship.


Doesn't define a new type, therefore **not** intended for instantiation

Basically a mixin bundles a set of methods for reuse.
Each mixin should have a single specific behaviour, implementing closely relatd methods.

Typically a child class uses multiple inheritance to combine the mixin classes with a parent class

Good practive to define mixin classes with suffix 'Mixin'

*Example*
First define a person class

```
class Person:
    def __init__(self,name):
        self.name=name
```

Second define an Employee class that inherits from the Person class
```
class Employee(Person):
    def __init__(self,name, skills, depdendents):
        super().__init__(name)
        self.skills=skills
        self.dependents=dependents
```
Third create a new instance of Employee class

```
if __name__ == '__main__':
    e = Employee(
        name='John',
        skills=['Python Programming''Project
Management'],
        depdendents={'wife':'Jane', 'children':['Alice','Bob']}
    )
```

Let's suppose you want to convert the Employee object to a dictionary


Todo that, you can add a new method to the Employee class - maybe a class method.
But suppose you want to convert other objects of other classes to dictionaries. To make the code reusable, you can define a mixin class, let's call it `DictMixin`

```
class DictMixin:
    def to_dict(self):
        return self._traverse_dict(self.__dict__)

    def _traverse_dict(self, attributes: dict) -> dict:
        result={}
        for key, value in attributes.items():
            result[key]=self._traverse(key,vale)
        return result
    def _traverse(self, key, value):
        if isinstance(value, DictMixin):
            return value.to_dict()
        elif isinstance(value,dict):
            return self._traverse_dict(value)
        elif isinstance(value, list):
            return [self._traverse(key,v) for v in value]
        elif hasattr(value, '__dict__'):
            return self._traverse_dict(value.__dict__)
        else:
            return value

```

We can now change the `Employee` class so that it inherits the `DictMixin` class

```
class Employee(DictMixin, Person):
    def __init__(self,name, skills, depdendents):
        super().__init__(name)
        self.skills=skills
        self.dependents=dependents
```

## Notes
