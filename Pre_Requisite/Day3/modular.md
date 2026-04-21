```python
# ===== Student Result Management System =====

# Function 1: Input student data

def get_student_data():
    name = input("Enter student name: ")
    marks = []

    # Take 3 subject marks
    for i in range(3):
        mark = int(input(f"Enter mark {i+1}: "))
        marks.append(mark)

    return name, marks


# Function 2: Calculate total and average
def calculate_result(marks):
    total = sum(marks)
    average = total / len(marks)
    return total, average


# Function 3: Check grade
def check_grade(avg):
    if avg >= 80:
        return "Grade A"
    elif avg >= 50:
        return "Grade B"
    else:
        return "Fail"


# Function 4: Display result
def display_result(name, marks, total, avg, grade):
    print("\n===== Student Result =====")
    print("Name:", name)
    print("Marks:", marks)
    print("Total:", total)
    print("Average:", avg)
    print("Result:", grade)


# ===== Main Program (Combining all modules) =====
def main():
    name, marks = get_student_data()           # Module 1
    total, avg = calculate_result(marks)       # Module 2
    grade = check_grade(avg)                   # Module 3
    display_result(name, marks, total, avg, grade)  # Module 4


# Run program
main()
```
