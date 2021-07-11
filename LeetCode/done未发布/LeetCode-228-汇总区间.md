#### 汇总区间

> 题目描述：给定一个无重复元素的有序整数数组 nums 。
>
> 返回 恰好覆盖数组中所有数字 的 最小有序 区间范围列表。也就是说，nums 的每个元素都恰好被某个区间范围所覆盖，并且不存在属于某个范围但不属于 nums 的数字 x 。
>
> 列表中的每个区间范围 [a,b] 应该按如下格式输出：
>
> - "a->b" ，如果 a != b
>
> - "a" ，如果 a == b
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/summary-ranges/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：遍历数组

> 首先，初始化一个result存返回结果，然后，处理过程如下：
>
> - 如果nums为null或者nums没有一个元素，直接返回result；
>
> - 如果nums只有一个元素，将唯一的元素添加到result中，返回result；
>
> - 初始化start和end为数组的第一个元素，然后从第1位开始遍历数组：
>
>   - 如果当前元素比end大1，说明是连续的，将当前元素赋值给end；
>   - 否则，判断start是否等于end，即将当前区间添加到result结果中，然后将当前元素赋值给start和end。
>
>   遍历完成后，把最后一个区间添加到result结果中，返回result。

```java
import java.util.ArrayList;
import java.util.List;

public class LeetCode_228 {
    public static List<String> summaryRanges(int[] nums) {
        List<String> result = new ArrayList<>();
        if (nums == null || nums.length == 0) {
            return result;
        }
        if (nums.length == 1) {
            result.add(String.valueOf(nums[0]));
            return result;
        }
        int start = nums[0], end = nums[0];
        for (int i = 1; i < nums.length; i++) {
            if (nums[i] == end + 1) {
                end = nums[i];
            } else {
                if (start == end) {
                    result.add("" + start);
                } else {
                    result.add(start + "->" + end);
                }
                start = end = nums[i];
            }
        }
        if (start == end) {
            result.add("" + start);
        } else {
            result.add(start + "->" + end);
        }
        return result;
    }

    public static void main(String[] args) {
        int[] nums = new int[]{0, 1, 2, 4, 5, 7};
        for (String summaryRange : summaryRanges(nums)) {
            System.out.println(summaryRange);
        }
    }
}
```

> 【每日寄语】 *你要做冲出的黑马 而不是坠落的星星。* 

