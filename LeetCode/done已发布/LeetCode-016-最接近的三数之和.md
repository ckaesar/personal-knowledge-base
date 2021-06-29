#### 最接近的三数之和

> 题目描述：给定一个包括 n 个整数的数组 nums 和 一个目标值 target。找出 nums 中的三个整数，使得它们的和与 target 最接近。返回这三个数的和。假定每组输入只存在唯一答案。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
>链接：https://leetcode-cn.com/problems/3sum-closest/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：双指针法

> 首先将数组排序，获取一个初始的结果**difference**，然后第一个数字**first**从第一个数字开始遍历，第二个数字**second**和第三个数字**third**分别从之后的数组中从两边向中间遍历，遍历过程中如果与**target**比**difference**更接近，则更新**difference**，直到遍历完成，返回**difference**对应的**result**。
>
> 说明：解法和 **LeetCode-015-三数之和** 这个题目的解法类似，可对比参考。

```java
import java.util.Arrays;

public class Solution {
    /**
     * 双指针法
     * @param nums
     * @param target
     * @return
     */
    public static int threeSumClosest(int[] nums, int target) {
        if (nums.length == 3) {
            return nums[0] + nums[1] + nums[2];
        }
        Arrays.sort(nums);

        int result = nums[0] + nums[1] + nums[2];
        int difference = Math.abs(result - target);
        // 第一个数字
        for (int first = 0; first < nums.length - 2; first++) {
            //过滤掉重复的
            if (first > 0 && nums[first] == nums[first - 1]) {
                continue;
            }
            for (int second = first + 1; second < nums.length - 1; second++) {
                if (second > first + 1 && nums[second] == nums[second - 1]) {
                    // 过滤掉重复的
                    continue;
                }

                int third = nums.length - 1;
                while (second < third) {
                    // 当3个数之和比当前的result更接近时，更新result
                    if (Math.abs(nums[first] + nums[second] + nums[third] - target) < difference) {
                        result = nums[first] + nums[second] + nums[third];
                        difference = Math.abs(result - target);
                    }
                    third--;
                }
            }
        }
        return result;
    }

    public static void main(String[] args) {
        int[] nums = new int[]{0, 1, 2, 3, 4, 5, 6};
        System.out.println(threeSumClosest(nums, 2));
    }
}
```

> 【每日寄语】*健康自己就是最大的关爱别人。* 
