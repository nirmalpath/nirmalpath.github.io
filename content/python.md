# Python Notes
## Mindmap

## Topics

- Basic Syntax
- Data Types
- Collections
- Control Flow
- Functions
- List Comprehension
- Strings
- Input/Output
- File Handling
- Exception Handling
- Modules n Imports
- Useful Built-ins
- Classes n OOP
- Lambda Function
- Virtual Environment (CLI)
- Useful Coding Snippets
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Basic Syntax
    1. Comment
      print("Hello, World!")
    2. Variables
      x = 10
      name - "Alice"
    3. Multiple Assignments
      a, b = 1, 2
      
### Data Types
    int_num = 10       #integer
    float_num = 3.14   #float
    text = "hello"     #string
    is_true = True     #boolean

### Collections
    # List (mutable)
    my_list = [1, 2, 3]
    my_list.appen(4)

    # Tuple (immutable)
    my_tuple = (1, 2, 3)

    # Set (unique values)
    my_set = {1, 2, 3}

    # Dictionary (key-value)
    my_dict = {"a": 1, "b": 2}
    print(my_dict["a"]

### Control Flow
    # If-else
    if z > 0:
      print("Positive")
    elif x==0;
      print("Zero")
    else:
      print("Negative")

    # For loop
    for i in range(5):
      print(i)

    # While loop
    while x > 0:
      x -= 1

### Functions
    def great(name):
      return f"Hello, {name}"

    print(greet("Alice"))

### List Comprehension
    squares = [x**2 for x in range(5)]

### Strings
    text = "hello"
    print(text.upper())
    print(text[0])
    print(len(text))


### Input/Ouput
    name = input("Enter nae" ")
    print(f"Hi {name})


### File Handling
    # Write
    with open("file.txt", "w") as f:
        f.write("Hello")

    # Read
    with open("file.txt", "r") as f:
        content = f.read()

### Exception Handling
    try:
        x = int("abc")
    except ValueError:
        print("Conversion failed")
    finally:
        print("Done")

### Modules n Imports
    import math
    print(math.sqrt(16))
    
    from datetime import datetime
    print(datetime.now())

### Useful Built-ins
    len([1,2,3])
    type(10)
    range(5)
    sum([1,2,3])
    max([1,2,3])
    min([1,2,3])

### Classes n OOP
    class Person:
        def __init__(self, name):
            self.name = name
    
        def greet(self):
            return f"Hi, I'm {self.name}"
    
    p = Person("Alice")
    print(p.greet())

### Lambda Functions
    add = lambda a, b: a + b
    print(add(2, 3))

### Virtual Environments (CLI)
    python -m venv venv
    source venv/bin/activate   # Mac/Linux
    venv\Scripts\activate      # Windows

### Useful Coding Snippets
    # Check if key exists
      data = {"name": "Alice"}
      
      if "name" in data:
          print(data["name"])

    # Swap 2 Variables
      a, b = 5, 10
      a, b = b, a

    # Count Frequency of items
      from collections import Counter
  
      items = ["a", "b", "a", "c"]
      count = Counter(items)
      print(count)   # {'a': 2, 'b': 1, 'c': 1}

    # Read CSV Easily
      import csv

      with open("file.csv") as f:
          reader = csv.reader(f)
          for row in reader:
              print(row)

    # Remove duplicates from list
      my_list = [1, 2, 2, 3]
      unique = list(set(my_list))

    # Merge 2 dictionaries
      a = {"x": 1}
      b = {"y": 2}
      
      merged = {**a, **b}

    # Join list into string
      words = ["Python", "is", "awesome"]
      sentence = " ".join(words)

    # Find index of item safely
      my_list = ["a", "b", "c"]

      index = my_list.index("b") if "b" in my_list else -1

    # Current date n time
      from datetime import datetime
      
      now = datetime.now()
      print(now.strftime("%Y-%m-%d %H:%M:%S"))

    # List files in directory
      import os
      
      files = os.listdir(".")
      print(files)

    # Memorization (cache results)
      from functools import lru_cache
      
      @lru_cache(maxsize=None)
      def fib(n):
          if n < 2:
              return n
          return fib(n-1) + fib(n-2)

    # Flatten List
        nested = [[1, 2], [3, 4]]
        flat = [item for sublist in nested for item in sublist]

    # Generate random password
        import random
        import string
        
        password = ''.join(random.choices(string.ascii_letters + string.digits, k=8))

    # Measure Execution Time
        import time
        
        start = time.time()
        
        # your code here
        
        end = time.time()
        print("Time:", end - start)

    # Read json file
      import json
      
      with open("data.json") as f:
          data = json.load(f)

    # Write json file
      import json

      data = {"name": "Alice"}
      
      with open("data.json", "w") as f:
          json.dump(data, f, indent=4)

    # Iterate with index
      for i, val in enumerate(["a", "b", "c"]):
      print(i, val)

    # Simple re-try logic
      import time

      for _ in range(3):
          try:
              print("Trying...")
              break
          except Exception:
              time.sleep(1)

    # Zip multiple lists
      names = ["Alice", "Bob"]
      scores = [90, 85]
  
      for name, score in zip(names, scores):
          print(name, score)

    # Clean String
      text = "  hello world  "
      clean = text.strip()

    # Dictionary Default Values
      from collections import defaultdict
      
      d = defaultdict(int)
      d["a"] += 1
