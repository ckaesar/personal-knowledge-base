#### 最后一个单词的长度

> 题目描述：给你一个字符串 s，由若干单词组成，单词之间用空格隔开。返回字符串中最后一个单词的长度。如果不存在最后一个单词，请返回 0 。
>
> 单词 是指仅由字母组成、不包含任何空格字符的最大子字符串。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/length-of-last-word/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：用lastIndexOf方法

> 首先，用`trim()`方法将**s**的前后空格去除，然后判断如果**s**中是否包含空格，如果不包含，说明只有一个单词，直接返回**s**的长度；如果包含，则用`lastIndexOf()`方法获取**s**中最后一个空格的位置，最后，利用`substring()`方法截取**s**中最后一个单词，返回这个单词的长度。

```java
public class LeetCode_058 {
    public static int lengthOfLastWord(String s) {
        s = s.trim();
        if (!s.contains(" ")) {
            return s.length();
        }
        int lastIndexOfSpace = s.lastIndexOf(" ");
        return s.substring(lastIndexOfSpace, s.length() - 1).length();
    }

    public static void main(String[] args) {
        System.out.println(lengthOfLastWord("Hello World"));
    }
}
```

> 【每日寄语】 *如果对方脸上没有笑容，那就将自己的笑容，展现给TA吧。用微笑面对每一天。* 

