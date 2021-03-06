#### 位1的个数

> 题目描述：编写一个函数，输入是一个无符号整数（以二进制串的形式），返回其二进制表达式中数字位数为 '1' 的个数（也被称为汉明重量）。
>
> 提示：
>
> - 请注意，在某些语言（如 Java）中，没有无符号整数类型。在这种情况下，输入和输出都将被指定为有符号整数类型，并且不应影响您的实现，因为无论整数是有符号的还是无符号的，其内部的二进制表示形式都是相同的。
> - 在 Java 中，编译器使用二进制补码记法来表示有符号整数。因此，在上面的 示例 3 中，输入表示有符号整数 -3。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/number-of-1-bits/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：遍历

> 首先，用`Integer.toBinaryString(num)`方法将n转化为二进制字符串binaryString；
>
> 然后，遍历字符串binaryString的每一个字符，判断当前字符是否是'1'，如果是，则将result加1；
>
> 最后返回result即为二进制位中1的个数。

```java
public class LeetCode_191 {
    public static int hammingWeight(int n) {
        String binaryString = Integer.toBinaryString(n);
        int result = 0;
        for (char c : binaryString.toCharArray()) {
            if (c == '1') {
                result++;
            }
        }
        return result;
    }

    public static void main(String[] args) {
        System.out.println(hammingWeight(20));
    }
}
```

> 【每日寄语】 *生活如雨,请撑伞原谅!待到雨过天晴,它会还你一片蓝天,赠你一道彩虹。* 

