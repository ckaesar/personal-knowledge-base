#### 杨辉三角

> 题目描述：给定一个非负整数 numRows，生成杨辉三角的前 numRows 行。
>
> 在杨辉三角中，每个数是它左上方和右上方的数的和。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/pascals-triangle/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：暴力破解法

> 首先，当numRows等于1或者2时，直接返回固定的前两行；
>
> 当numRows大于等于3时，从第3行开始处理，假如当前行是cur，上一行是last：
>
> - cur的第一个数字是1；
> - cur的第二个数字到倒数第二个数字(j)是last行的相应位置(j-2和j-1)的和；
> - cur的最后一个数字是1；
> - 将cur添加到结果集result里。
>
> 最后返回result。

```java
import java.util.ArrayList;
import java.util.List;

public class LeetCode_118 {
    public static List<List<Integer>> generate(int numRows) {
        List<List<Integer>> result = new ArrayList<>();
        List<Integer> one = new ArrayList<>();
        one.add(1);
        result.add(one);
        if (numRows == 1) {
            return result;
        }
        List<Integer> two = new ArrayList<>();
        two.add(1);
        two.add(1);
        result.add(two);
        if (numRows == 2) {
            return result;
        }
        for (int i = 3; i <= numRows; i++) {
            List<Integer> lastOne = result.get(result.size() - 1);
            List<Integer> cur = new ArrayList<>();
            cur.add(1);
            for (int j = 2; j < i; j++) {
                cur.add(lastOne.get(j - 2) + lastOne.get(j - 1));
            }
            cur.add(1);
            result.add(cur);
        }
        return result;
    }

    public static void main(String[] args) {
        for (List<Integer> integers : generate(5)) {
            for (Integer integer : integers) {
                System.out.print(integer + " ");
            }
            System.out.println();
        }
    }
}
```

> 【每日寄语】 *以清净心看世界，以欢喜心过生活，以平常心生情味，以柔软心除挂碍。* 

