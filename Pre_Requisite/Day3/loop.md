```python
# 1. FOR LOOP (Print numbers 1 to 5)
print("For Loop Example:")
for i in range(1, 6):
    print(i)

# 2. FOR LOOP with CONDITION (Even numbers)
print("\nEven Numbers (1 to 10):")
for i in range(1, 11):
    if i % 2 == 0:
        print(i)

# 3. WHILE LOOP (Print numbers 1 to 5)
print("\nWhile Loop Example:")
i = 1
while i <= 5:
    print(i)
    i += 1   # increment to avoid infinite loop

# 4. BREAK STATEMENT (Stop loop at 5)
print("\nBreak Example:")
for i in range(1, 10):
    if i == 5:
        break   # stop loop when i = 5
    print(i)

# 5. CONTINUE STATEMENT (Skip number 3)
print("\nContinue Example:")
for i in range(1, 6):
    if i == 3:
        continue   # skip 3
    print(i)

# 6. NESTED LOOP (Multiplication table)
print("\nNested Loop (Multiplication Table 1 to 3):")
for i in range(1, 4):
    for j in range(1, 4):
        print(i, "x", j, "=", i * j)

# 7. LOOP WITH LIST
print("\nLoop through List:")
names = ["Alice", "Bob", "Charlie"]
for name in names:
    print("Hello", name)
```
