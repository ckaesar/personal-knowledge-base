#### Z 字形变换

> 题目描述：将一个给定字符串 s 根据给定的行数 numRows ，以从上往下、从左到右进行 Z 字形排列。
>
> 比如输入字符串为 "PAYPALISHIRING" 行数为 3 时，排列如下：
>
> P   A   H   N
> A P L S I I G
> Y   I   R
> 之后，你的输出需要从左往右逐行读取，产生出一个新的字符串，比如："PAHNAPLSIIGYIR"。
>
> 请你实现这个将字符串进行指定行数变换的函数：
>
> string convert(string s, int numRows);
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/zigzag-conversion/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：遍历

> 首先要判断当字符串的长度为空或者小于3的时候或numRows为1（即全部平铺在一行）时，直接返回字符串。否则，遍历字符串的字符，并用一个二维boolean数组标记，分2步，首先往下走，走不动了，再往右斜线走，重复这2步，直到把所有的字符都记录到，根据boolean数组的标记，返回结果。

```java
public class Solution {
    public static String convert(String s, int numRows) {
        if (s == null || s.length() < 3 || numRows == 1) {
            return s;
        }
        char[][] chars = new char[numRows][s.length()];
        boolean[][] flags = new boolean[numRows][s.length()];

        int x = -1, y = 0, count = 0;
        while (count < s.length()) {
            while (x < numRows && count < s.length()) {
                if (x + 1 < numRows) {
                    x++;
                    chars[x][y] = s.charAt(count);
                    flags[x][y] = true;
                    count++;
                } else {
                    break;
                }
            }
            while (x >= 0 && count < s.length()) {
                if (x - 1 >= 0) {
                    x--;
                    y++;
                    chars[x][y] = s.charAt(count);
                    flags[x][y] = true;
                    count++;
                } else {
                    break;
                }
            }
        }
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < chars.length; i++) {
            for (int j = 0; j < chars[i].length; j++) {
                if (flags[i][j]) {
                    sb.append(String.valueOf(chars[i][j]));
                }
            }
        }

        return sb.toString();
    }

    public static void main(String[] args) {
        System.out.println(convert("ABC", 1));
    }
}
```
