#### 2 的幂

> 题目描述：给你一个整数 n，请你判断该整数是否是 2 的幂次方。如果是，返回 true ；否则，返回 false 。
>
> 如果存在一个整数 x 使得 n == $2^{x}$ ，则认为 n 是 2 的幂次方。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/power-of-two/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：二分法

> 首先，如果n是负数，直接返回false；
>
> 然后通过二分法查找是否有符合条件的整数，minPower和maxPower分别为整数范围内2的最小和最大次幂，过程如下：
>
> - mid赋值为maxPower和minPower的中间值；
> - 判断如果2的mid次幂等于n，则返回true；
> - 如果2的mid次幂大于n，则将maxPower赋值为mid-1；
> - 如果2的mid次幂小于你，则将minPower赋值为mid+1；
> - 循环终止的条件就是minPower大于maxPower。
>
> 最后如果没有符合条件的整数，返回false。

```java
public class LeetCode_231 {
    public static boolean isPowerOfTwo(int n) {
        if (n < 0) {
            return false;
        }
        int minPower = 0, maxPower = 30, mid;
        while (minPower <= maxPower) {
            mid = (minPower + maxPower) / 2;
            if (n == Math.pow(2, mid)) {
                return true;
            } else if (n < Math.pow(2, mid)) {
                maxPower = mid - 1;
            } else {
                minPower = mid + 1;
            }
        }
        return false;
    }

    public static void main(String[] args) {
        System.out.println(isPowerOfTwo(16));
    }
}
```

> 【每日寄语】 *驾驭命运的舵是奋斗，不抱有一丝幻想，不放弃一点机会，不停止一日努力。* 

