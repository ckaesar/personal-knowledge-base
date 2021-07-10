#### 只出现一次的数字

> 题目描述：给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。
>
> 说明：
>
> 你的算法应该具有线性时间复杂度。 你可以不使用额外空间来实现吗？
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/single-number/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：二进制运算

> 利用二进制运算的异或运算操作符`^`，异或运算就是二进制位上相同位置的数字如果相同则为0，如果不同则为1，即`0^0=0，1^0=1，0^1=1，1^1=0`。所以通过遍历一遍数组，把每一个数字进行异或运算，由于重复的数字异或之后都是0，最后的结果就是只出现了一次的元素。

```java
public class LeetCode_136 {
    public static int singleNumber(int[] nums) {
        int result = 0;
        for (int i = 0; i < nums.length; i++) {
            result ^= nums[i];
        }
        return result;
    }

    public static void main(String[] args) {
        int[] nums = new int[]{2, 2, 1};
        System.out.println(singleNumber(nums));
    }
}
```

> 【每日寄语】 *你的负担将变成礼物，你受的苦将照亮你的路。* 

