#### 外观数列

> 题目描述：给定一个正整数 n ，输出外观数列的第 n 项。
>
> 「外观数列」是一个整数序列，从数字 1 开始，序列中的每一项都是对前一项的描述。
>
> 你可以将其视作是由递归公式定义的数字字符串序列：
>
> - countAndSay(1) = "1"
> - countAndSay(n) 是对 countAndSay(n-1) 的描述，然后转换成另一个数字字符串。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/count-and-say/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：迭代

> 如果n为1，直接返回“1”；如果n大于1，记录last为上一个字符串序列，初始为“1”，curNum记录当前字符数字，curNumCount记录当前字符数字连续出现的次数，cur为当前需要得到的字符串序列，遍历last，获取每个字符数字连续出现的次数，得到cur，然后将cur赋值给last，继续下一轮处理，最终返回cur。

```java
public class LeetCode_038 {
    public static String countAndSay(int n) {
        if (n == 1) {
            return "1";
        }
        String last = "1", cur = "";
        char curNum;
        int curNumCount = 0;
        for (int i = 2; i <= n; i++) {
            cur = "";
            curNum = last.charAt(0);
            curNumCount = 1;
            for (int x = 1; x < last.length(); x++) {
                if (last.charAt(x) == curNum) {
                    curNumCount++;
                } else {
                    cur += curNumCount + "" + curNum;
                    curNum = last.charAt(x);
                    curNumCount = 1;
                }
            }
            cur += curNumCount + "" + curNum;
            last = cur;
        }
        return cur;
    }

    public static void main(String[] args) {
        System.out.println(countAndSay(5));
    }
}
```

> 【每日寄语】 *山有峰顶，海有彼岸。漫漫长途，终有回转。余味苦涩，终有回甘。* 

