# Exp.No:32  
## CONVERSION OF INFIX TO POSTFIX

---

### AIM  
To write a Python program to convert a given Infix expression to a Postfix expression by following the precedence and associative rules. The input expression contains only Division, Subtraction, and Bitwise AND operators. A dictionary is used to set the priority for operators, and a set is used to hold the operators used in the given expression.

---

### ALGORITHM

1. **Start the program.**
2. **Initialise an empty stack** and an empty output string.
3. **Iterate through each character** in the infix expression:
   - If the character is **not an operator**, append it directly to the output string.
   - If the character is an **open parenthesis '('**, push it onto the stack.
   - If the character is a **close parenthesis ')'**, pop from the stack and append to the output until encountering a left parenthesis '('.
   - If the character is an **operator**, handle it based on precedence:
     - While there’s an operator at the top of the stack with higher or equal precedence, pop the stack and append those operators to the output.
     - Push the current operator onto the stack.
4. **Use a priority dictionary** to define operator precedence, ensuring higher precedence operators are placed before lower precedence ones.
5. Once the expression is fully processed, continue popping any remaining operators from the stack and append them to the output.
6. **Return the final postfix expression.**
7. **Print the result.**
8. **End the program.**

---

### PROGRAM

```python
def infix_to_postfix(expression):

    precedence = {'%': 2, '*': 2, '|': 1}
    operators = {'%', '*', '|'}
    
    stack = []
    postfix = ''
    
    for char in expression:
        if char.isalnum():  
            postfix += char
        elif char == '(':
            stack.append(char)
        elif char == ')':
            
            while stack and stack[-1] != '(':
                postfix += stack.pop()
            stack.pop()  
        elif char in operators:
            while (stack and stack[-1] in operators and
                   precedence[char] <= precedence[stack[-1]]):
                postfix += stack.pop()
            stack.append(char)


    while stack:
        postfix += stack.pop()
    
    return postfix


expr = input()

print("infix notation: ", expr)
postfix_expr = infix_to_postfix(expr)
print("postfix notation: ", postfix_expr)


```

### OUTPUT

<img width="930" height="190" alt="image" src="https://github.com/user-attachments/assets/faec3fea-9218-40ce-ac13-91f016b8eaf9" />


### RESULT

Successfully converted an infix expression with subtraction and multiplication into postfix notation using a dictionary for precedence and a set for operator validation.
