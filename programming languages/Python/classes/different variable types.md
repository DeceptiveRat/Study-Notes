In Python, **local variables**, **class variables**, and **instance variables** each have different scopes and purposes. Here's a clear breakdown of each:

---

### ✅ Local Variables

* **Defined inside a function or method.**
* **Accessible only within that function.**
* **Created when the function is called, destroyed when the function ends.**

```python
def greet():
    message = "Hello"  # local variable
    print(message)

greet()
# print(message)  # ❌ Error: message is not defined outside the function
```

---

### ✅ Instance Variables

* **Defined inside a class using `self` (e.g., `self.name`).**
* **Unique to each instance (object) of the class.**
* Used to store **object-specific data**.

```python
class Dog:
    def __init__(self, name):
        self.name = name  # instance variable

dog1 = Dog("Fido")
dog2 = Dog("Buddy")

print(dog1.name)  # Fido
print(dog2.name)  # Buddy
```

---

### ✅ Class Variables

* **Shared by all instances** of the class.
* **Defined inside the class but outside of any methods.**
* Typically used for **constants or shared data**.

```python
class Dog:
    species = "Canis familiaris"  # class variable

    def __init__(self, name):
        self.name = name  # instance variable

dog1 = Dog("Fido")
dog2 = Dog("Buddy")

print(dog1.species)  # Canis familiaris
print(dog2.species)  # Canis familiaris
```

> If you modify `species` using the class (e.g., `Dog.species = "Wolf"`), it changes for all instances. But if you change it via an instance (`dog1.species = "Cat"`), it creates a **new instance variable** instead.

---

### 🔁 Summary Table

| Variable Type     | Defined In                         | Accessed With             | Scope                    | Shared? |
| ----------------- | ---------------------------------- | ------------------------- | ------------------------ | ------- |
| Local Variable    | Inside function/method             | By name                   | Only inside the function | ❌ No    |
| Instance Variable | Inside class methods (with `self`) | `self.var_name`           | Per object               | ❌ No    |
| Class Variable    | Inside class (outside methods)     | `Class.var` or `self.var` | Whole class & instances  | ✅ Yes   |

Would you like an example that shows all three together?
