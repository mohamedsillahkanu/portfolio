# 📖 Chapter 2: Types of Functions

## 2.1 Introduction  
In the previous chapter, we learned what functions are and why they are important. Now, let’s explore different types of functions used in Python.

## 2.2 Built-in Functions  
Python provides many **built-in functions** such as `print()`, `len()`, `sum()`, `max()`, and `min()`.

### Example:
```python
numbers = [10, 20, 30, 40]

print(len(numbers))  # Output: 4
print(sum(numbers))  # Output: 100
print(max(numbers))  # Output: 40
print(min(numbers))  # Output: 10
```

---

## 2.3 User-Defined Functions
A **user-defined function** is a function created by the programmer.

### Example:
```python
def greet(name):
    return f"Hello, {name}!"

print(greet("Alice"))  # Output: Hello, Alice!
```

---

## 2.4 Lambda Functions
A **lambda function** is a small, one-line function.

### Example:
```python
square = lambda x: x**2
print(square(5))  # Output: 25
```

---

## 2.5 Recursive Functions
A **recursive function** is a function that **calls itself**.

### Example: Factorial
The factorial of a number $n$ is:

$$
n! = n \times (n-1) \times (n-2) \times ... \times 1
$$

For example:

$$
5! = 5 \times 4 \times 3 \times 2 \times 1 = 120
$$

```python
def factorial(n):
    if n == 1:
        return 1
    return n * factorial(n - 1)

print(factorial(5))  # Output: 120
```

---

## 2.6 Fibonacci Sequence
The Fibonacci sequence is:

$$
F(n) = F(n-1) + F(n-2)
$$

where:

$$
F(0) = 0, \quad F(1) = 1
$$

### Example:
```python
def fibonacci(n):
    if n == 0:
        return 0
    elif n == 1:
        return 1
    return fibonacci(n - 1) + fibonacci(n - 2)

print(fibonacci(6))  # Output: 8
```

---

## Summary
| Function Type      | Description |
|--------------------|-------------|
| **Built-in**      | Predefined functions like `len()` and `sum()` |
| **User-Defined**  | Functions written by programmers |
| **Lambda**        | Short, anonymous functions |
| **Recursive**     | Functions that call themselves |

---

## 📌 Exercises
1. Write a function to check if a number is **even or odd**.
2. Create a lambda function to **find the cube** of a number.
3. Write a **recursive function** to calculate the **sum of numbers from 1 to n**.
4. Implement a **user-defined function** that finds the **maximum of three numbers**.

