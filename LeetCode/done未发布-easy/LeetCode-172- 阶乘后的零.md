####  阶乘后的零

> 题目描述：给定一个整数 n，返回 n! 结果尾数中零的数量。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
>链接：https://leetcode-cn.com/problems/factorial-trailing-zeroes/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：统计2和5出现的次数

> 因为`2*5=10`，所以只要出现一个2和5就会多一个0，所以统计所有数字中可被2或5整除的次数，就可以得到有多少个0，用twoCount记录2出现的次数，用fiveCount记录5出现的次数，具体做法如下：
>
> - 遍历从1到n的数字num；
> - 计算num可被2或5整除的次数；
> - 最后返回twoCount和fiveCount中的较小者，即最终n!结果尾数中零的数量。

```java
public class LeetCode_172 {
    public static int trailingZeroes(int n) {
        int twoCount = 0, fiveCount = 0;
        for (int i = 1; i <= n; i++) {
            int num = i;
            while (num % 2 == 0 || num % 5 == 0) {
                if (num % 2 == 0) {
                    twoCount++;
                    num = num / 2;
                }
                if (num % 5 == 0) {
                    fiveCount++;
                    num = num / 5;
                }
            }
        }
        return Math.min(twoCount, fiveCount);
    }

    public static void main(String[] args) {
        System.out.println(trailingZeroes(5));
    }
}
```

> 【每日寄语】 *保持热爱奔赴山海，忠于自己热爱生活，知足上进不负野心，各自努力顶峰相见。* 

