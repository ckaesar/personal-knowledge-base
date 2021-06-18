#### 电话号码的字母组合

> 题目描述：给定一个仅包含数字 2-9 的字符串，返回所有它能表示的字母组合。答案可以按 任意顺序 返回。
>
> 给出数字到字母的映射如下（与电话按键相同）。注意 1 不对应任何字母。
>
> ![img](https://assets.leetcode-cn.com/aliyun-lc-upload/original_images/17_telephone_keypad.png)
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/letter-combinations-of-a-phone-number/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：解法一

> 首先，将所有的映射列出来**mappings**，然后，遍历**digits**中的每一个字符，从**mappings**中取出对应的字母，拼到一起，最终遍历完后把结果放到结果集里面，返回。

```java
import java.util.*;

public class Solution {

    private static Map<Integer, List<Character>> mappings = new HashMap<>();

    static {
        mappings.put(2, new ArrayList<>(Arrays.asList('a', 'b', 'c')));
        mappings.put(3, new ArrayList<>(Arrays.asList('d', 'e', 'f')));
        mappings.put(4, new ArrayList<>(Arrays.asList('g', 'h', 'i')));
        mappings.put(5, new ArrayList<>(Arrays.asList('j', 'k', 'l')));
        mappings.put(6, new ArrayList<>(Arrays.asList('m', 'n', 'o')));
        mappings.put(7, new ArrayList<>(Arrays.asList('p', 'q', 'r', 's')));
        mappings.put(8, new ArrayList<>(Arrays.asList('t', 'u', 'v')));
        mappings.put(9, new ArrayList<>(Arrays.asList('w', 'x', 'y', 'z')));
    }

    public static List<String> letterCombinations(String digits) {
        if (digits == null || digits.length() == 0) {
            return new ArrayList<>();
        }
        Set<String> result = new HashSet<>();
        for (Character temp : mappings.get(Integer.valueOf(String.valueOf(digits.charAt(0))))) {
            result.add(temp.toString());
        }
        for (int i = 1; i < digits.length(); i++) {
            Set<String> tempResult = result;
            result = new HashSet<>();
            for (String s : tempResult) {
                for (Character character : mappings.get(Integer.valueOf(String.valueOf(digits.charAt(i))))) {
                    if (!result.contains(s + character)) {
                        result.add(s + character);
                    }
                }
            }
        }
        return new ArrayList<>(result);
    }

    public static void main(String[] args) {
        List<String> strings = letterCombinations("2");
        for (String string : strings) {
            System.out.print(string + "--");
        }
    }
}
```

> 【每日寄语】*睡去昨天的疲惫，忘却昨天的烦恼，睁开今天的双眼，打开今天的美好。* 

