#### 下一个排列

> 题目描述：实现获取 下一个排列 的函数，算法需要将给定数字序列重新排列成字典序中下一个更大的排列。
>
> 如果不存在下一个更大的排列，则将数字重新排列成最小的排列（即升序排列）。
>
> 必须 原地 修改，只允许使用额外常数空间。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/next-permutation/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：遍历数组

> 首先，如果数组为空或者数组只有一个元素，直接返回；
>
> 声明一个变量handled表示是否找到更大的排列，默认是false，left和right分别记录找到更大排列需要调换的数字，然后双重循环遍历数组判断是否存在更大的排列，具体遍历过程如下：
>
> - 从数组的最后一位开始遍历，如果存在前面的数字比当前数字大的，则left和right分别记录当前索引位，并将handled更新为true，然后遍历下一位；
> - 遍历过程中需要判断如果找到一种符合条件的数字，要判断是否比之前已得到的情况更优，如果是，更新left和right。
>
> 然后根据handled判断，如果为false，说明没有更大的排列，也就是不存在下一个更大排列，将数字重新排列成最小的排列，就是将顺序倒排；如果为true，则需要进行如下处理：
>
> - 首先，将left和right位置的数字调换位置；
> - 然后将 right+1 后面的数字倒排，这一步是为了将后面的数字排列成最小的值；
> - 然后将 left+1到right-1 之间的数字跟 right+1到nums.length-1 的数字整体调换顺序，这一步也是为了将left后面的数字排列成最小的值；
> - 然后将 left+1 位置的数字移到小于它的数字之后，这一步是为了获取最终的排列结果。

```java
import java.util.Arrays;

public class LeetCode_031 {
    public static void nextPermutation(int[] nums) {
        // 如果数组为空，或者数组的长度为0或者只有一个元素，不用处理
        if (nums == null || nums.length < 2) {
            return;
        }
        // 是否找到更大的排列
        boolean handled = false;
        // 首先找到需要调换位置的数字
        int left = -1, right = -1;
        for (int i = nums.length - 1; i > 0; i--) {
            for (int j = i - 1; j >= 0; j--) {
                if (nums[i] > nums[j]) {
                    if (j > left) {
                        left = j;
                        right = i;
                    } else if (j == left) {
                        if (i == right) {
                            left = j;
                            right = i;
                        }
                    }
                    handled = true;
                    break;
                }
            }
        }

        if (handled) {
            // 找到更大的排列
            // 1.将 right 的数字和 left 的数字调换位置
            exch(nums, left, right);
            // 2.首先将 right+1 后面的数字倒排
            for (int x = right + 1; x < (nums.length + right + 1) / 2; x++) {
                exch(nums, x, nums.length - 1 - (x - right) / 2);
            }
            // 3.然后将 left+1到right-1 之间的数字跟 right+1到nums.length-1 的数字整体调换顺序
            for (int x = right - 1; x >= left + 1; x--) {
                for (int y = x; y < nums.length - 1; y++) {
                    exch(nums, y, y + 1);
                }
            }
            // 4.然后将 left+1 位置的数字移到小于它的数字之后
            for (int x = left + 1; x < nums.length - 1; x++) {
                if (nums[x] > nums[x + 1]) {
                    exch(nums, x, x + 1);
                } else {
                    break;
                }
            }
        } else {
            // 如果handled为false，说明没有更大的排列，也就是不存在下一个更大排列，将数字重新排列成最小的排列，
            // 就是将顺序倒排
            for (int i = 0; i < nums.length / 2; i++) {
                exch(nums, i, nums.length - 1 - i);
            }
        }
    }

    private static void exch(int[] nums, int left, int right) {
        int temp = nums[right];
        nums[right] = nums[left];
        nums[left] = temp;
    }

    public static void main(String[] args) {
        int[] nums = new int[]{4, 2, 0, 2, 3, 2, 0};
        System.out.println("=====处理前=====");
        Arrays.stream(nums).forEach(num -> {
            System.out.print(num + " ");
        });
        System.out.println();
        System.out.println("=====处理后=====");
        nextPermutation(nums);
        Arrays.stream(nums).forEach(num -> {
            System.out.print(num + " ");
        });
    }
}
```

> 【每日寄语】 *努力是人生应有的态度，睁开眼就是新的开始。* 

