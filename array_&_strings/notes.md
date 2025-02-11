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
    - Find the shortest string length - You iterate through the list to determine the length of the shortest string (maxi), as the longest possible prefix cannot exceed this length.
    - Iterate character by character - You use a while loop to iterate from index 0 to maxi - 1, comparing characters across all strings at the same position.
    - Compare each character - Within the loop, you check if all strings have the same character at the current index. If a mismatch is found, you return the substring of any string up to that index.
    - Increment and continue - If no mismatch is found, you continue checking the next character until reaching maxi.
    - Return the prefix - If all characters match up to maxi, return the first string sliced up to start, as it contains the longest common prefix

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
## 121: Best time to buy and sell a stock
### Approach:
	- Use two pointers - Start with slow at day 0 (buy day) and fast at day 1 (sell day) to track potential transactions.
	- Calculate profit - At each step, compute profit = prices[fast] - prices[slow] to see if selling at fast gives a better result.
	- Update max profit - If selling at fast is profitable, update best with the maximum profit found so far.
	- Move the buy day if needed - if the price at fast is lower than slow, update slow = fast to consider a new potential buy day.
	- Return the best profit - Continue until the end of the list, then return best, which holds the highest possible profit. If no profit is possible, return 0
### Runtime:
    - O(N): One while loop that checks over the array

### Solution:
```py
    def maxProfit(self, prices: List[int]) -> int:
        slow = 0
        fast = 1
        best = 0
        while fast < len(prices):
            profit = prices[fast] - prices[slow]
            if prices[slow] < prices[fast]:
                best = max(profit, best)
            else:
                slow = fast
            fast += 1
        return best
```
------------------
## 75. Sort colors
### Appraoch:
    - THIS IS JUST A SIMPLE SELECTION SORT
    - Loop through the array to find the smallest element and move it to its correct position (like selection sort).
	- For each position i, find the minimum value in the remaining unsorted part of the array starting from index i+1.
	- Swap the current element at index i with the smallest element found in the unsorted part of the array.
	- Continue this process until the whole array is sorted.
	- This solution works by sorting the array in-place without using any additional space (except for temporary variables used in swaps).


### Solution:
```py
class Solution:
    def sortColors(self, nums: List[int]) -> None:
        n = len(nums)
        for i in range(n):
            min_index = i
            for j in range(i + 1, n):
                if nums[j] < nums[min_index]:
                    min_index = j
            nums[i], nums[min_index] = nums[min_index], nums[i]
        print(nums)
```

### runtime:
    - o(n^2)

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