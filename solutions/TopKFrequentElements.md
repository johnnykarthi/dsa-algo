# 347. Top K Frequent Elements

Given an integer array nums and an integer k, return the k most frequent elements. You may return the answer in any order.

#### Example 1:

>**Input:** nums = [1,1,1,2,2,3], k = 2
>
>**Output:** [1,2]

#### Example 2:

>**Input:** nums = [1], k = 1
>
>**Output:** [1]


---

# Solutions

### *Optimized Solution*

```java

class Solution {
    public int[] topKFrequent(int[] nums, int k) {

        Map<Integer,Integer> map = new HashMap<>();
        Map<Integer,List<Integer>> freq = new HashMap<>();
        int[] ans = new int[k];
        int n =0;

        for (int num : nums) {
            if (!map.containsKey(num)) {
                map.put(num, 1);
            } else {
                map.put(num, map.get(num) + 1);
            }
        }

        for(int num:map.keySet()){
                List<Integer> temp= freq.getOrDefault(map.get(num),new ArrayList<>());
                temp.add(num);
                freq.put(map.get(num),temp);
        }
        
        for(int i = nums.length;i > 0;i--){
            if(freq.containsKey(i)){
                List<Integer> temp = freq.get(i);
                for(int j =0;j<temp.size() && n < k;j++){
                    ans[n++] = temp.get(j);
                }
            }
        }
        return ans;
    }
}

```
