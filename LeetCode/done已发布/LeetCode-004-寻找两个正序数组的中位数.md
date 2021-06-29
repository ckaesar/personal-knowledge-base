#### 寻找两个正序数组的中位数

> 题目描述：给定两个大小分别为 m 和 n 的正序（从小到大）数组 nums1 和 nums2。请你找出并返回这两个正序数组的 中位数 。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
>链接：https://leetcode-cn.com/problems/median-of-two-sorted-arrays/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：有序数组合并

> 将2个数组按顺序合并到一个大数组里面，2个数组都只会遍历一次。然后在大数组中获取中位数。

###### 解法二：待完成

> 思考怎么在 时间复杂度为 `O(log (m+n))`下完成？

```java
public class Solution {
    public static double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int[] allNums = new int[nums1.length + nums2.length];
        int i = 0, j = 0, x = 0;
        int num1 = Integer.MAX_VALUE, num2 = Integer.MAX_VALUE;
        for (; i < nums1.length || j < nums2.length; ) {
            if (i < nums1.length) {
                num1 = nums1[i];
            }
            if (j < nums2.length) {
                num2 = nums2[j];
            }
            if (num1 < num2) {
                allNums[x] = num1;
                i++;
            } else {
                allNums[x] = num2;
                j++;
            }
            x++;
            num1 = Integer.MAX_VALUE;
            num2 = Integer.MAX_VALUE;
        }
        int count = nums1.length + nums2.length;
        if (count % 2 == 1) {
            return allNums[count / 2];
        } else {
            return ((double) (allNums[count / 2 - 1] + allNums[count / 2])) / 2;
        }
    }

    public static void main(String[] args) {
        int[] nums1 = new int[]{1, 2};
        int[] nums2 = new int[]{3, 4};
        System.out.println(findMedianSortedArrays(nums1, nums2));
    }
}
```
