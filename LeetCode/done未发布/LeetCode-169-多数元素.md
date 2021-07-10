#### 多数元素

> 题目描述：给定一个大小为 n 的数组，找到其中的多数元素。多数元素是指在数组中出现次数 大于 ⌊ n/2 ⌋ 的元素。
>
> 你可以假设数组是非空的，并且给定的数组总是存在多数元素。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/majority-element/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：HashMap

> 利用java的`HashMap`，key存不同的数字，value存对应的数字出现的次数：
>
> - 遍历nums，将每个数字放入HashMap里；
> - 比较得到的HashMap，比较每个数字出现的次数，得到出现次数最多的数字，返回结果。

```java
import java.util.HashMap;
import java.util.Map;

public class LeetCode_169 {
    public static int majorityElement(int[] nums) {
        Map<Integer, Integer> count = new HashMap<>();
        for (int num : nums) {
            if (count.get(Integer.valueOf(num)) == null) {
                count.put(Integer.valueOf(num), 1);
            } else {
                count.put(Integer.valueOf(num), count.get(Integer.valueOf(num)) + 1);
            }
        }
        int result = -1, maxCount = -1;
        for (Map.Entry<Integer, Integer> integerIntegerEntry : count.entrySet()) {
            if (integerIntegerEntry.getValue() > maxCount) {
                maxCount = integerIntegerEntry.getValue();
                result = integerIntegerEntry.getKey();
            }
        }
        return result;
    }

    public static void main(String[] args) {
        int[] nums = new int[]{3, 3, 4};
        System.out.println(majorityElement(nums));
    }
}
```

> 【每日寄语】 *所有逆袭，都是有备而来；所有光芒，都是努力埋下的伏笔。* 

