#### 在排序数组中查找元素的第一个和最后一个位置

> 题目描述：给定一个按照升序排列的整数数组 nums，和一个目标值 target。找出给定目标值在数组中的开始位置和结束位置。
>
> 如果数组中不存在目标值 target，返回 [-1, -1]。
>
> 进阶：
>
> - 你可以设计并实现时间复杂度为 O(log n) 的算法解决此问题吗？
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/find-first-and-last-position-of-element-in-sorted-array/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：二分查找、递归

> 用left和right记录开始位置和结束位置，用二分查找法查找target在nums中的位置，从0到nums.length-1分别记为low和high，mid表示中间值，具体过程如下：
>
> - 计算mid为low和high的中间值；
> - 如果mid的值和target相等，则判断mid左边的元素是否跟target相等，如果相等，则递归查找开始位置，从low到mid-1查找，如果不相等，则left为mid；判断mid右边的元素是否跟target相等，如果相等，则递归查找结束位置，从mid+1到high查找，如果不相等，则right为mid；
> - 如果mid的值大于target，则high更新为mid-1；
> - 如果mid的值小于target，则low更新为mid+1。
>
> 查找完成后返回left和right即为最终结果。

```java
import javafx.util.Pair;

public class LeetCode_034 {
    public static int[] searchRange(int[] nums, int target) {
        Pair<Integer, Integer> result = find(nums, 0, nums.length - 1, target);
        return new int[]{result.getKey(), result.getValue()};
    }

    public static Pair<Integer, Integer> find(int[] nums, int low, int high, int target) {
        int mid, left = -1, right = -1;
        while (low <= high) {
            mid = (low + high) / 2;
            if (nums[mid] == target) {
                if (mid + 1 <= high && nums[mid + 1] == nums[mid]) {
                    right = find(nums, mid + 1, high, target).getValue();

                } else {
                    right = mid;
                }
                if (mid - 1 >= low && nums[mid - 1] == nums[mid]) {
                    left = find(nums, low, mid - 1, target).getKey();
                } else {
                    left = mid;
                }
                break;
            } else if (nums[mid] > target) {
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        }
        return new Pair<>(left, right);
    }

    public static void main(String[] args) {
        int[] nums = new int[]{5, 7, 7, 8, 8, 10};
        int[] ints = searchRange(nums, 8);
        System.out.println("[" + ints[0] + "," + ints[1] + "]");
    }
}
```

> 【每日寄语】 *阳春三月，万物复苏，愿所有美好如期而至。* 
