# Python Class Types: Detailed Notes with Practical Examples

## 1. Introduction

Python is an object-oriented language, but it also supports multiple programming styles including procedural and functional programming. A class is a blueprint for creating objects. An object is an instance of a class.

Classes are used to:
- model real-world entities
- organize code into reusable structures
- encapsulate data and behavior
- support inheritance and polymorphism
- apply abstraction to complex systems

---

## 2. Core Class Types in Python

Python supports several different kinds of classes and class-related constructs.

### 2.1 Built-in Types (Predefined Data Types)
These are not user-defined classes, but they are types in Python:

- int
- float
- complex
- bool
- str
- list
- tuple
- set
- frozenset
- dict
- bytes
- bytearray
- range
- NoneType

Example:

```python
x = 10          # int
pi = 3.14       # float
z = 2 + 3j      # complex
flag = True     # bool
name = "Alice"  # str
nums = [1, 2, 3]  # list
coords = (10, 20)  # tuple
items = {1, 2, 3}  # set
d = {"name": "Alice", "age": 25}  # dict
b = b"hello"    # bytes
```

### 2.2 User-Defined Classes
A user-defined class is created with the `class` keyword.

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def greet(self):
        return f"Hello, my name is {self.name}"
```

### 2.3 Instance Types
An instance is an object created from a class.

```python
p1 = Person("Alice", 25)
print(p1.greet())
```

### 2.4 Abstract Classes
Abstract classes define common behavior without implementing every method.

```python
from abc import ABC, abstractmethod

class Animal(ABC):
    @abstractmethod
    def sound(self):
        pass
```

### 2.5 Concrete Classes
Concrete classes implement the abstract methods and can be instantiated.

```python
class Dog(Animal):
    def sound(self):
        return "Bark"

print(Dog().sound())
```

### 2.6 Static Classes
Python does not have a true static class in the same way as Java, but you can use a class with only static methods.

```python
class MathHelper:
    @staticmethod
    def add(a, b):
        return a + b

print(MathHelper.add(3, 5))
```

### 2.7 Data Classes
Data classes are used to simplify class definition for storing data.

```python
from dataclasses import dataclass

@dataclass
class Student:
    name: str
    age: int
    grade: str

s = Student("Jane", 18, "A")
print(s)
```

### 2.8 Namedtuple and Typed Structures
These provide lightweight structures with named attributes.

```python
from collections import namedtuple

Point = namedtuple("Point", ["x", "y"])
p = Point(3, 4)
print(p.x, p.y)
```

---

## 3. Class Features in Python

### 3.1 Attributes
Attributes are variables attached to objects.

```python
class Car:
    def __init__(self, model, color):
        self.model = model
        self.color = color

c = Car("Toyota", "Red")
print(c.model)
```

### 3.2 Methods
Methods are functions defined inside classes.

```python
class Circle:
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return 3.14 * self.radius ** 2
```

### 3.3 Constructors (`__init__`)
The constructor initializes the object.

```python
class Employee:
    def __init__(self, name, salary):
        self.name = name
        self.salary = salary
```

### 3.4 `self`
`self` refers to the current instance of the class.

```python
class Book:
    def __init__(self, title):
        self.title = title

    def show(self):
        print(self.title)
```

### 3.5 Class Attributes vs Instance Attributes

```python
class Counter:
    total = 0  # class attribute

    def __init__(self):
        self.count = 1  # instance attribute
```

---

## 4. Class Types and Programming Concepts

### 4.1 Simple Classes
These are basic classes with attributes and methods.

```python
class Laptop:
    def __init__(self, brand, ram):
        self.brand = brand
        self.ram = ram

    def info(self):
        return f"Laptop: {self.brand}, RAM: {self.ram}GB"
```

### 4.2 Inheritance
A child class inherits properties from a parent class.

```python
class Animal:
    def speak(self):
        return "Animal sound"

class Dog(Animal):
    def speak(self):
        return "Woof"

print(Dog().speak())
```

### 4.3 Multiple Inheritance
A class can inherit from more than one base class.

```python
class A:
    def method_a(self):
        return "A"

class B:
    def method_b(self):
        return "B"

class C(A, B):
    pass

obj = C()
print(obj.method_a(), obj.method_b())
```

### 4.4 Encapsulation
Encapsulation restricts direct access to internal data.

```python
class BankAccount:
    def __init__(self, balance):
        self.__balance = balance

    def deposit(self, amount):
        self.__balance += amount

    def get_balance(self):
        return self.__balance
```

### 4.5 Polymorphism
Different classes can implement the same method name differently.

```python
class Cat:
    def sound(self):
        return "Meow"

class Cow:
    def sound(self):
        return "Moo"

for animal in [Cat(), Cow()]:
    print(animal.sound())
```

### 4.6 Abstraction
Abstraction hides complexity and shows essential behavior.

```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass
```

### 4.7 Composition
Instead of inheritance, one class contains other classes.

```python
class Engine:
    def __init__(self):
        self.power = 200

class Car:
    def __init__(self):
        self.engine = Engine()

c = Car()
print(c.engine.power)
```

---

## 5. Special Class Methods in Python

### 5.1 `__str__`
Returns user-friendly string representation.

```python
class Product:
    def __init__(self, name):
        self.name = name

    def __str__(self):
        return f"Product({self.name})"

print(Product("Laptop"))
```

### 5.2 `__repr__`
Returns developer-friendly representation.

```python
class Product:
    def __init__(self, name):
        self.name = name

    def __repr__(self):
        return f"Product(name={self.name!r})"

