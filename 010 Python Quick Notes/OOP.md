## Class and Objects
Each object have some specific attributes (features) of their own, but they can belong to the same class. and it's not good the initialize different attributes of each objects separately, so we define a *Constructor* at the first thing in our class.
### Constructor
`__init__` to initialize the attributes of the object. Whenever an instance will be created we can give them the instance value at the beginning in itself via parameter.
```Python
def __init__(self, name, age):
	self.name = name
	self.age = age

self.age this part is the instance variable, and name, age is the parameters value will be given while creating the isntance.
```
Using the self, we define the *Instance variable and Methods*
## Four Pillars of OOP
#### 1. Inheritance
Inheriting the parent class properties inside the child class. we call the `super().__init__` method when we have one parent class. For having multiple parent class, we use the `ClassName.__initt__(self, att)`
#### 2. Encapsulation

#### 3. Polymorphism

#### 4. Abstraction


