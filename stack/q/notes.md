## Leetcode Name
### Apprach:


------------------

## Leetcode Name
### Apprach:
    - Use a stack to track scores: Maintain a list (stack) to store valid scores as you process the operations.
	- Handle operations based on rules:
	•	If 'C', remove the last score using pop().
	•	If 'D', double the last score and add it to the stack.
	•	If '+', sum the last two scores and add the result to the stack.
	•	Otherwise, convert the string to an integer and add it to the stack.
	- Return the sum of all scores: After processing all operations, return the sum of the stack to get the final score.

### Solution:
```py
class Solution:
    def calPoints(self, operations: List[str]) -> int:
        stack = []
        for i in operations:
            if i == 'C':
                stack.pop()
            elif i == 'D':
                stack.append(stack[-1] * 2)
            elif i == '+':
                stack.append(stack[-1] + stack[-2])
            else:
                stack.append(int(i))
        return sum(stack)
```
### runtime:
    - o(n)

------------------

## 20. valid parenthesis
### Approach:
    - Use a stack to track open brackets: Create an empty list (open) to push open brackets as you encounter them in the string.
	- Match closing brackets with the stack: For each closing bracket, check if the stack is empty. If it is, return False (no corresponding open bracket). Otherwise, pop the stack and ensure the popped open bracket matches the corresponding type of closing bracket.
	- Check if all brackets are matched: After iterating through the string, if the stack is empty, return True (all brackets are valid). If the stack still contains open brackets, return False.
	- Use a dictionary for matching pairs: Use a dictionary (uhh) to map each closing bracket to its corresponding opening bracket for quick lookups.
### Solution:
```py
class Solution:
    def isValid(self, s: str) -> bool:
        open = []

        uhh = {')': '(', '}': '{', ']': '['}

        for i in s:
            if i in uhh.values():
                open.append(i)
            elif i in uhh:
                if len(open) == 0:
                    return False
                first = open.pop()
                if first != uhh[i]:
                    return False
                    
        if len(open) == 0:
            return True
        else:
            return False
            

```

### runtime:
    - o(n)

------------------
