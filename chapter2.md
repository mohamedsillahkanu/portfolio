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



---

### **1. Filtering Data Based on a Condition**
#### **Regular Function Approach**
```python
def filter_even_numbers(data):
    return [num for num in data if num % 2 == 0]

numbers = [10, 15, 20, 25, 30, 35, 40]
even_numbers = filter_even_numbers(numbers)
print(even_numbers)  # Output: [10, 20, 30, 40]
```
#### **Lambda Function Approach**
```python
numbers = [10, 15, 20, 25, 30, 35, 40]
even_numbers = list(filter(lambda x: x % 2 == 0, numbers))
print(even_numbers)  # Output: [10, 20, 30, 40]
```
---

### **2. Transforming Data (Squaring Numbers)**
#### **Regular Function Approach**
```python
def square_numbers(data):
    return [num**2 for num in data]

numbers = [1, 2, 3, 4, 5]
squared_numbers = square_numbers(numbers)
print(squared_numbers)  # Output: [1, 4, 9, 16, 25]
```
#### **Lambda Function Approach**
```python
numbers = [1, 2, 3, 4, 5]
squared_numbers = list(map(lambda x: x**2, numbers))
print(squared_numbers)  # Output: [1, 4, 9, 16, 25]
```
---

### **3. Sorting a List of Dictionaries by a Key (e.g., Sorting Employees by Salary)**
#### **Regular Function Approach**
```python
def sort_by_salary(employees):
    return sorted(employees, key=lambda emp: emp["salary"])

employees = [
    {"name": "Alice", "salary": 50000},
    {"name": "Bob", "salary": 70000},
    {"name": "Charlie", "salary": 60000}
]

sorted_employees = sort_by_salary(employees)
print(sorted_employees)
```
#### **Lambda Function Approach**
```python
employees = [
    {"name": "Alice", "salary": 50000},
    {"name": "Bob", "salary": 70000},
    {"name": "Charlie", "salary": 60000}
]

sorted_employees = sorted(employees, key=lambda emp: emp["salary"])
print(sorted_employees)
```
---

### **4. Grouping Data Based on a Condition (Even and Odd Numbers)**
#### **Regular Function Approach**
```python
def group_numbers(data):
    even = [num for num in data if num % 2 == 0]
    odd = [num for num in data if num % 2 != 0]
    return {"even": even, "odd": odd}

numbers = [10, 15, 20, 25, 30, 35, 40]
grouped_numbers = group_numbers(numbers)
print(grouped_numbers)
```
#### **Lambda Function Approach**
```python
numbers = [10, 15, 20, 25, 30, 35, 40]
even_numbers = list(filter(lambda x: x % 2 == 0, numbers))
odd_numbers = list(filter(lambda x: x % 2 != 0, numbers))

grouped_numbers = {"even": even_numbers, "odd": odd_numbers}
print(grouped_numbers)
```
---

### **5. Summing Values in a List (Aggregation)**
#### **Regular Function Approach**
```python
def sum_numbers(data):
    return sum(data)

numbers = [10, 20, 30, 40, 50]
total_sum = sum_numbers(numbers)
print(total_sum)  # Output: 150
```
#### **Lambda Function Approach**
```python
from functools import reduce

numbers = [10, 20, 30, 40, 50]
total_sum = reduce(lambda x, y: x + y, numbers)
print(total_sum)  # Output: 150
```
---


