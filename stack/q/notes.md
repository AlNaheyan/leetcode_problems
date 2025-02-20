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
