# 两数之和（easy）

[TOC]



## 暴力枚举

  ### 代码

```java
class Solution {
    public static int[] twoSum(int[] nums, int target) {
        int[] result = new int[]{0, 1};
        if(nums.length==2){
            return result;  
        }
        for (int i = 0; i < nums.length; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[i] + nums[j] == target) {
                    result[0] = i;
                    result[1] = j;
                    return result;  
                }
            }
        }
      return result; // 要有返回值
    }
}
```

###   复杂度分析

​	时间复杂度：O(N^2)O(N2)，其中 NN 是数组中的元素数量。最坏情况下数组中任意两个数都要被匹配一次。

​	空间复杂度：O(1)O(1)。



##哈希表

### 	代码

```java
import java.util.HashMap;
import java.util.Map;

public class Main {
    public static void main(String[] args) {
        int[] nums = {2,7,10,11};
        int target = 9;
        Map<Integer, Integer> hashtable = new HashMap<Integer, Integer>();
        hashtable.put(nums[0], 0);
        for (int i = 0; i < nums.length; ++i) {
            if (hashtable.containsKey(target - nums[i])) {
                int x = hashtable.get(target-nums[i]);
                System.out.println(x+","+i); 
            }
            hashtable.put(nums[i], i);
         }
        
     }
    } 

```

**设第i个数是x，通过查找前面的数有没有target-x，所以需要遍历一次**

### 复杂度分析

时间复杂度：O(N)O(N)，其中 NN 是数组中的元素数量。对于每一个元素 x，我们可以 O(1)O(1) 地寻找 target - x。

空间复杂度：O(N)O(N)，其中 NN 是数组中的元素数量。主要为哈希表的开销。






