#### 合并两个有序数组

> 题目描述：给你两个有序整数数组 nums1 和 nums2，请你将 nums2 合并到 nums1 中，使 nums1 成为一个有序数组。
>
> 初始化 nums1 和 nums2 的元素数量分别为 m 和 n 。你可以假设 nums1 的空间大小等于 m + n，这样它就有足够的空间保存来自 nums2 的元素。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/merge-sorted-array/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：数组遍历

> 同时遍历2个数组，从大到小开始遍历，nums1数组的最大的索引位为maxIndex，记录当前的值分别为num1和num2，当前索引为分别为m-1和n-1，遍历过程：
>
> - 如果num1大于num2，则更新nums1数组maxIndex位置的值为num1，然后m减一，maxIndex减一；
> - 如果num1不大于num2，则更新nums1数组maxIndex位置的值为num2，然后n减一，maxIndex减一；
> - 遍历结束的条件是m和n都不大于0，即2个数组都遍历结束。
>
> 遍历完成后，num1即为合并后的结果。

```java
import java.util.Arrays;

public class LeetCode_088 {
    public static void merge(int[] nums1, int m, int[] nums2, int n) {
        int maxIndex = m + n - 1;
        while (m > 0 || n > 0) {
            int num1 = Integer.MIN_VALUE, num2 = Integer.MIN_VALUE;
            if (m > 0) {
                num1 = nums1[m - 1];
            }
            if (n > 0) {
                num2 = nums2[n - 1];
            }
            if (num1 > num2) {
                nums1[maxIndex] = num1;
                m--;
            } else {
                nums1[maxIndex] = num2;
                n--;
            }
            maxIndex--;
        }
    }

    public static void main(String[] args) {
        int[] nums1 = new int[]{1, 2, 3, 0, 0, 0}, nums2 = new int[]{2, 5, 6};
        merge(nums1, 3, nums2, 3);
        Arrays.stream(nums1).forEach(num -> {
            System.out.print(num + " ");
        });
    }
}
```

> 【每日寄语】 *希望好心情每天照常营业，烦心事永久打烊。* 

