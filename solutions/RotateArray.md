# 189. Rotate Array

Given an integer array ``nums``, rotate the array to the right by ``k`` steps, where ``k`` is non-negative

#### Example 1:

>**Input:** nums = [1,2,3,4,5,6,7], k = 3
>
>**Output:** [5,6,7,1,2,3,4]
>
>**Explanation:** 
>
>rotate 1 steps to the right: [7,1,2,3,4,5,6]
>
>rotate 2 steps to the right: [6,7,1,2,3,4,5]
>
>rotate 3 steps to the right: [5,6,7,1,2,3,4]


#### Example 2:

>**Input:** nums = [-1,-100,3,99], k = 2
>
>**Output:** [3,99,-1,-100]
>
>**Explanation:** 
>
>rotate 1 steps to the right: [99,-1,-100,3]
>
>rotate 2 steps to the right: [3,99,-1,-100]

---

# Solutions

### Solution 1: 
***Brute force Approach***

```java

public static void rotate(int[] nums, int k) {
        int m =0;
        while(m < k){
            int prev = nums[nums.length-1];
            for (int i = 0; i < nums.length; i++) {
                int temp = nums[i];
                nums[i] = prev;
                prev = temp;
            }
            m++;
        }
}

```

### Solution 2:
***Using a new Array***

```java

public static void rotate(int[] nums, int k) {
        int n = nums.length;
        int[] ans = new int[n];
        for(int i =0;i<nums.length;i++){
            int index = (i+k) % n;  // To begin start index by 0 if it will goes to end index  
            ans[index] = nums[i];
        }

        for(int i =0;i<n;i++){
            nums[i] = ans[i];
        }
    }

```

### Solution 3:

***Without a new Array***

```java

public static void rotate3(int[] nums, int k) {
        int n = nums.length;
         k %=n;   // To find how many times to rotate the array
        reverse(nums,0,n-1);
        reverse(nums,0,k-1);
        reverse(nums,k,n-1);

        System.out.println(Arrays.toString(nums));
    }

    public static void reverse(int[] nums,int start,int end){
        int  i = start;
        int  j = end;
        while(i<j){
            int temp = nums[i];
            nums[i] = nums[j];
            nums[j] = temp;
            i++;
            j--;
        }
    }

```
