## Data structure tutorial exercise: Stack
1. Write a function in python that can reverse a string using stack data structure. Use [Stack class](https://github.com/codebasics/data-structures-algorithms-python/blob/master/data_structures/5_Stack/5_stack.ipynb) from the tutorial.
    ```
    reverse_string("We will conquere COVID-19") should return "91-DIVOC ereuqnoc lliw eW"
    ```
Solution:
```py
from collections import deque

class Stack:
    def __init__(self):
        self.container = deque()

    def push(self, val):
        self.container.append(val)

    def pop(self):
        return self.container.pop()

    def peek(self):
        return self.container[-1]

    def is_empty(self):
        return len(self.container) == 0

    def size(self):
        return len(self.container)

def reverseStrings(str):
    stack = Stack()

    for s in str:
        stack.push(s) ## append in deque

    revString = ''
    while not stack.is_empty():
        revString += stack.pop()

    return revString
```
[Solution](https://github.com/codebasics/data-structures-algorithms-python/blob/master/data_structures/5_Stack/Exercise/reverse_string.py)

2. Write a function in python that checks if paranthesis in the string are balanced or not. Possible parantheses are "{}',"()" or "[]". Use [Stack class](https://github.com/codebasics/data-structures-algorithms-python/blob/master/data_structures/5_Stack/5_stack.ipynb) from the tutorial.
    ```
    is_balanced("({a+b})")     --> True
    is_balanced("))((a+b}{")   --> False
    is_balanced("((a+b))")     --> True
    is_balanced("))")          --> False
    is_balanced("[a+b]*(x+2y)*{gg+kk}") --> True
    ```

Solution
```py
from collections import deque

class Stack:
    def __init__(self):
        self.container = deque()

    def push(self, val):
        self.container.append(val)

    def pop(self):
        return self.container.pop()

    def peek(self):
        return self.container[-1]

    def is_empty(self):
        return len(self.container) == 0

    def size(self):
        return len(self.container)

##  Write a function in python that checks if paranthesis in the string are balanced or not. Possible parantheses are "{}',"()" or "[]".
def is_balanced(str):
    stack = Stack()
    opening_brackets = ['(', '{', '[']
    closing_brackets = [')', '}', ']']

    for char in str:
        if char in opening_brackets:  # Push opening brackets onto the stack
            stack.push(char)

        elif char in closing_brackets:  # Check if this closing bracket matches the top element on stack
            if stack.is_empty():  # If the stack is already empty, there's no matching opening bracket
                return False

            top_element = stack.pop()  # Pop the top element from stack

            # Get the corresponding opening bracket for this closing bracket
            corresponding_opening_bracket = opening_brackets[closing_brackets.index(char)]

            if top_element != corresponding_opening_bracket:  # If the popped element is not the matching opening bracket
                return False

    return stack.is_empty()  # If the stack is empty after the loop, the brackets are balanced

        


```

[Solution](https://github.com/codebasics/data-structures-algorithms-python/blob/master/data_structures/5_Stack/Exercise/balance_paran.py)
