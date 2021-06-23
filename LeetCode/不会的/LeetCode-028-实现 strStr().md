#### 实现 strStr()

> 题目描述：实现 strStr() 函数。
>
> 给你两个字符串 haystack 和 needle ，请你在 haystack 字符串中找出 needle 字符串出现的第一个位置（下标从 0 开始）。如果不存在，则返回  -1 。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/implement-strstr/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：暴力破解法

> - 首先，如果needle为空，直接返回0；如果 haystack 为空 或者 haystack 的长度 小于 needle 的长度，直接返回-1；
> - 否则，从 haystack 的第一位开始跟 needle 进行匹配，如果匹配不上，则往后继续遍历haystack，直到遍历完成，就能得到结果。

###### 解法二：KMP算法

> 描述

```java
package com.kaesar.leetcode;

public class LeetCode_028 {
    /**
     * 暴力破解法
     * @param haystack
     * @param needle
     * @return
     */
    public static int strStr(String haystack, String needle) {
        if (needle == null || needle.length() == 0) {
            return 0;
        }
        if (haystack == null || haystack.length() == 0 || haystack.length() < needle.length()) {
            return -1;
        }
        int first = 0;
        while (first < haystack.length()) {
            int matchCount = 0;
            for (int i = 0; i < needle.length() && (i + first) < haystack.length(); i++) {
                if (needle.charAt(i) == haystack.charAt(i + first)) {
                    matchCount++;
                } else {
                    break;
                }
            }
            if (matchCount == needle.length()) {
                return first;
            } else {
                first++;
            }
        }
        return -1;
    }

    /**
     * KMP算法：todo
     * @param haystack
     * @param needle
     * @return
     */
    public static int strStr2(String haystack, String needle) {
        return -1;
    }

    public static void main(String[] args) {
        System.out.println(strStr("mississippi", "issi"));
    }
}

```

> 【每日寄语】 *在最美的年华，做最喜欢的事情，别辜负了美好时光，借时光之手，暖一处花开，借一方晴空，拥抱梦想。* 
