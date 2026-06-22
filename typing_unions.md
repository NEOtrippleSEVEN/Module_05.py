# Abstract Methods 

## ABC - Abstract Base Class 

*Definition:* 

> An Abstract Base Class (ABC) defines methods that must be implemented by it's subclasses, ensuring that the subclasses follow a consistent structure. ABC's allow you to define common interfaces that various subclasses can implement while enforcing a level of abstraction. 

> ABC's are marked as abstract rather than making it fully concrete. `@abstractmethod` is used here to define a common interface that all concrete subclasses must implement. 

![alt text](1_k4cQvaJWa80QeCRR45UBgg.webp)

### < Characteristics of an ABC >

1. You cannot create an object directly from an abstract class. It is considered incomplete until the missing parts are fleshed out by subclass. 

2. It can contain asbtract methods (@abstractmethod), which are declared with a name and parameters but have no body or implementations. 

3. It can create a mandatory "Check-List" for it's subclasses. If even one item is missing the program throws an error.

### < Use Case >

1. *Consistent Interface:* IT ensures that a group fo related classes all share the same method signatures, making them interchangeable. 

2. *Preventing INcomplete Code:* Acts as a safety net, preventing of creating subclasses that are missing critical functionalities. 

3. *Code Resusability:* Centralizes shared logic adn variables in one place, preventing code dups. 

### Example 

```py
from abc import ABC, abstractmethod
class Animal(ABC):
	@abstractmethod
	def sounf(self):
		pass

class Dog(Animal):
	def sound(self):
		return "Bark"

dog - Dog()
print(dog.sound())
```
## Abstract Methods

*Defintion:*

> Abstract methods are methods that are defined in an abstract class but don't have an implementation. 

### Example 
```py
from abc import ABC, abstractmethod
class Animal(ABC):
	@abstractmethod
	def make_sound(self):
		pass
# animal = Animal() # Raises: TypeError
```
> `make_sound` is an abstract method in the Animal class, so it doesn't have any code inside it. If you try to initiate Animal Directly, Python will raise a TypeError since the method is not implemented. 

## Concrete Methods 	

*Defintion:* 
> Are methods that have full implementations in an abstract class. These methods can be inherited by subclasses and used directly without needing to be redefined. 

### Example
```py
class Dog(Animal):
	def make_sound(self):
		return "Bark"
dog = Dog()
print(dog.move()) # Use Concrete Method from "Animal"
print(dog.make_sound())
```
- `Dog` inherits the concrete method `move()` from `Animal` without redefining it while also implementing it required abstract method `make_soud`. 

## Abstract Properties 

*Definition:*
> Abstract Properties work like abstract methods but are used for properties. These properties are declared with `@properties` decorator and marked as abstract using `@abstractmethod`. 

Abstract propertoes enfore that a subclass provides the property's implementation. They are especially usefful when you want all subclasses to have a certain attribute (Like species, categories or type).

### Example 
```py
from abc import ABC, abstractmethod
class Animal(ABC):
	@property
	@abstractmethod
	def species(self):
		pass
class Dog(Animal):
	@property
	def species(self):
		return "Canine"

# Instantiate the concrete subclass
dog = Dog()
print(dog.species)
```
Explanation: 
- Species is an abstract property in the Animal class and it is marked as `@abstractmethod`. 

- The Dog class implements the species property, making it a concrete subclass that can be instantiated (Represent an asbstraction, theory or concept)

- Abstract properties enforce that a subclass provides the property's implementation. 


## Abstract Class Instantiation

*Definition:*
> Abstract classes cannot be instantiated directly. This is because they contain one or more abstract methods or properties that lack implementations. Attempting to instantiate an asbtract class will result in a `TypeError`. 

### Example
```py
# This example shows the error raised when trying to instantiate an abstract class. 

from abc import ABC, abstractmethod
class Animal(ABC):
	@abstractmethod
	def make_sound(self):
		pass

# animal = Animal()
# TypeError: can't instantiate abstract class Animal with abstract methods make_sound
```
Explanation
- The `Animal` class is abstract because it has the abstract method `make_sound()`

- Trying to create `animal = Animal()` directly raises a `TypeError`.

- Only concrete subclasses that implement all abstract methods (like Dog) can be instantiated. 


>> NOTE >>  If a subclass doens't implement all abstract methods or properties from it's parent, it also remains abstract and cannot be instantiated. 

>----

## Questions ? 

> What is the purpose of the `@property` decorator in Python?

<To create read-only properties

> How can you create an abstract class in python using the abc module?

A. By using the abstract Keyword

B. By defining methods with the @abstractmethod decorator <Answer>

C. By using the abstract attribute in the class definition 

D. By creating a class with no concrete methods 

> What is an abstract class? 

A.  A class that provides a complete implementations of all it's methods

B. A class that cannot be instantiated and usually contains one or more abstract methods <Answer>

C. A class that contains only instance attributes

D. A class with only private attributes. 
