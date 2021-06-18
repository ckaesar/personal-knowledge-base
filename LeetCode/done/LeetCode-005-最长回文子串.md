#### 最长回文子串

> 题目描述：给你一个字符串 s，找到 s 中最长的回文子串。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
>链接：https://leetcode-cn.com/problems/longest-palindromic-substring/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：暴力破解法

> 遍历所有可能的子串，然后判断子串是否是回文子串，如果是，判断是否超过当前最长的长度，遍历完成即可得到最长的回文子串。  这是我第一个想到的方法， 尴尬的是leetcode上提交之后**超出时间限制**了，此方法不可取。

###### 解法二：动态规划

> 动态规划效率更高，待完成。

```java
public class Solution {
    /**
     * 解法一：暴力破解法
     *
     * @param s
     * @return
     */
    public static String longestPalindrome(String s) {
        if (s == null || s.length() < 2) {
            return s;
        }
        String result = String.valueOf(s.charAt(0));
        int max = 1;
        StringBuilder sb;
        for (int i = 0; i < s.length() - 1; i++) {
            sb = new StringBuilder(String.valueOf(s.charAt(i)));
            for (int j = i + 1; j < s.length(); j++) {
                sb.append(s.charAt(j));
                if (checkPalindrome(sb.toString())) {
                    if (sb.length() > max) {
                        result = sb.toString();
                        max = sb.length();
                    }
                }
            }
        }
        return result;
    }

    /**
     * 解法二：动态规划
     *
     * @param s
     * @return
     */
    public static String longestPalindrome2(String s) {
        // TODO: 2021/6/7 待完成 
        return null;
    }

    public static boolean checkPalindrome(String str) {
        if (str == null || str.length() == 1) {
            return true;
        }
        if (str.length() == 2 && str.charAt(0) == str.charAt(1)) {
            return true;
        }
        int count = str.length();
        for (int i = 0; i < count; i++) {
            if (str.charAt(i) != str.charAt(count - i - 1)) {
                return false;
            }
        }
        return true;
    }

    public static void main(String[] args) {
        // 超时的例子 后面还有很多很多个d
        System.out.println(longestPalindrome("dddddddd..."));
    }
}
```
