#### 无重复字符的最长子串

> 题目描述：给定一个字符串，请你找出其中不含有重复字符的 最长子串 的长度。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：滑动窗口法

> 从第一个字符开始，有一个指针p记录不重复的第一个字符，然后依次向后遍历，把已经出现的字符放在List里，先判断是否出现过，如果出现过，则计算当前位置和p指针的位置之差，即当前不重复的子串的长度，和最长的count对比，如果大于count，则替换之，然后把p指针向右移动一位，继续向后遍历，知道最后一个字符，返回count值即为最长子串的长度。

```java
import java.util.ArrayList;
import java.util.List;

public class Solution {
    public static int lengthOfLongestSubstring(String s) {
        if (s == null || s.length() == 0) {
            return 0;
        }

        int count = 0;
        int charAt = 0;
        List<Character> charList = new ArrayList<Character>(s.length());
        for (int i = 0; i < s.length(); i++) {
            List<Character> subList = charList.subList(charAt, i);
            if (subList.contains(s.charAt(i))) {
                charAt = charList.lastIndexOf(s.charAt(i)) + 1;
            }
            if (i + 1 - charAt > count) {
                count = i + 1 - charAt;
            }
            charList.add(s.charAt(i));
        }
        return count;
    }

    public static void main(String[] args) {
        System.out.println(lengthOfLongestSubstring("abcabcbb"));
    }
}
```
