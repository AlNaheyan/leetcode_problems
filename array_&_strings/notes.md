## Leetcode Name
### Apprach:


------------------
## 2239: Find closest number to zero
### Approach: 
    - I set closest to be a large number for easier detection and get's replaced by the abs() number. 
    - I also have another variable to save the actual number from array
    - Start a for loop to interate thru the array
    - If the abs() of that nuber is less than closest, closest becomes the abs() of that num and indexd becomes the actual num. 
    - However, if the abs() of num (lowest) is equal to closest, the actaul number is defined by the largest from real num and abs() of num.
    - At the end, we return the indexd since that's the real num

### Run time:
    - O(N) because we interate thru the array checking for all nums

### Solution:
```py
def findClosestNumber(self, nums: List[int]) -> int:
        indexd = 0
        closest = 999999999
        for num in nums:
            if abs(num) < closest:
                closest = abs(num)
                indexd = num
            elif (abs(num) == closest):
                indexd = max(indexd, num)
        return indexd
```
------------------
## 977: Squares of a Sorted Array
### Approach:
    - Start with an empty array to store the squared nums
    - loop thru the array and square each num by it self
    - at the end, return sorted() of that squared num array

### Run Time:
    - O(N), iterating thru o(N) + sorted() function takes o(N), O(N+N) = O(N)
### Solution:
```py
    def sortedSquares(self, nums: List[int]) -> List[int]:
        squared = []
        for num in nums:
            squared.append(num * num)
        return sorted(squared)
```

------------------
## Longest common Prefix
### Approach: 
    - Find the shortest string length – You iterate through the list to determine the length of the shortest string (maxi), as the longest possible prefix cannot exceed this length.
    - Iterate character by character – You use a while loop to iterate from index 0 to maxi - 1, comparing characters across all strings at the same position.
    - Compare each character – Within the loop, you check if all strings have the same character at the current index. If a mismatch is found, you return the substring of any string up to that index.
    - Increment and continue – If no mismatch is found, you continue checking the next character until reaching maxi.
    - Return the prefix – If all characters match up to maxi, return the first string sliced up to start, as it contains the longest common prefix

### Runtime:
    - O(N*N) = O(N^2) because we have 2 iteration, a for loop inside a while loop. 

### Solution:
```py
    def longestCommonPrefix(self, strs: List[str]) -> str:
        maxi = float('inf')
        for s in strs:
            if len(s) < maxi:
                maxi = len(s)
        print(maxi)

        start = 0
        while start < maxi:
            for s in strs:  
                if s[start] != strs[0][start]:
                    return s[:start]
            start += 1
        return strs[0][:start]
```


------------------

