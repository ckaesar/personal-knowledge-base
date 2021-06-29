#### 正则表达式匹配

> 题目描述：给你一个字符串 s 和一个字符规律 p，请你来实现一个支持 '.' 和 '*' 的正则表达式匹配。
>
> '.' 匹配任意单个字符
> '*' 匹配零个或多个前面的那一个元素
> 所谓匹配，是要涵盖 整个 字符串 s的，而不是部分字符串。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/regular-expression-matching/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：遍历、递归

> 遍历p，将s和p进行匹配。分几种情况，分别是 '.' 或 '\*' 或者两者都不是的情况， '.' 和两者都不是的相对比较简单，比较复杂点的是'\**'的判断，因为'**'是匹配零个或多个元素，所以用到了递归。

``` java
public class Solution {
    public static boolean isMatch(String s, String p) {
        if ((s == null || s.length() == 0) && (p == null || p.length() == 0)) {
            return true;
        }
        if ((p == null || p.length() == 0) && s.length() > 0) {
            return false;
        }

        char preChar = 0;
        boolean havePreChar = false;
        int sIndex = 0;
        for (int i = 0; i < p.length(); i++) {
            if (p.charAt(i) == '.') {
                if (i < p.length() - 1 && p.charAt(i + 1) == '*') {
                    preChar = p.charAt(i);
                    havePreChar = true;
                    continue;
                } else {
                    if (sIndex < s.length()) {
                        preChar = s.charAt(sIndex);
                        sIndex++;
                        havePreChar = true;
                        continue;
                    } else {
                        return false;
                    }
                }
            }
            if (p.charAt(i) == '*') {
                if (!havePreChar) {
                    return false;
                }
                if (sIndex == s.length()) {
                    if (p.length() - 1 == i) {
                        return true;
                    } else {
                        return isMatch("", p.substring(i + 1));
                    }
                } else {
                    if (preChar == '.') {
                        if (i == p.length() - 1) {
                            return true;
                        }
                        while (sIndex < s.length()) {
                            boolean result = isMatch(s.substring(sIndex), p.substring(i + 1));
                            if (result) {
                                return true;
                            }
                            sIndex++;
                            continue;
                        }
                    } else {
                        while (sIndex < s.length()) {
                            if (s.charAt(sIndex) == preChar) {
                                boolean result = isMatch(s.substring(sIndex), p.substring(i + 1));
                                if (result) {
                                    return true;
                                }
                                sIndex++;
                                continue;
                            } else {
                                break;
                            }

                        }
                    }
                    havePreChar = false;
                }
            }
            if (p.charAt(i) != '*' && p.charAt(i) != '.') {
                if (i < p.length() - 1 && p.charAt(i + 1) == '*') {
                    preChar = p.charAt(i);
                    havePreChar = true;
                    continue;
                } else {
                    if (sIndex == s.length() || s.charAt(sIndex) != p.charAt(i)) {
                        return false;
                    } else {
                        sIndex++;
                        havePreChar = false;
                        continue;
                    }
                }
            }
        }

        if (sIndex < s.length()) {
            return false;
        }

        return true;
    }

    public static void main(String[] args) {
        String s = "", p = "c*c*"; // true
        System.out.println(isMatch(s, p));
    }
}
```
