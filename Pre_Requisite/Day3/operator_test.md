```python
# Numeric values
a = 10
b = 3

# ===== 1. Arithmetic Operators =====
print("Arithmetic Operators:")
print("Addition:", a + b)        # 10 + 3 = 13
print("Subtraction:", a - b)     # 10 - 3 = 7
print("Multiplication:", a * b)  # 10 * 3 = 30
print("Division:", a / b)        # 10 / 3 = 3.33
print("Modulus:", a % b)         # Remainder = 1
print("Power:", a ** b)          # 10^3 = 1000

# ===== 2. Comparison Operators =====
print("\nComparison Operators:")
print("a == b:", a == b)   # False
print("a != b:", a != b)   # True
print("a > b:", a > b)     # True
print("a < b:", a < b)     # False
print("a >= b:", a >= b)   # True
print("a <= b:", a <= b)   # False

# ===== 3. Logical Operators =====
print("\nLogical Operators:")
x = True
y = False

print("x and y:", x and y)   # False
print("x or y:", x or y)     # True
print("not x:", not x)       # False

# ===== 4. Assignment Operators =====
print("\nAssignment Operators:")
c = 5
c += 2   # c = c + 2
print("c += 2:", c)

c *= 3   # c = c * 3
print("c *= 3:", c)

# ===== 5. Membership Operators =====
print("\nMembership Operators:")
numbers = [1, 2, 3, 4]

print("2 in numbers:", 2 in numbers)        # True
print("5 not in numbers:", 5 not in numbers) # True

# ===== 6. Identity Operators =====
print("\nIdentity Operators:")
list1 = [1, 2, 3]
list2 = list1
list3 = [1, 2, 3]

print("list1 is list2:", list1 is list2)     # True (same object)
print("list1 is list3:", list1 is list3)     # False (different object)
print("list1 == list3:", list1 == list3)     # True (same values)
```
