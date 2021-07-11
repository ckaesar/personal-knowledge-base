#### 存在重复元素

> 题目描述：给定一个整数数组，判断是否存在重复元素。
>
> 如果存在一值在数组中出现至少两次，函数返回 true 。如果数组中每个元素都不相同，则返回 false 。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/contains-duplicate/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：HashSet判重

> 利用HashSet判重，声明一个HashSet变量notRepeatedNums，遍历数组nums，将每一位的数字用`add()`方法加到notRepeatedNums里，如果返回false，说明这个数字已经存在，也就是存在重复元素，返回true；如果返回true，则会把当前数字加到notRepeatedNums里，然后遍历下一个数字。遍历完成后，如果没有重复数字，返回false。

```java
import java.util.HashSet;
import java.util.Set;

public class LeetCode_217 {
    public static boolean containsDuplicate(int[] nums) {
        Set<Integer> notRepeatedNums = new HashSet<>();
        for (int num : nums) {
            if (!notRepeatedNums.add(num)) {
                return true;
            }
        }
        return false;
    }

    public static void main(String[] args) {
        int[] nums = new int[]{1, 2, 3, 1};
        System.out.println(containsDuplicate(nums));
    }
}
```

> 【每日寄语】 *善良的人总是快乐！感恩的人总是富有！让我们带着感恩与善良，不忘初心，温暖前行。* 

