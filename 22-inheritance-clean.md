# 🔥 **Python Inheritance Interview Guide (Beginner to Pro)** 🔥  

This guide covers **everything** about **inheritance in Python**, from basic concepts to advanced scenarios, with **real interview questions**, **practical examples**, and **clear explanations**.  

---

## **📌 Table of Contents**  
1. [Basic Inheritance](#-basic-inheritance-questions) (Beginner)  
2. [Intermediate Inheritance](#-intermediate-inheritance-questions) (Mid-Level)  
3. [Advanced Inheritance](#-advanced-inheritance-questions) (Pro-Level)  
4. [Real-World Scenarios](#-real-world-inheritance-scenarios) (Case Studies)  
5. [Cheat Sheet](#-cheat-sheet-key-takeaways)  

---

## **🔹 Basic Inheritance Questions**  

### **1. What is inheritance in Python?**  
✅ **Answer:**  
Inheritance allows a **child class** to **reuse** methods and attributes from a **parent class**.  

<details><summary>📌 Example</summary>  

```python
class Animal:
    def speak(self):
        print("Animal speaks")

class Dog(Animal):  # Dog inherits from Animal
    pass

dog = Dog()
dog.speak()  # Output: "Animal speaks"
```
</details>  

---

### **2. What is `super()` in Python?**  
✅ **Answer:**  
`super()` is used to **call a method from the parent class** (useful in constructors).  

<details><summary>📌 Example</summary>  

```python
class Person:
    def __init__(self, name):
        self.name = name

class Employee(Person):
    def __init__(self, name, salary):
        super().__init__(name)  # Calls Person.__init__
        self.salary = salary

emp = Employee("Alice", 50000)
print(emp.name, emp.salary)  # Output: Alice 50000
```
</details>  

---

### **3. What is method overriding?**  
✅ **Answer:**  
When a **child class** provides its own implementation of a method already defined in the **parent class**.  

<details><summary>📌 Example</summary>  

```python
class Bird:
    def fly(self):
        print("Flying high!")

class Penguin(Bird):
    def fly(self):  # Overrides Bird.fly()
        print("Penguins can't fly!")

p = Penguin()
p.fly()  # Output: "Penguins can't fly!"
```
</details>  

---

## **🔹 Intermediate Inheritance Questions**  

### **4. What is multiple inheritance?**  
✅ **Answer:**  
When a class inherits from **more than one parent class**.  

<details><summary>📌 Example</summary>  

```python
class Father:
    def skills(self):
        print("Programming")

class Mother:
    def skills(self):
        print("Cooking")

class Child(Father, Mother):  # Inherits from both
    pass

kid = Child()
kid.skills()  # Output: "Programming" (due to MRO)
```
</details>  

---

### **5. What is MRO (Method Resolution Order)?**  
✅ **Answer:**  
The order in which Python searches for methods in inheritance.  

<details><summary>📌 Example</summary>  

```python
class A:
    def show(self):
        print("A")

class B(A):
    pass

class C(A):
    def show(self):
        print("C")

class D(B, C):
    pass

d = D()
d.show()  # Output: "C" (due to MRO)
print(D.mro())  # [D, B, C, A, object]
```
</details>  

---

### **6. What is multilevel inheritance?**  
✅ **Answer:**  
When a **child class** inherits from another **child class** (forming a chain).  

<details><summary>📌 Example</summary>  

```python
class Grandfather:
    def wealth(self):
        print("Rich")

class Father(Grandfather):
    def job(self):
        print("Engineer")

class Son(Father):  # Inherits from Father (which inherits from Grandfather)
    pass

s = Son()
s.wealth()  # Output: "Rich"
s.job()     # Output: "Engineer"
```
</details>  

---

## **🔹 Advanced Inheritance Questions**  

### **7. What is the Diamond Problem?**  
✅ **Answer:**  
A confusion in **multiple inheritance** when a class inherits from **two classes that have a common parent**.  

<details><summary>📌 Example</summary>  

```python
class A:
    def show(self):
        print("A")

class B(A):
    def show(self):
        print("B")

class C(A):
    def show(self):
        print("C")

class D(B, C):
    pass

d = D()
d.show()  # Output: "B" (due to MRO)
```
</details>  

---

### **8. How to prevent a method from being overridden?**  
✅ **Answer:**  
Use **name mangling** (`__method`) or **documentation** (but Python doesn’t enforce it).  

<details><summary>📌 Example</summary>  

```python
class Parent:
    def __secret(self):  # Name mangling
        print("Can't override easily")

class Child(Parent):
    def __secret(self):  # Doesn't override Parent.__secret
        print("Tried to override")

c = Child()
# c.__secret()  ❌ Error (use _Parent__secret)
```
</details>  

---

### **9. When to use composition over inheritance?**  
✅ **Answer:**  
- Use **inheritance** for **"is-a"** relationships (e.g., `Dog` is an `Animal`).  
- Use **composition** for **"has-a"** relationships (e.g., `Car` has an `Engine`).  

<details><summary>📌 Example</summary>  

```python
class Engine:
    def start(self):
        print("Engine starts")

class Car:
    def __init__(self):
        self.engine = Engine()  # Composition

car = Car()
car.engine.start()  # Output: "Engine starts"
```
</details>  

---

## **🔹 Real-World Inheritance Scenarios**  

### **10. Scenario: Building a Payment System**  
✅ **Problem:**  
You need `CreditCard`, `PayPal`, and `UPI` payment methods with common validation.  

<details><summary>📌 Solution</summary>  

```python
class Payment:
    def validate(self, amount):
        return amount > 0

class CreditCard(Payment):
    def pay(self, amount):
        if self.validate(amount):
            print("Paid via CreditCard")

class UPI(Payment):
    def pay(self, amount):
        if self.validate(amount):
            print("Paid via UPI")

cc = CreditCard()
cc.pay(100)  # Output: "Paid via CreditCard"
```
</details>  

---

## **📜 Cheat Sheet (Key Takeaways)**  

| Concept | Key Point |
|---------|-----------|
| **Inheritance** | Child class reuses parent’s methods. |
| **`super()`** | Calls parent’s method. |
| **Method Overriding** | Child modifies parent’s method. |
| **Multiple Inheritance** | Inherit from >1 class (use MRO). |
| **Diamond Problem** | Solved by MRO. |
| **Composition > Inheritance?** | Prefer composition for "has-a" relationships. |

---

## **🎯 Final Tips for Interviews**  
✔ **Always explain MRO** when discussing multiple inheritance.  
✔ Use **`super()`** correctly in constructors.  
✔ Know **when to use inheritance vs composition**.  

🚀 **Now you’re ready to ace inheritance questions!**  

Would you like **practice exercises** or **mock interview questions** next? 😊
