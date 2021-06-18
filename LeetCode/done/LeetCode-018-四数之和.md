#### 四数之和

> 题目描述：给定一个包含 n 个整数的数组 nums 和一个目标值 target，判断 nums 中是否存在四个元素 a，b，c 和 d ，使得 a + b + c + d 的值与 target 相等？找出所有满足条件且不重复的四元组。
>
> 注意：答案中不可以包含重复的四元组。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/4sum/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：双指针法

> 首先，将**nums**排序；然后**first**和**fourth**指针分别从数组的第一个和最后一位开始，**second**和**third**指针分别从**first+1**和**fourth-1**处从两边向内移动，直到**second**不小于**third**，移动过程中**需要判断4个指针所指向的数字之和是否和target相等**，如果相等，则放到结果集**result**里面。  直到遍历到**first**不小于**fourth-2**为止，最后返回结果**result**。

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

public class Solution {


    public static List<List<Integer>> fourSum(int[] nums, int target) {
        if (nums == null || nums.length < 4) {
            return new ArrayList<>();
        }
        if (nums.length == 4 && nums[0] + nums[1] + nums[2] + nums[3] != target) {
            return new ArrayList<>();
        }
        Arrays.sort(nums);
        List<List<Integer>> result = new ArrayList<>();
        for (int first = 0, fourth = nums.length - 1; first < fourth - 2; first++) {
            // 过滤掉重复的
            if (first > 0 && nums[first] == nums[first - 1]) {
                continue;
            }

            while (first < fourth - 2) {
                // 过滤掉重复的
                if (fourth < nums.length - 1 && nums[fourth] == nums[fourth + 1]) {
                    fourth--;
                    continue;
                }
                for (int second = first + 1, third = fourth - 1; second < third; second++) {
                    // 过滤掉重复的
                    if (second > first + 1 && nums[second] == nums[second - 1]) {
                        continue;
                    }
                    while (second < third && nums[first] + nums[second] + nums[third] + nums[fourth] > target) {
                        third--;
                    }
                    if (second != third && nums[first] + nums[second] + nums[third] + nums[fourth] == target) {
                        result.add(new ArrayList<>(Arrays.asList(new Integer[]{nums[first], nums[second], nums[third], nums[fourth]})));
                    }
                }
                fourth--;
            }
            fourth = nums.length - 1;
        }

        return result;
    }

    public static void main(String[] args) {
        int[] nums = new int[]{-3, -1, 0, 2, 4, 5};
        for (List<Integer> integers : fourSum(nums, 0)) {
            for (Integer integer : integers) {
                System.out.print(integer + "/");
            }
            System.out.println();
        }
    }
}
```

【每日寄语】*忠实的守住自己最初的梦想，让生活的每一天都变得有意义。* 

