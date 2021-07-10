#### 爬楼梯

> 题目描述：假设你正在爬楼梯。需要 n 阶你才能到达楼顶。
>
> 每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？
>
> 注意：给定 n 是一个正整数。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/climbing-stairs/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 问题解析

> 典型的斐波那契数列，因为到第n个台阶有2种走法， 要么是从第n-1个台阶上去，要么是从第n-2个台阶上去，所以到第n个台阶的走法总数等于第n-1个台阶的走法加上第n-2个台阶的走法。

###### 解法一：递归

> 递归调用同一个方法，首先如果n为1或者2的时候直接返回n；如果n大于2的时候则递归调用该方法即`f(n) = f(n - 1) + f(n - 2)`。

###### 解法二：迭代

> 首先如果n为1或者2的时候直接返回n；如果n大于2的时候，则记录2个之前的值分别为lastOne和lastTwo，则当前的值为这2个值的和，然后更新lastOne和lastTwo的值，直到迭代到n为止。

```java
public class LeetCode_070 {
    /**
     * 递归：提交时超出时间限制了
     *
     * @param n
     * @return
     */
    public static int climbStairs(int n) {
        if (n == 1 || n == 2) {
            return n;
        }
        return climbStairs(n - 1) + climbStairs(n - 2);
    }

    /**
     * 迭代
     *
     * @param n
     * @return
     */
    public static int climbStairs2(int n) {
        if (n == 1 || n == 2) {
            return n;
        }
        int lastOne = 1, lastTwo = 2, result = -1;
        for (int i = 3; i <= n; i++) {
            result = lastOne + lastTwo;
            lastOne = lastTwo;
            lastTwo = result;
        }
        return result;
    }

    public static void main(String[] args) {
        System.out.println(climbStairs(45));
        System.out.println(climbStairs2(45));
    }
}
```

> 【每日寄语】 *你的好运气藏在你的实力里，也藏在你不为人知的努力里，你越努力，就越幸运。* 

