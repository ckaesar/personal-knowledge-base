#### 杨辉三角 II

> 题目描述：给定一个非负索引 k，其中 k ≤ 33，返回杨辉三角的第 k 行。
>
> 在杨辉三角中，每个数是它左上方和右上方的数的和。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/pascals-triangle-ii/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：暴力破解法

> 首先，当numRows等于0或者1时，直接返回固定的前两行；
>
> 当numRows大于等于2时，从第2行开始处理，假如当前行是cur，上一行是last：
>
> - cur的第一个数字是1；
> - cur的第二个数字到倒数第二个数字(j)是last行的相应位置(j-2和j-1)的和；
> - cur的最后一个数字是1；
> - 将last设置为cur。
>
> 最后返回cur。

> 备注：方法跟该题 **LeetCode-118-杨辉三角** 完全一样。

```java
import java.util.ArrayList;
import java.util.List;

public class LeetCode_119 {
    public static List<Integer> getRow(int rowIndex) {
        List<Integer> one = new ArrayList<>();
        one.add(1);
        if (rowIndex == 0) {
            return one;
        }
        List<Integer> two = new ArrayList<>();
        two.add(1);
        two.add(1);
        if (rowIndex == 1) {
            return two;
        }
        List<Integer> last = two;
        List<Integer> cur = new ArrayList<>();
        for (int i = 2; i <= rowIndex; i++) {
            cur = new ArrayList<>();
            cur.add(1);
            for (int j = 1; j < i; j++) {
                cur.add(last.get(j - 1) + last.get(j));
            }
            cur.add(1);
            last = cur;
        }
        return cur;
    }

    public static void main(String[] args) {
        for (Integer integer : getRow(3)) {
            System.out.print(integer + " ");
        }
    }
}
```

> 【每日寄语】 *愿你所得过少时，不会终日愤愤；愿你所得过多时，不必终日惶恐。* 

