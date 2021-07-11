#### 计数质数

> 题目描述：统计所有小于非负整数 n 的质数的数量。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
>链接：https://leetcode-cn.com/problems/count-primes/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：暴力破解法

> 遍历从2开始到n-1的所有数字，用result记录质数的数量，如果是质数，则result加1，判断质数的方法如下：
>
> - 如果数字是2或3，则直接返回true；
> - 如果数字大于3，则从2到num的平方根，如果当前数num能被整除，则说明这个数不是质数，遍历完成，如果没有能整除的，则说明这个数是质数。

> 说明：该方法效率低，有更优解，待优化。

```java
public class LeetCode_204 {
    /**
     * 暴力破解法：提交后超出时间限制，性能不好
     * @param n
     * @return
     */
    public static int countPrimes(int n) {
        int result = 0;
        for (int i = 2; i < n; i++) {
            if (isPrime(i)) {
                result++;
            }
        }
        return result;
    }

    public static boolean isPrime(int num) {
        if (num == 2 || num == 3) {
            return true;
        }
        boolean result = true;
        for (int i = 2; i <= Math.sqrt(num); i++) {
            if (num % i == 0) {
                return false;
            }
        }
        return result;
    }

    public static void main(String[] args) {
        System.out.println(countPrimes(1500000));
    }
}
```

> 【每日寄语】 *想要得到世界最美好的东西，那就先让世界看看最美好的你。愿你遇见更好的自己！* 

