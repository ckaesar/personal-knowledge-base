#### 整数反转

> 题目描述：给你一个 32 位的有符号整数 x ，返回将 x 中的数字部分反转后的结果。
>
> 如果反转后整数超过 32 位的有符号整数的范围 [$−2^{31}$,  $2^{31}$ − 1] ，就返回 0。
>
> 假设环境不允许存储 64 位整数（有符号或无符号）。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/reverse-integer/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：字符串遍历

> 将输入的整数转换成字符串，从后往前遍历。
>
> 注意点：考虑转化后的值是否超过整数的范围，如果超过了，返回0。

```java
public class Solution {
    public static int reverse(int x) {
        if (x == 0 || x < Integer.MIN_VALUE || x > Integer.MAX_VALUE) {
            return 0;
        }
        String xStr = String.valueOf(x);
        String symbol = "";
        if (x < 0) {
            symbol = "-";
            xStr = xStr.substring(1);
        }
        String result = "";
        int zeroCount = 0;
        for (int i = xStr.length() - 1; i >= 0; i--) {
            if (xStr.charAt(i) != '0') {
                break;
            } else {
                zeroCount++;
            }
        }
        for (int i = xStr.length() - 1 - zeroCount; i >= 0; i--) {
            result += xStr.charAt(i);
        }
        double doubleResult = Double.valueOf(symbol + result);
        if (doubleResult < Integer.MIN_VALUE || doubleResult > Integer.MAX_VALUE) {
            return 0;
        }
        return Integer.valueOf(symbol + result);
    }

    public static void main(String[] args) {
        System.out.println(reverse(123));
    }
}
```
