#### 罗马数字转整数

> 题目描述：罗马数字包含以下七种字符: I， V， X， L，C，D 和 M。
>
> 字符          数值
> I             	  1
> V             	 5
> X             	 10
> L             	  50
> C             	 100
> D             	 500
> M             	1000
> 例如， 罗马数字 2 写做 II ，即为两个并列的 1。12 写做 XII ，即为 X + II 。 27 写做  XXVII, 即为 XX + V + II 。
>
> 通常情况下，罗马数字中小的数字在大的数字的右边。但也存在特例，例如 4 不写做 IIII，而是 IV。数字 1 在数字 5 的左边，所表示的数等于大数 5 减小数 1 得到的数值 4 。同样地，数字 9 表示为 IX。这个特殊的规则只适用于以下六种情况：
>
> I 可以放在 V (5) 和 X (10) 的左边，来表示 4 和 9。
> X 可以放在 L (50) 和 C (100) 的左边，来表示 40 和 90。 
> C 可以放在 D (500) 和 M (1000) 的左边，来表示 400 和 900。
> 给定一个罗马数字，将其转换成整数。输入确保在 1 到 3999 的范围内。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/roman-to-integer/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：从大到小取值

> 利用**String**的**startsWith()**方法，按照罗马数字的大小取值，将对应的数字累加起来，就得到了最终的结果。
>
> 参考题目：**LeetCode-013-罗马数字转整数**，和这个题目处理过程相反。

```java
public class Solution {

    public static int romanToInt(String s) {
        // 所有可能的取值
        int[] values = {1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1};
        // 对应的罗马数字表示
        String[] romans = {"M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"};
        int result = 0;
        for (int i = 0; i < romans.length && s.length() > 0; i++) {
            String roman = romans[i];
            int value = values[i];
            while (s.startsWith(roman)) {
                s = s.substring(roman.length());
                result += value;
            }
        }
        return result;
    }

    public static void main(String[] args) {
        System.out.println(romanToInt("III"));
        System.out.println(romanToInt("IV"));
        System.out.println(romanToInt("IX"));
        System.out.println(romanToInt("LVIII"));
        System.out.println(romanToInt("MCMXCIV"));
    }
}
```
