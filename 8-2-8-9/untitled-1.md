# 283. Move Zeroes

**Example 1:**

```text
Input: nums = [0,1,0,3,12]
Output: [1,3,12,0,0]
```

**Example 2:**

```text
Input: nums = [0]
Output: [0]
```

### Thinking: 

quick sort , povit is != 0, swap if != 0

### Steps:

1. iterate the array 
2. if not 0 , swap

```java
 public void moveZeroes(int[] nums) {
        int j = 0;
        for(int i = 0 ; i < nums.length ; i++){
           if(nums[i] != 0) {
               int tmp = nums[i];
               nums[i] = nums[j];
               nums[j] = tmp;
               j++;
           }
       }
    }
```

