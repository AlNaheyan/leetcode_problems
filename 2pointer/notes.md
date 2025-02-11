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
## 88. Merge sorted array
### Approach:
    - Start merging from the end of nums1, using three pointers: p1 at m-1 (last valid element of nums1), p2 at n-1 (last element of nums2), and p at m+n-1 (last position of nums1).
	- Compare elements at p1 and p2, placing the larger one at position p, then move the respective pointer left.
	- Repeat until either p1 or p2 runs out of elements.
	- If p2 still has elements left, copy the remaining elements of nums2 into nums1.
	- Since merging is done in-place, the array remains sorted without extra space

### Solution:
```py
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        p1 = m
        tot = m + n
        p2 = 0
        while tot > p1:
            nums1[p1] = nums2[p2]
            p1 += 1
            p2 += 1
        return nums1.sort()
```
### runtime: 
    - o(n)
------------------
## 167. two sum II - input array is sorted
### Approach:
    - Use two pointers, left starting at the beginning and right at the end of the sorted array.
	- Compute the sum of numbers[left] and numbers[right].
	- If the sum is less than the target, move left rightward; if it’s greater, move right leftward.
	- If the sum equals the target, return the 1-based indices [left + 1, right + 1].
	- Repeat until the correct pair is found (guaranteed to exist).

### Solution:
```py
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        left = 0
        right = len(numbers) - 1
        while left < right:
            total = numbers[left] + numbers[right]
            if total < target:
                left += 1
            elif total > target:
                right -= 1
            else:
                return [left + 1 , right + 1]
```

### runtime:
    - o(n)
    
------------------
## 344. reverse string
### Apprach:
	- Two pointers: Start with two pointers: one (p1) at the beginning of the string and the other (p2) at the end of the string.
	- Swap elements: While p1 is less than p2, swap the elements at p1 and p2.
	- Move pointers: After each swap, increment p1 and decrement p2 to move towards the center of the string.
	- Repeat the process until the pointers meet or cross, meaning the string has been reversed.
	- This approach modifies the input array s in place, requiring O(1) extra memory

### solution:
```py
class Solution:
    def reverseString(self, s: List[str]) -> None:
        p1 = 0
        p2 = len(s) - 1
        while p2 > p1:
            s[p1], s[p2] = s[p2], s[p1]
            p1 += 1
            p2 -= 1
```

### runtime:
    - o(n)
    
------------------

