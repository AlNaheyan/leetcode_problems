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

## 242. Valid Anagram
### Apprach:
	- Check if s and t have the same length. If not, return False immediately since they can’t be anagrams.
	- Use a hash table (tab) to count the occurrences of each character in s.
	- Loop through t and decrease the count of each character in tab. If a character is missing or its count drops below zero, return False.
	- If all character counts balance out to zero, return True, meaning s and t are anagrams

### solution:
```py
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False

        tab = {}
        
        for char in s:
            if char not in tab:
                tab[char] = 1
            else:
                tab[char] += 1
        print(tab)
        for char in t:
            if char not in tab:
                return False
            tab[char] -= 1
            if tab[char] < 0:
                return False
        return True
```

### runtime:
    - o(n)

------------------

## 383. ransom note
### Approach:
    - Use a dictionary to count magazine letters: Create a dictionary (dict) to store the frequency of each letter in magazine.
	- Populate the dictionary: Iterate through magazine, increasing the count of each letter in dict.
	- Check ransomNote letters: Iterate through ransomNote and check if each letter exists in dict with a count greater than zero.
	- Reduce count or remove letters: If a letter is found, decrease its count in dict. If a letter’s count reaches zero, remove it.
	- Return result: If all letters in ransomNote are found in dict, return True; otherwise, return False.


### solution:
```py
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:      
        dict = {}
        for letter in magazine:
            if letter in dict:
                dict[letter] += 1
            else:
                dict[letter] = 1
        
        for letter in ransomNote:
            if letter not in dict:
                return False
            elif dict[letter] == 1:
                del dict[letter]
            else:
                dict[letter] -= 1
        return True
```

### runtime: 
    - o(n+m)


------------------