#### 最长公共前缀

> 题目描述：编写一个函数来查找字符串数组中的最长公共前缀。
>
> 如果不存在公共前缀，返回空字符串 ""。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/longest-common-prefix/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：字符数组法

> 把第一个字符串放到字符数组chars中，从第二个字符串开始，挨个字符遍历比较，得到每次不相等的索引位置p，如果p-1小于0，则表示没有公共前缀；遍历后面的字符串，重复这一过程。  中间只要p-1小于0，直接返回空字符串，没有公共前缀。 遍历结束后，获取chars数组中从0到p-1位置的字符，返回即为最长公共前缀。

```java
public class Solution {
    public static String longestCommonPrefix(String[] strs) {
        if (strs == null || strs.length == 0 || strs[0] == null || strs[0].length() == 0) {
            return "";
        }
        char[] chars = strs[0].toCharArray();
        int maxIndex = strs[0].length() - 1;
        for (int i = 1; i < strs.length && maxIndex >= 0; i++) {
            String curStr = strs[i];
            if (curStr == null || curStr.length() == 0) {
                return "";
            }
            int curMax = maxIndex;
            for (int j = 0; j < curStr.length() && j <= curMax && maxIndex >= 0; j++) {
                if (curStr.charAt(j) != chars[j]) {
                    maxIndex = j - 1;
                    break;
                } else {
                    maxIndex = j;
                }
            }
        }
        if (maxIndex < 0) {
            return "";
        }
        StringBuilder result = new StringBuilder();
        for (int i = 0; i <= maxIndex; i++) {
            result.append(chars[i]);
        }
        return result.toString();
    }

    public static void main(String[] args) {
        System.out.println(longestCommonPrefix(new String[]{"flower", "flow", "flight"}));
        System.out.println(longestCommonPrefix(new String[]{"ab", "a"}));
    }
}
```
