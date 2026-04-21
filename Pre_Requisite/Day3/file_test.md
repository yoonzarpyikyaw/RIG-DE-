```python
# File names
main_file = "student_data.txt"
copy_file = "student_data_copy.txt"


# 1. Create and write to a file
def write_file():
    with open(main_file, "w") as file:
        file.write("Name: Alice\n")
        file.write("Age: 20\n")
        file.write("City: Yangon\n")
    print("File created and data written successfully.")


# 2. Read file content
def read_file():
    try:
        with open(main_file, "r") as file:
            content = file.read()
        print("\n--- File Content ---")
        print(content)
    except FileNotFoundError:
        print("File not found.")


# 3. Append new data to file
def append_file():
    with open(main_file, "a") as file:
        file.write("Course: Python Programming\n")
        file.write("Status: Active\n")
    print("New data appended successfully.")


# 4. Read file line by line
def read_lines():
    try:
        with open(main_file, "r") as file:
            print("\n--- Reading Line by Line ---")
            for line in file:
                print(line.strip())
    except FileNotFoundError:
        print("File not found.")


# 5. Count number of lines in file
def count_lines():
    try:
        with open(main_file, "r") as file:
            lines = file.readlines()
        print("\nTotal number of lines:", len(lines))
    except FileNotFoundError:
        print("File not found.")


# 6. Search for a word in file
def search_word(word):
    try:
        with open(main_file, "r") as file:
            content = file.read()

        if word in content:
            print(f'\nThe word "{word}" was found in the file.')
        else:
            print(f'\nThe word "{word}" was not found in the file.')
    except FileNotFoundError:
        print("File not found.")


# 7. Copy file content to another file
def copy_content():
    try:
        with open(main_file, "r") as source:
            data = source.read()

        with open(copy_file, "w") as target:
            target.write(data)

        print(f"\nContent copied successfully to {copy_file}.")
    except FileNotFoundError:
        print("Source file not found.")


# 8. Main program
def main():
    print("=== Python File Operations Demo ===")

    # Step 1: Write file
    write_file()

    # Step 2: Read file
    read_file()

    # Step 3: Append file
    append_file()

    # Step 4: Read updated file
    read_file()

    # Step 5: Read line by line
    read_lines()

    # Step 6: Count lines
    count_lines()

    # Step 7: Search word
    search_word("Python")

    # Step 8: Copy file
    copy_content()


# Run program
main()
```
