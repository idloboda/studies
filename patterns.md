### **Design Patterns**

The **Design Patterns** are typical solutions to common problems in software design. They are like blueprints that you can customize to solve a particular design problem in your code. Below, we recap the most common design patterns with examples to help understand each one.

### 1. **Singleton Pattern**
   - **Definition**: The **Singleton Pattern** ensures that a class has **only one instance** and provides a global point of access to that instance.
   - **Use Case**: It's often used for managing resources like database connections or logging.
   - **Code Example**:
     ```python
     class Logger:
         _instance = None

         @classmethod
         def get_instance(cls):
             if cls._instance is None:
                 cls._instance = cls()  # Create an instance only if it doesn't exist
             return cls._instance
         
         def log(self, message):
             print(message)

     # Get the singleton instance of Logger
     logger1 = Logger.get_instance()
     logger2 = Logger.get_instance()

     # Verify Singleton behavior
     print(logger1 is logger2)  # Output: True, indicating both are the same instance
     ```

### 2. **Factory Pattern**
   - **Definition**: The **Factory Pattern** defines an interface for creating an object, but allows subclasses to alter the type of objects that will be created.
   - **Use Case**: Useful when the exact type of the object to be created is determined by the subclasses.
   - **Code Example**:
     ```python
     from abc import ABC, abstractmethod

     class Weapon(ABC):
         @abstractmethod
         def attack(self):
             pass

     class Sword(Weapon):
         def attack(self):
             print("Swinging the sword!")

     class Bow(Weapon):
         def attack(self):
             print("Shooting an arrow!")

     class WeaponFactory:
         @staticmethod
         def create_weapon(weapon_type):
             if weapon_type == "sword":
                 return Sword()
             elif weapon_type == "bow":
                 return Bow()
             else:
                 raise ValueError(f"Unknown weapon type: {weapon_type}")

     # Create and use weapons
     weapon1 = WeaponFactory.create_weapon("sword")
     weapon2 = WeaponFactory.create_weapon("bow")
     weapon1.attack()  # Output: Swinging the sword!
     weapon2.attack()  # Output: Shooting an arrow!
     ```

### 3. **Observer Pattern**
   - **Definition**: The **Observer Pattern** defines a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.
   - **Use Case**: Often used in event handling systems or the implementation of distributed event-driven systems.
   - **Code Example**:
     ```python
     class Observer:
         def update(self, message):
             pass

     class ConcreteObserver(Observer):
         def update(self, message):
             print(f"Observer received: {message}")

     class Subject:
         def __init__(self):
             self._observers = []
         
         def add_observer(self, observer):
             self._observers.append(observer)
         
         def notify_observers(self, message):
             for observer in self._observers:
                 observer.update(message)

     # Example usage
     subject = Subject()
     observer1 = ConcreteObserver()
     observer2 = ConcreteObserver()
     subject.add_observer(observer1)
     subject.add_observer(observer2)
     subject.notify_observers("Hello Observers!")
     # Output:
     # Observer received: Hello Observers!
     # Observer received: Hello Observers!
     ```

### 4. **Adapter Pattern**
   - **Definition**: The **Adapter Pattern** allows the interface of an existing class to be used as another interface. It acts as a bridge between two incompatible interfaces.
   - **Use Case**: Useful for making unrelated classes work together without modifying their code.
   - **Code Example**:
     ```python
     class EuropeanPlug:
         def plug_in(self):
             print("Plugging in using European plug.")

     class USPlug:
         def plug_in(self):
             print("Plugging in using US plug.")

     class Adapter:
         def __init__(self, european_plug):
             self.european_plug = european_plug
         
         def plug_in(self):
             self.european_plug.plug_in()

     # Example usage
     european_plug = EuropeanPlug()
     adapter = Adapter(european_plug)
     adapter.plug_in()  # Output: Plugging in using European plug.
     ```

### 5. **Decorator Pattern**
   - **Definition**: The **Decorator Pattern** allows behavior to be added to an individual object, dynamically, without affecting the behavior of other objects from the same class.
   - **Use Case**: Useful for adding functionalities like logging, authentication, etc., without modifying the original code.
   - **Code Example**:
     ```python
     class Coffee:
         def cost(self):
             return 5

     class MilkDecorator:
         def __init__(self, coffee):
             self._coffee = coffee
         
         def cost(self):
             return self._coffee.cost() + 1  # Add the cost of milk

     class SugarDecorator:
         def __init__(self, coffee):
             self._coffee = coffee
         
         def cost(self):
             return self._coffee.cost() + 0.5  # Add the cost of sugar

     # Example usage
     basic_coffee = Coffee()
     coffee_with_milk = MilkDecorator(basic_coffee)
     coffee_with_milk_and_sugar = SugarDecorator(coffee_with_milk)
     print(coffee_with_milk_and_sugar.cost())  # Output: 6.5
     ```

### 6. **Facade Pattern**
   - **Definition**: The **Facade Pattern** provides a simplified interface to a complex system.
   - **Use Case**: Used when you want to provide an easy-to-use interface over a large body of code or multiple subsystems.
   - **Code Example**:
     ```python
     class CPU:
         def start(self):
             print("CPU starting...")

     class Memory:
         def load(self):
             print("Loading memory...")

     class HardDrive:
         def read(self):
             print("Reading data from hard drive...")

     class Computer:
         def __init__(self):
             self.cpu = CPU()
             self.memory = Memory()
             self.hard_drive = HardDrive()
         
         def start_computer(self):
             self.cpu.start()
             self.memory.load()
             self.hard_drive.read()

     # Example usage
     computer = Computer()
     computer.start_computer()
     # Output:
     # CPU starting...
     # Loading memory...
     # Reading data from hard drive...
     ```

---

These patterns help in designing **scalable, flexible, and maintainable** software systems. While we have now covered some of the most common patterns, each provides a different way to solve recurring problems in software design. Let me know if you'd like to dive deeper into any of these patterns or need more examples!
