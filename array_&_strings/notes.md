## Leetcode Name
#### Apprach:


------------------


## 2239: Find closest number to zero

#### Approach: 
    - I set closest to be a large number for easier detection and get's replaced by the abs() number. 
    - I also have another variable to save the actual number from array
    - Start a for loop to interate thru the array
    - If the abs() of that nuber is less than closest, closest becomes the abs() of that num and indexd becomes the actual num. 
    - However, if the abs() of num (lowest) is equal to closest, the actaul number is defined by the largest from real num and abs() of num.
    - At the end, we return the indexd since that's the real num

Run time:
    - O(N) because we interate thru the array checking for all nums

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

------------------
## 977: Squares of a Sorted Array
#### Apprach:
    - Start with an empty array to store the squared nums
    - loop thru the array and square each num by it self
    - at the end, return sorted() of that squared num array

#### Time Complexity:
    - O(N), iterating thru o(N) + sorted() function takes o(N), O(N+N) = O(N)


------------------

