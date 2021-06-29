#### 两数之和

> 题目描述：给定一个整数数组 nums 和一个整数目标值 target，请你在该数组中找出 和为目标值 target  的那 两个 整数，并返回它们的数组下标。
>
> 你可以假设每种输入只会对应一个答案。但是，数组中同一个元素在答案里不能重复出现。
>
> 你可以按任意顺序返回答案。 
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/two-sum
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：暴力破解法

> 暴力破解法，就是通过双重循环的方式，得到结果后立刻返回。是我最容易想到的也是比较懒的解法。

###### 解法二：利用Map

> 利用Map的containsKey方法， 虽然也会遍历一层，但是效率应该比暴力破解法更高一些。

```java
package com.kaesar.leetcode;

import java.util.HashMap;
import java.util.Map;

class Solution {
    /**
     * 方法一：暴力法
     *
     * @param nums
     * @param target
     * @return
     */
    public static int[] twoSum(int[] nums, int target) {
        int[] result = new int[2];
        finish:
        for (int i = 0; i < nums.length; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[i] + nums[j] == target) {
                    result[0] = i;
                    result[1] = j;
                    break finish;
                }
            }
        }
        return result;
    }

    /**
     * 方法二：用Map
     *
     * @param nums
     * @param target
     * @return
     */
    public static int[] twoSum2(int[] nums, int target) {
        Map<Integer, Integer> oneMap = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            oneMap.put(nums[i], i);
        }
        for (int i = 0; i < nums.length; i++) {
            int two = target - nums[i];
            if (oneMap.containsKey(two) && oneMap.get(two) != i) {
                return new int[]{oneMap.get(two), i};
            }
        }
        throw new RuntimeException("找不到");
    }

    public static void main(String[] args) {
        int[] nums = new int[]{2, 4, 1, 22, 91, 23};
        int target = 26;
        int[] ints = twoSum(nums, target);
        System.out.println(ints[0] == 1);
        System.out.println(ints[1] == 3);

        int[] ints2 = twoSum2(nums, target);
        System.out.println(ints2[0] == 1 || ints2[0] == 3);
        System.out.println(ints2[1] == 3 || ints2[1] == 1);
    }
}
```
