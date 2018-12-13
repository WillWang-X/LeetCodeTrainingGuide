# 75. Sort Colors


Given an array with n objects colored red, white or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white and blue.

Here, we will use the integers 0, 1, and 2 to represent the color red, white, and blue respectively.

Note: You are not suppose to use the library's sort function for this problem.

```
Example:

Input: [2,0,2,1,1,0]
Output: [0,0,1,1,2,2]
```

Follow up:

* A rather straight forward solution is a two-pass algorithm using counting sort. First, iterate the array counting number of 0's, 1's, and 2's, then overwrite array with total number of 0's, then 1's and followed by 2's.
* Could you come up with a one-pass algorithm using only **constant** space?


## Idea 

[0,1,2,0,1,2,0,1,2,1,1,1,1]

* The first idea I come up with is that we can just sort the nums, with sorting algorithms, which takes O(nlogn).
* At second thought, we can start from the definition. I mean swap 0 to the start and swap 1 to the end, which only takes O(n).
* Specifically, we can use two pointer to point the position we are going to take a '0' and '2'. We itrate the list and every time we meet a '0', we swap it to the start and update our pointer position; every time we meet a '2', we swap it to the end and update our pointer position.


For example, 

```
[2,0,2,1,1,0]

   i
[0,2,2,1,1,0]
   h      
 			 t
```
注意：

i 移动的情况有两种：

1.  遇到`1`，i往右移动一个。
2.  与`head` 交换完，也要移动，因为交换完，此时nums[i] 不是`0`就是`1`。(容易错，如果此时不移动`i`, 想想为什么 `[2,0,2,1,1,0]` -> `[1,1,2,2,0,0]`)
   
zeroPointer = the position we are going to take '0'  
twoPoointer = the position we are going to take '2'

Corner case:

```
[0]
[0, 1]
[0, 0]
[1]
```

## Code 

Python: 

``` python 
# Time: O(n)
# Space: O(1)
# 75. Sort colors

class Solution(object):
    def sortColors(self, nums):
        """
        :type nums: List[int]
        :rtype: void Do not return anything, modify nums in-place instead.
        """
        def is_head(num):
            return num == 0

        def is_tail(num):
            return num == 2

        head, tail = 0, len(nums) - 1
        i = 0 
        
        while i <= tail:
            if is_head(nums[i]):
                nums[i], nums[head] = nums[head], nums[i]
                head += 1
                i += 1
            elif is_tail(nums[i]):
                nums[i], nums[tail] = nums[tail], nums[i]
                tail -= 1
            else:
                i += 1  
```

Java: 

``` java
// Remember the swap(a, b) in java is a = b ^ a ^ (b = a)

class Solution {
    public void sortColors(int[] nums) {
        int head = 0, tail = nums.length - 1;
        int i = 0;
        while (i <= tail){
            if(nums[i] == 0){
                nums[i] = nums[head] ^ nums[i] ^ (nums[head] = nums[i]); 
                i += 1;
                head += 1;
            }
            else if(nums[i] == 2){
                nums[i] = nums[tail] ^ nums[i] ^ (nums[tail] = nums[i]);
                tail -= 1;
            }
            else{
                i += 1;
            }
        }
        
        
    }
}
```

Javascript:

``` javascript 
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var sortColors = function(nums) {
    let head = 0; 
    let tail = nums.length - 1;
    let i = 0;
    
    while (i <= tail){
        if (nums[i] === 0){
            [nums[i], nums[head]] = [nums[head], nums[i]]
            head += 1
            i += 1
        }
        else if(nums[i] === 2){
            [nums[i], nums[tail]] = [nums[tail], nums[i]]
            tail -= 1
        }
        else{
            i += 1
        }
    }
};
```