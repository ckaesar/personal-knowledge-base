#### 最大子序和

> 题目描述：给定一个整数数组 nums ，找到一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
>链接：https://leetcode-cn.com/problems/maximum-subarray/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：动态规划

> 首先，初始化**max**和**sum**都为**nums**的第一个元素的值，然后从第2位开始遍历数组：
>
> - 当`sum <= 0`时，**sum**设置为当前索引为的值，也就是抛弃之前累加的值；
> - 当`sum > 0`时，**sum**加上当前索引位的值，累加；
> - 然后每次便利时**max**取**max**和**sum**的较大者。
>
> 最后，返回**max**即为最后结果。

```java
public class LeetCode_053 {
    public static int maxSubArray(int[] nums) {
        int max = nums[0], sum = nums[0];
        for (int i = 1; i < nums.length; i++) {
            if (sum <= 0) {
                sum = nums[i];
            } else {
                sum = sum + nums[i];
            }
            max = Math.max(max, sum);
        }
        return max;
    }

    public static void main(String[] args) {
        int[] nums = new int[]{-2, 1, -3, 4, -1, 2, 1, -5, 4};
        System.out.println(maxSubArray(nums));
    }
}
```

> 【每日寄语】 *在忙碌的日子里，要学会每天给自己找一个开心的理由，哪怕只是，阳光很暖，电量很满。*

