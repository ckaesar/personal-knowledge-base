#### 删除有序数组中的重复项

> 题目描述：给你一个有序数组 nums ，请你 原地 删除重复出现的元素，使每个元素 只出现一次 ，返回删除后数组的新长度。
>
> 不要使用额外的数组空间，你必须在 原地 修改输入数组 并在使用 O(1) 额外空间的条件下完成。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/remove-duplicates-from-sorted-array/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：数组的遍历

> - 首先，如果数组nums为空或者数组nums的长度为0，直接返回0；
> - current记录当前不重复的索引位置，遍历数组，pre记录上一位的值，当当前位index的值和pre的值相等时，`index+1`后往后继续遍历；当当前位的值和pre的值不相等时，更新current的值为当前index位的值，并且将current往后移一位，index+1，pre不停的往后移，直到遍历结束位置。

```java
public class LeetCode_026 {
    public static int removeDuplicates(int[] nums) {
        if (nums.length == 0) {
            return 0;
        }
        int current = 1;
        int index = 1;
        int pre = nums[0];
        while (index < nums.length) {
            if (!(nums[index] == pre)) {
                nums[current++] = nums[index];
            }
            pre = nums[index];
            index++;
        }
        return current;
    }

    public static void main(String[] args) {
        int[] nums = new int[]{0, 0, 1, 1, 1, 2, 2, 3, 3, 4};
        int result = removeDuplicates(nums);
        System.out.println(result);
        for (int num : nums) {
            System.out.print(num + " ");
        }
    }
}
```

> 【每日寄语】 *纵有千古，横有八荒；前途似海，来日方长。* 

