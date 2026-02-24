# Smart Library System

## 📌 Project Overview

The Smart Library System is a fully Pythonic, object-oriented library management system built without any external database.  

This project demonstrates advanced Python concepts including:

- Object-Oriented Programming (OOP)
- Magic (Dunder) Methods
- Custom Iterable Containers
- Decorators
- Closures
- Role-Based Access Control
- Python Packaging Structure
- Duck Typing
- Method Resolution Order (MRO) using C3 Linearization

---

## 📂 Project Structure

```
smart_library/
│
├── README.md
└── library_system/
    ├── __init__.py
    ├── core.py
    ├── utils.py
    └── __main__.py
```

---

## 🚀 How to Run the Project

Navigate to the `smart_library` directory:

```bash
cd smart_library
```

Run the package:

```bash
python -m library_system
```

This executes `__main__.py` and demonstrates the system functionality.

---

# 🧱 Part 1: Core (OOP & Magic Methods)

## Book Class

Implements:

- `__str__` → User-friendly representation  
- `__len__` → Returns number of pages  
- `__eq__` → Compares books by title and author  

Example:

```python
print(book)
len(book)
book1 == book2
```

---

## Library Class

- Stores books internally in a list
- Implements `__getitem__` to allow iteration:

```python
for book in library:
    print(book)
```

This makes the Library behave like a container.

---

# ⚙ Part 2: Advanced Logic (Decorators & Closures)

## Logging Decorator

`@track_access` logs:

- Timestamp
- Method name
- Arguments

Every time a book is borrowed or returned.

---

## Permission Control Using Closure

`permission_check(required_role)`:

- Returns a decorator
- Enforces role-based access
- Only users with the correct role (e.g., Admin) can add/remove books

This demonstrates closure behavior because the inner decorator remembers `required_role`.

---

# 🦆 Duck Typing Demonstration

The method:

```python
def borrow_item(self, item):
    print(f"Borrowing {item.title}")
    item.borrow()
```

Does NOT check type.

It works with ANY object that:

- Has a `.title` attribute
- Has a `.borrow()` method

Example:

```python
class Magazine:
    def __init__(self, title):
        self.title = title

    def borrow(self):
        pass
```

This demonstrates true Pythonic Duck Typing:

"If it behaves like a Book, it is treated like a Book."

---

# 🧠 Method Resolution Order (MRO) & C3 Linearization

Assume we create:

```python
class Software:
    pass

class DigitalBook(Book, Software):
    pass
```

Python uses **C3 Linearization** to determine method lookup order.

## Step 1: Compute Parent MROs

```
MRO(Book) = [Book, object]
MRO(Software) = [Software, object]
```

## Step 2: Apply C3 Merge Algorithm

```
MRO(DigitalBook) =
DigitalBook
+ merge(
    MRO(Book),
    MRO(Software),
    [Book, Software]
)
```

Result:

```
DigitalBook
Book
Software
object
```

This ensures:

- Local precedence order
- Monotonicity
- Consistency
- Deterministic method resolution

You can verify using:

```python
print(DigitalBook.__mro__)
```

---

# 📏 PEP 8 Compliance

The project strictly follows:

- Proper naming conventions
- Line length limits
- Docstrings
- Clear spacing and formatting

---

# 🎯 Conclusion

This project demonstrates advanced Python design principles including:

- Operator overloading
- Custom container behavior
- Decorator patterns
- Closure-based access control
- Package architecture
- Multiple inheritance resolution
- Duck typing

The system is fully runnable and modular, structured as a professional Python package.
