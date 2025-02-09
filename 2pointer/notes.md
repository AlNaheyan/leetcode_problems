## 392. Is Subsequence
### Approach: 
    - Since I knew we can easy iterate thru both strings w/ 2 pointers, I set 2 pointers and started from 0.
    - I also set counter to 0 to check over the sequences
    - Start the while loop, conditionally checking p1 being less than the length of s and p2 being less than length t since we dont want to go out of index. Refering to us starting with 0 and len() starts from 1.
    - Then we check if the letter in s and letter in t are the same. If so, we increament p1 and counter since its same.
    - in the while loop, we'll automatically increment p2 since we are essentially checking this even if we letter in s equal or not.
    - At the end, we return if the counter is the same as p1 since they should be in sequence and return a boolean. 

### Time Complexity:
    - O(N) since we are iterating through both loop once during the while loop and we checking len(t). So O(N+N) = O(N)

### solution:
```py
class Solution:
    def isSubsequence(self, s: str, t: str) -> bool:
        p1 = 0
        p2 = 0
        counter = 0

        while p1 < len(s) and p2 < len(t):
            if s[p1] == t[p2]:
                p1 += 1
                counter += 1
            p2 += 1
        return (counter) == len(s)
```

### runtime:
    - o(n)
------------------

## 125. Valid Palidrome
### Approach:
    - Handle edge case – If the string is just a space, return True immediately.
	- Use two pointers – Set L at the start and R at the end of the string to compare characters.
	- Skip non-alphanumeric characters – Move L forward and R backward if they point to non-alphanumeric characters.
    - Compare characters – Convert both characters to lowercase and check if they match. If they don’t, return False.
	- Return result – If all valid characters match, return True after checking the entire string

### Solution:
```py
class Solution:
    def isPalindrome(self, s: str) -> bool:
        if s == " ":
            return True

        L = 0
        R = len(s) - 1
        isPal = True

        while L < R:
            if not (s[L].isalnum()):
                L += 1
                continue
            if not (s[R].isalnum()):
                R -= 1
                continue
            if s[L].lower() != s[R].lower():
                return False
            L += 1
            R -= 1
        return isPal
```

### runtime:
    - o(n)

------------------

	•	Check if s and t have the same length. If not, return False immediately since they can’t be anagrams.
	•	Use a hash table (tab) to count the occurrences of each character in s.
	•	Loop through t and decrease the count of each character in tab. If a character is missing or its count drops below zero, return False.
	•	If all character counts balance out to zero, return True, meaning s and t are anagrams

