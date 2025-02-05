## Leetcode Name
### Apprach:


------------------

## 13. Roman to Integer
### Apprach:
    - Create a mapping – Define a dictionary romans to store the values of Roman numeral symbols.
	- Initialize total – Start with total = 0 to accumulate the integer value.
	- Check for subtraction cases – Loop through the string, and if the current numeral is smaller than the next one, subtract its value (e.g., IV = 4). Otherwise, add it.
	- Handle the last character – Since the loop stops before the last character, add its value separately at the end.
	- Return the total – After processing all characters, return the computed integer value
### Solution:
```py
class Solution:
    def romanToInt(self, s: str) -> int:
        romans = {
            "I": 1,
            "V": 5,
            "X": 10,
            "L": 50,
            "C": 100,
            "D": 500,
            "M": 1000
        }

        total = 0
        for i in range(len(s) - 1):
            if romans[s[i]] < romans[s[i + 1]]:
                total -= romans[s[i]]
            else:
                total += romans[s[i]]
        return total + romans[s[-1]]
```

### runtime:
    - o(n), singe for loop to check over each char in the roman word

------------------