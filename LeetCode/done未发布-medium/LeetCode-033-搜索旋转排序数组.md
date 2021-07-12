#### 搜索旋转排序数组

> 题目描述：整数数组 nums 按升序排列，数组中的值 互不相同 。
>
> 在传递给函数之前，nums 在预先未知的某个下标 k（0 <= k < nums.length）上进行了 旋转，使数组变为 [nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]]（下标 从 0 开始 计数）。例如， [0,1,2,4,5,6,7] 在下标 3 处经旋转后可能变为 [4,5,6,7,0,1,2] 。
>
> 给你 旋转后 的数组 nums 和一个整数 target ，如果 nums 中存在这个目标值 target ，则返回它的下标，否则返回 -1 。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/search-in-rotated-sorted-array/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：二分查找

> 首先，如果nums只有一个数字，直接判断这个数字是否等于target，并返回结果；
>
> 如果nums不止一位，首先遍历一遍nums获取最大值的位置maxIndx，然后分两种情况：
>
> - 判断target如果不大于nums最后一位的数，则用二分查找法查找nums中`(maxIndx, nums.length - 1)`中是否存在跟target值相等的元素，如果有返回相应的位置，如果没有返回-1；
> - 如果target大于nums最后一位的数，则用二分查找法查找nums中`(0, maxIndx)`中是否存在跟target值相等的元素，如果有返回相应的位置，如果没有返回-1。

```java
public class LeetCode_033 {
    public static int search(int[] nums, int target) {
        if (nums.length == 1) {
            if (nums[0] == target) {
                return 0;
            } else {
                return -1;
            }
        }
        // 最大值的位置
        int maxIndx = -1;
        for (int i = 0; i < nums.length - 1; i++) {
            if (nums[i] > nums[i + 1]) {
                maxIndx = i;
                break;
            }
        }
        if (target <= nums[nums.length - 1]) {
            return find(nums, maxIndx + 1, nums.length - 1, target);
        } else {
            return find(nums, 0, maxIndx, target);
        }
    }

    /**
     * 二分查找
     * @param nums
     * @param left
     * @param right
     * @param target
     * @return
     */
    public static int find(int[] nums, int left, int right, int target) {
        int mid;
        while (left <= right) {
            mid = (left + right) / 2;
            if (nums[mid] == target) {
                return mid;
            } else if (nums[mid] < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        int[] nums = new int[]{4, 5, 6, 7, 0, 1, 2};
        System.out.println(search(nums, 0));
    }
}
```

> 【每日寄语】 *愿每一个醒来的日子，都有阳光相伴，或许在晴空，或许在心里。* 

