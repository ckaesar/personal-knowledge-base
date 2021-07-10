#### 二进制求和

> 题目描述：给你两个二进制字符串，返回它们的和（用二进制表示）。
>
> 输入为 非空 字符串且只包含数字 1 和 0。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/add-binary/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：分组处理

> 由于过长的字符串直接转成int值会报错，因为超出了int值的上线，所以采取分段处理的方式，从后往前，每30位相加，利用了`Integer.parseInt(String, 2)`方法将字符串二进制数转成10进制的int值，然后利用`Integer.toBinaryString(int)`方法将相加后的值再转成二进制字符串，然后把分段的字符串加起来，就是最后的结果。
>
> 做的过程中有几点要考虑：
>
> - 第一，每段相加时，考虑是否有进位，如果有进位，用addOne表示进位数，值为1，在下一分段相加时把addOne加上；
> - 第二，当每段相加的结果长度小于30位时，需要在前面补0，补到30位。

```java
public class LeetCode_067 {
    public static String addBinary(String a, String b) {
        int addOne = 0;
        String result = "";
        while (a.length() > 30 || b.length() > 30) {
            String aStr;
            String bStr;
            if (a.length() > 30) {
                aStr = a.substring(a.length() - 30, a.length());
                a = a.substring(0, a.length() - 30);
            } else {
                aStr = a;
                a = "0";
            }
            if (b.length() > 30) {
                bStr = b.substring(b.length() - 30, b.length());
                b = b.substring(0, b.length() - 30);
            } else {
                bStr = b;
                b = "0";
            }
            String temp = Integer.toBinaryString(Integer.parseInt(aStr, 2) + Integer.parseInt(bStr, 2) + addOne);
            if (temp.length() > 30) {
                addOne = 1;
                temp = temp.substring(1, temp.length());
            } else {
                if(temp.length() < 30) {
                    int zeroCount = 30 - temp.length();
                    for(int i = 0; i < zeroCount; i++) {
                        temp = "0" + temp;
                    }
                }
                addOne = 0;
            }
            result = temp + result;
        }
        return Integer.toBinaryString(Integer.parseInt(a, 2) + Integer.parseInt(b, 2) + addOne) + result;
    }

    public static void main(String[] args) {
        String a = "1001101011011010000010111010100111001000100001111110011111001010100101111";
        String b = "111000011000010000001100001001010011000101000000001111101101000100000000100100001100010000111001000";
        System.out.println(addBinary(a, b));
    }
}
```

> 【每日寄语】 *天可补，海可填，南山可移。日月既往，不可复追。* 

