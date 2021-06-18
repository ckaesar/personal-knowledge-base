#### 移除元素

> 题目描述：给你一个数组 nums 和一个值 val，你需要 原地 移除所有数值等于 val 的元素，并返回移除后数组的新长度。
>
> 不要使用额外的数组空间，你必须仅使用 O(1) 额外空间并 原地 修改输入数组。
>
> 元素的顺序可以改变。你不需要考虑数组中超出新长度后面的元素。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/remove-element/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：交换位置

> - 首先，如果数组为空或者数组的长度为0，直接返回0；
> - 然后，如果数组不为空，遍历数组，count记录和val值不相同的数目（也就是最后的返回值），index表示从0开始遍历，reverseCount表示交换数字的次数，具体遍历过程如下：
>   - 当index对应的值不等于val时，count加1，并且index加1也就是往后移一位；
>   - 当index对应的值等于val时，判断index是否后面可遍历的位数，如果是，则将index和可遍历的最后一位交换数字，并且reverseCount+1，然后继续遍历；如果不是，则没有可交换的位置，即已经遍历完成。返回count值。

```java
public class LeetCode_027 {
    public static int removeElement(int[] nums, int val) {
        if (nums == null || nums.length == 0) {
            return 0;
        }
        int count = 0;
        int index = 0;
        int reverseCount = 0;
        while (index < nums.length - reverseCount) {
            if (nums[index] != val) {
                index++;
                count++;
            } else {
                if (index < (nums.length - 1 - reverseCount)) {
                    int temp = nums[index];
                    nums[index] = nums[nums.length - 1 - reverseCount];
                    nums[nums.length - 1 - reverseCount] = temp;
                    reverseCount++;
                } else {
                    break;
                }
            }
        }
        return count;
    }

    public static void main(String[] args) {
        int[] nums = new int[]{1};
        System.out.println(removeElement(nums, 1));
        System.out.println();
        for (int num : nums) {
            System.out.print(num + " ");
        }
    }
}
```

> 【每日寄语】 *昨天是历史，明天是谜团，只有今天是天赐的礼物。* 

