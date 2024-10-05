### **SOLID Principles**

The **SOLID** principles are five design principles that help developers create more maintainable and scalable software. These principles are used to ensure good object-oriented design and programming practices. Here’s a quick recap of each principle along with implementation examples:

1. **Single Responsibility Principle (SRP)**
   - **Definition**: A class should have **only one reason to change**, meaning it should have only one job or responsibility.
   - **Purpose**: This principle helps keep classes **simple and focused**. When a class has only one responsibility, it becomes easier to maintain and modify, as changes are isolated to a specific purpose.
   - **Code Example**:
     ```python
     class Order:
         def __init__(self, order_id, items):
             self.order_id = order_id
             self.items = items  # List of items in the order

     class OrderPrinter:
         def print_order(self, order: Order):
             print(f"Order ID: {order.order_id}")
             for item in order.items:
                 print(f"- {item}")
     
     # Creating an order and printing it
     order = Order(1, ["Item1", "Item2", "Item3"])
     order_printer = OrderPrinter()
     order_printer.print_order(order)
     ```

2. **Open/Closed Principle (OCP)**
   - **Definition**: Software entities (e.g., classes, functions) should be **open for extension** but **closed for modification**.
   - **Purpose**: This ensures that you can **add new functionality** without altering existing code, which helps prevent bugs.
   - **Code Example**:
     ```python
     from abc import ABC, abstractmethod

     class Discount(ABC):
         @abstractmethod
         def calculate(self, amount):
             pass

     class NoDiscount(Discount):
         def calculate(self, amount):
             return amount

     class PercentageDiscount(Discount):
         def __init__(self, percent):
             self.percent = percent
         
         def calculate(self, amount):
             return amount * (1 - self.percent / 100)
     
     # Applying different discounts
     amount = 1000
     no_discount = NoDiscount()
     percentage_discount = PercentageDiscount(10)
     print("No Discount:", no_discount.calculate(amount))
     print("Percentage Discount (10%):", percentage_discount.calculate(amount))
     ```

3. **Liskov Substitution Principle (LSP)**
   - **Definition**: Objects of a superclass should be **replaceable with objects of a subclass** without affecting the correctness of the program.
   - **Purpose**: This ensures that derived classes are **fully compatible** with their base classes, allowing for better substitutability.
   - **Code Example**:
     ```python
     class Rectangle:
         def __init__(self, width, height):
             self.width = width
             self.height = height
         
         def get_area(self):
             return self.width * self.height

     class Square(Rectangle):
         def __init__(self, side_length):
             super().__init__(side_length, side_length)
     
     # Using Rectangle and Square
     rectangle = Rectangle(10, 20)
     square = Square(15)
     print("Rectangle Area:", rectangle.get_area())
     print("Square Area:", square.get_area())
     ```

4. **Interface Segregation Principle (ISP)**
   - **Definition**: A class should not be forced to implement interfaces it does not use. Instead, many **small, specific interfaces** are better than one large, general-purpose interface.
   - **Purpose**: This principle helps reduce **unnecessary dependencies** in your code by ensuring that interfaces are **tailored** to specific clients.
   - **Code Example**:
     ```python
     from abc import ABC, abstractmethod

     class Printer(ABC):
         @abstractmethod
         def print_document(self, document):
             pass

     class Scanner(ABC):
         @abstractmethod
         def scan_document(self, document):
             pass

     class MultiFunctionPrinter(Printer, Scanner):
         def print_document(self, document):
             print(f"Printing: {document}")
         
         def scan_document(self, document):
             print(f"Scanning: {document}")

     class SimplePrinter(Printer):
         def print_document(self, document):
             print(f"Printing: {document}")
     
     # Using different printer types
     printer = SimplePrinter()
     printer.print_document("Document1")

     multi_printer = MultiFunctionPrinter()
     multi_printer.print_document("Document2")
     multi_printer.scan_document("Document3")
     ```

5. **Dependency Inversion Principle (DIP)**
   - **Definition**: High-level modules should not depend on low-level modules. Both should depend on **abstractions**. Abstractions should not depend on details; details should depend on abstractions.
   - **Purpose**: This reduces the **tight coupling** between high-level and low-level components, making the code more flexible and reusable.
   - **Code Example**:
     ```python
     class MessageSender(ABC):
         @abstractmethod
         def send(self, message):
             pass

     class EmailSender(MessageSender):
         def send(self, message):
             print(f"Sending email: {message}")

     class SMSSender(MessageSender):
         def send(self, message):
             print(f"Sending SMS: {message}")

     class NotificationService:
         def __init__(self, sender: MessageSender):
             self.sender = sender
         
         def notify(self, message):
             self.sender.send(message)
     
     # Sending notifications
     email_sender = EmailSender()
     sms_sender = SMSSender()
     notification_service = NotificationService(email_sender)
     notification_service.notify("Hello via Email!")

     notification_service_sms = NotificationService(sms_sender)
     notification_service_sms.notify("Hello via SMS!")
     ```

---

These principles help developers write **modular, maintainable, and testable** code, reducing the risk of bugs and making it easier to extend the system in the future. Let me know if you'd like to dive deeper into any of these principles or if you have questions about how they apply to real-world scenarios!
