#### 快乐数

> 题目描述：编写一个算法来判断一个数 n 是不是快乐数。
>
> 「快乐数」定义为：
>
> - 对于一个正整数，每一次将该数替换为它每个位置上的数字的平方和。
>
> - 然后重复这个过程直到这个数变为 1，也可能是 无限循环 但始终变不到 1。
> - 如果 可以变为  1，那么这个数就是快乐数。
> - 如果 n 是快乐数就返回 true ；不是，则返回 false 。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/happy-number/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：暴力破解法

> 由于int类型的最大值的各数位的平方和相加的结果也是有限的数，所以如果某个数不是快乐数，则多次平方和相加后一定会出现循环，当循环后就终止，因为再次计算的结果一样，具体过程如下，用appearedNums记录出现过的数：
>
> - num从n开始，判断num是否出现在appearedNums里，如果出现过，则出现循环，直接返回false；
> - 如果没有出现过，则计算各数位的平方和sum是否为1，如果是1，则这个数是快乐数；否则，继续将sum赋值给num，继续下一次判断。

```java
import java.util.ArrayList;
import java.util.List;

public class LeetCode_202 {
    public static boolean isHappy(int n) {
        if (n == 1) {
            return true;
        }
        List<Integer> appearedNums = new ArrayList<>();
        int num = n;
        while (!appearedNums.contains(num)) {
            appearedNums.add(num);
            int sum = 0;
            for (char c : String.valueOf(num).toCharArray()) {
                int cur = Integer.valueOf(String.valueOf(c));
                sum += cur * cur;
            }
            if (sum == 1) {
                return true;
            } else {
                num = sum;
            }
        }
        return false;
    }

    public static void main(String[] args) {
        System.out.println(isHappy(2));
    }
}
```

> 【每日寄语】 *顺其自然，人生会顺畅很多，豁达以对，世界会温柔很多。* 

