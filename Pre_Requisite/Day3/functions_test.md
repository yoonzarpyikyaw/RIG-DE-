```python
# Simple Function
def greet():
    print("Hello World")

greet()

#Function with Parameters
def greet(name):
    print("Hello", name)

greet("Alice")

# Function with Return Value
def add(a, b):
    return a + b

result = add(5, 3)
print(result)

# Modular Programming
def calculate_total(marks):
    return sum(marks)

def check_result(avg):
    if avg >= 50:
        return "Pass"
    else:
        return "Fail"

marks = [80, 70, 90]
avg = calculate_total(marks) / len(marks)
print(check_result(avg))

```
