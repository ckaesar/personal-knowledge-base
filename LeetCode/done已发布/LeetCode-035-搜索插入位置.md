#### 搜索插入位置

> 题目描述：给定一个排序数组和一个目标值，在数组中找到目标值，并返回其索引。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。
>
> 你可以假设数组中无重复元素。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/search-insert-position/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：暴力破解法

> - 首先，如果**nums**是null或者为空，直接返回0；
> - 从**nums**的第一个元素开始遍历，当**target**不大于当前元素时，返回当前元素的索引位；
> - 如果没有找到比**target**更大的元素，则返回**nums.length**。

###### 解法二：二分查找法

> 二分查找的解法，low和high分别是数组的第一位和最后一位，mid为`(low+high)/2`，判断mid的值是否和target相等，根据大小分别移动low和high，直到low不小于high为止，返回结果。

```java
public class LeetCode_035 {
    /**
     * 暴力破解法
     *
     * @param nums
     * @param target
     * @return
     */
    public static int searchInsert(int[] nums, int target) {
        if (nums == null || nums.length == 0) {
            return 0;
        }
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] >= target) {
                return i;
            }
        }
        return nums.length;
    }

    /**
     * 二分查找法
     *
     * @param nums
     * @param target
     * @return
     */
    public static int searchInsert2(int[] nums, int target) {
        if (nums == null || nums.length == 0) {
            return 0;
        }
        int low = 0, high = nums.length - 1, mid, result = nums.length;
        while (low <= high) {
            mid = (low + high) / 2;
            if (nums[mid] >= target) {
                result = mid;
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        }
        return result;
    }

    public static void main(String[] args) {
        int[] nums = new int[]{1, 3, 5, 6};
        System.out.println(searchInsert(nums, 7));
        System.out.println(searchInsert2(nums, 7));
    }
}
```

> 【每日寄语】 *只要你奔跑，这个世界就会跟着你奔跑。确定一个方向，使劲的跑起来，这个世界会为你让路。* 

