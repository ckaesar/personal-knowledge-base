#### 存在重复元素 II

> 题目描述：给定一个整数数组和一个整数 k，判断数组中是否存在两个不同的索引 i 和 j，使得 nums [i] = nums [j]，并且 i 和 j 的差的 绝对值 至多为 k。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
>链接：https://leetcode-cn.com/problems/contains-duplicate-ii/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：暴力破解法

> 双重循环，外层循环i的范围是`0~nums.length-2`，内层循环j的范围是`i+1~(nums.length且j<=i+k)`，循环体内的判断条件就是2个值相等，如果相等，则返回true。循环结束后，如果没有符合条件的整数对，则返回false。

```java
public class LeetCode_219 {
    /**
     * 暴力破解法
     * @param nums
     * @param k
     * @return
     */
    public static boolean containsNearbyDuplicate(int[] nums, int k) {
        if (nums == null || nums.length < 2) {
            return false;
        }
        for (int i = 0; i < nums.length - 1; i++) {
            for (int j = i + 1; j < nums.length && j <= i + k; j++) {
                if (nums[i] == nums[j] && (j - i) <= k) {
                    return true;
                }
            }
        }
        return false;
    }

    public static void main(String[] args) {
        int[] nums = new int[]{1, 2, 3, 1};
        System.out.println(containsNearbyDuplicate(nums, 3));
    }
}
```

> 【每日寄语】 *努力的意义就是：以后的日子里，放眼望去，全都是自己喜欢的东西。* 