print(repr(Product("Laptop")))
```

### 5.3 `__len__`
Allows use of `len(obj)`.

```python
class Queue:
    def __init__(self, items):
        self.items = items

    def __len__(self):
        return len(self.items)

q = Queue([1, 2, 3])
print(len(q))
```

### 5.4 `__eq__`
Defines equality comparison.

```python
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __eq__(self, other):
        return self.x == other.x and self.y == other.y

p1 = Point(1, 2)
p2 = Point(1, 2)
print(p1 == p2)
```

### 5.5 `__add__`
Defines addition behavior for objects.

```python
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __add__(self, other):
        return Vector(self.x + other.x, self.y + other.y)
```

---

## 6. Class Decorators and Advanced Features

### 6.1 Class Methods
A class method receives the class instead of the instance.

```python
class Employee:
    company = "ABC Ltd"

    @classmethod
    def info(cls):
        return cls.company

print(Employee.info())
```

### 6.2 Static Methods
Static methods do not access self or cls.

```python
class Utility:
    @staticmethod
    def square(n):
        return n * n

print(Utility.square(5))
```

### 6.3 Property Decorator
Used to create getter and setter logic.

```python
class Person:
    def __init__(self, age):
        self._age = age

    @property
    def age(self):
        return self._age

    @age.setter
    def age(self, value):
        if value < 0:
            raise ValueError("Age cannot be negative")
        self._age = value
```

### 6.4 Descriptors
Descriptors control attribute access.

```python
class IntegerField:
    def __get__(self, obj, objtype=None):
        return obj._value

    def __set__(self, obj, value):
        if not isinstance(value, int):
            raise TypeError("Must be an integer")
        obj._value = value

class Record:
    age = IntegerField()
```

---

## 7. Python Built-in Class Patterns

### 7.1 Numbers
- int
- float
- complex

```python
num1 = 10
num2 = 12.5
num3 = 3 + 2j
print(type(num1), type(num2), type(num3))
```

### 7.2 Strings
Strings are immutable sequences of characters.

```python
name = "python"
print(name.upper())
print(name[0])
```

### 7.3 Lists
Lists are mutable and ordered.

```python
items = [1, 2, 3]
items.append(4)
print(items)
```

### 7.4 Tuples
Tuples are immutable sequences.

```python
point = (4, 5)
print(point[0])
```

### 7.5 Sets
Sets contain unique elements.

```python
s = {1, 2, 2, 3}
print(s)
```

### 7.6 Dictionaries
Dictionaries store key-value pairs.

```python
student = {"name": "Alice", "age": 20}
print(student["name"])
```

### 7.7 Bytes and Bytearray
Used for binary data.

```python
b = b"ABC"
print(b)
print(list(b))
```

---

## 8. Practical Applications of Classes

### 8.1 Banking System

```python
class Account:
    def __init__(self, owner, balance=0):
        self.owner = owner
        self.balance = balance

    def deposit(self, amount):
        self.balance += amount

    def withdraw(self, amount):
        if amount > self.balance:
            raise ValueError("Insufficient balance")
        self.balance -= amount

    def show(self):
        return f"{self.owner} has {self.balance}"

acct = Account("Alice", 1000)
acct.deposit(500)
print(acct.show())
```

### 8.2 Student Record Management

```python
class Student:
    def __init__(self, name, marks):
        self.name = name
        self.marks = marks

    def average(self):
        return sum(self.marks)/len(self.marks)

s = Student("Bob", [70, 80, 90])
print(s.average())
```

### 8.3 Library System

```python
class Book:
    def __init__(self, title, author):
        self.title = title
        self.author = author

    def info(self):
        return f"{self.title} by {self.author}"

book = Book("Python Programming", "John Doe")
print(book.info())
```

### 8.4 E-Commerce Product Catalog

```python
class Product:
    def __init__(self, name, price):
        self.name = name
        self.price = price

    def discount(self, percent):
        return self.price * (1 - percent / 100)

p = Product("Laptop", 800)
print(p.discount(10))
```

### 8.5 Vehicle and Inheritance Example

```python
class Vehicle:
    def __init__(self, name):
        self.name = name

    def move(self):
        return f"{self.name} is moving"

class Car(Vehicle):
    def honk(self):
        return "Beep beep"

car = Car("Toyota")
print(car.move())
print(car.honk())
```

---

## 9. Best Practices for Classes in Python

- Use meaningful class names
- Keep methods focused and short
- Keep data encapsulated when needed
- Prefer composition over deep inheritance where appropriate
- Use dataclasses for simple data containers
- Use type hints for clarity
- Avoid over-engineering simple tasks

Example with type hints:

```python
from dataclasses import dataclass

@dataclass
class User:
    id: int
    username: str
    email: str
```

---

## 10. Summary

Python class types range from built-in primitive data types to complex user-defined models. The heart of Python object-oriented programming is the class, which groups state and behavior into reusable modules. Understanding the differences between built-in types, custom classes, abstract classes, inheritance, polymorphism, and data classes is essential for building maintainable, reusable, and professional Python applications.

Python classes are used in:
- web development
- data modeling
- game development
- automation
- APIs and backend systems
- machine learning pipelines
- scientific computing

---

## 11. Quick Reference

```python
# Basic class
class Example:
    def __init__(self, value):
        self.value = value

    def show(self):
        print(self.value)

# Inheritance
class Child(Example):
    pass

# Static method
class Helper:
    @staticmethod
    def add(a, b):
        return a + b

# Class method
class Demo:
    count = 0

    @classmethod
    def inc(cls):
        cls.count += 1
```

This document is designed to be copied into Word or Google Docs and exported as a PDF.
