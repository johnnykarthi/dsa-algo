# 238. Product of Array Except Self

Given an integer array ``nums``, return an array ``answer`` such that ``answer[i]`` is equal to the product of all the elements of ``nums`` except ``nums[i]``.

The product of any prefix or suffix of ``nums`` is **guaranteed** to fit in a **32-bit** integer.

You must write an algorithm that runs in ``O(n)`` time and without using the division operation.

#### Example 1:

>**Input:** nums = [1,2,3,4]
>
>**Output:** [24,12,8,6]
>



#### Example 2:

>**Input:** nums = [-1,1,0,-3,3]
>
>**Output:** [0,0,9,0,0]


---

# Solutions

### Solution 1: 
***Brute force Approach***

```java

public static int[] productExceptSelf(int[] nums) {

        int[] ans = new int[nums.length];

        for(int i =0;i<nums.length;i++){
            int product = 1;
            for(int j =0;j<nums.length;j++){
                if(i != j){
                    product*=nums[j];
                }
            }
            ans[i] = product;
        }
}
```

### Solution 2:
***Using Division***

```java

public static int[] productExceptSelf(int[] nums) {

        int[] ans = new int[nums.length];
        int count = 0;
        int product = 1;
        for(int num:nums){
            if(num == 0) {
                count++;
            }
            else{
                product*=num;
            }
        }

        if(count > 1){
            return ans;
        }

        for(int i =0;i<nums.length;i++){
            if(nums[i] == 0){
                ans[i]= product;
            } else if(count == 0){
                ans[i] = product/nums[i];
            }else{
                ans[i] = 0;
            }
        }

        return ans;
}

```

### Solution 3:

***With prefix and suffix array***

```java

public static int[] productExceptSelf(int[] nums) {

        int[] ans = new int[nums.length];

        int[] prefix = new int[nums.length];
        int[] suffix = new int[nums.length];
        int pre =1;
        int suf = 1;

        for(int i=0;i<nums.length;i++){
            pre *=nums[i];
            prefix[i] = pre;
        }

        for(int i=nums.length-1;i>=0;i--){
            suf *=nums[i];
            suffix[i] = suf;
        }

        ans[0] = suffix[1];
        ans[nums.length-1] = prefix[nums.length-2];

        for(int i= 1;i<nums.length-1;i++){
            ans[i] = prefix[i-1] * suffix[i+1];
        }

        return ans;
}

```

### Solution 4:

***Without prefix and suffix array***

```java

public static int[] productExceptSelf(int[] nums) {

        int[] ans = new int[nums.length];
        int pre = 1;
        for(int i =0;i<nums.length;i++){
            ans[i] = pre;
            pre*=nums[i];
        }
        int suf =1;
        for(int i = nums.length-1;i>=0;i--){
            ans[i] *= suf;
            suf*= nums[i];
        }

        return ans;
}

```