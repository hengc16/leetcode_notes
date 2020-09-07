# 1. Two Sum

Given an array of integers `nums` and an integer `target`, return _indices of the two numbers such that they add up to `target`_.

You may assume that each input would have _**exactly**_ **one solution**, and you may not use the _same_ element twice.

You can return the answer in any order.

**Example 1:**

```text
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Output: Because nums[0] + nums[1] == 9, we return [0, 1].
```

**Example 2:**

```text
Input: nums = [3,2,4], target = 6
Output: [1,2]
```

**Example 3:**

```text
Input: nums = [3,3], target = 6
Output: [0,1]
```

**Constraints:**

* `2 <= nums.length <= 105`
* `-109 <= nums[i] <= 109`
* `-109 <= target <= 109`
* **Only one valid answer exists.**

### **思路：**

* nest loop，对应每个ele用O\(n）时间去找它是否有对应的元素相加等于target
* 用空间换时间, 把见过的ele和它对应的index都存起来，调用是O\(1\)的，但是space变O\(n\)了

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        if(nums == null || nums.length == 0) return new int[]{};
        Map<Integer, Integer> map = new HashMap<>();
        for(int i = 0; i < nums.length; i++) {
            if(map.containsKey(target - nums[i])) {
                return new int[] {map.get(target-nums[i]), i};
            }else{
                map.put(nums[i], i);
            }
        }
        return new int[]{};
    }
}
```



