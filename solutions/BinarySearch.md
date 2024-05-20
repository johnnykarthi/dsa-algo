
# 704. Binary Search

Given an array of integers ``nums`` which is sorted in ascending order, and an integer ``target``, write a function to search ``target`` in ``nums``. If target exists, then return its index. Otherwise, return ``-1``.

You must write an algorithm with ``O(log n)`` runtime complexity.

#### Example 1:

> Input: nums = [-1,0,3,5,9,12], target = 9
> 
> Output: 4

#### Example 2:

>Input: nums = [-1,0,3,5,9,12], target = 2
>
>Output: -1

---

# Solutions

### *Optimized Solution*

```java

class Solution {
    public int search(int[] nums, int target) {
        
        int start=0;
        int end = nums.length -1;

        while(start<=end){
            int mid = (start + end)/2;
            if(nums[mid] == target){
                return mid;
            } else if (nums[mid] > target) {
                end = mid -1;
            }else{
                start = mid+1;
            }
        }
        return -1;
    }
}

```