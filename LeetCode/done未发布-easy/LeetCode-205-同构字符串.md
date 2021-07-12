#### 同构字符串

> 题目描述：给定两个字符串 s 和 t，判断它们是否是同构的。
>
> 如果 s 中的字符可以按某种映射关系替换得到 t ，那么这两个字符串是同构的。
>
> 每个出现的字符都应当映射到另一个字符，同时不改变字符的顺序。不同字符不能映射到同一个字符上，相同字符只能映射到同一个字符上，字符可以映射到自己本身。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/isomorphic-strings/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：利用HashMap

> 首先如果s和t都为null，则直接返回true；如果s和t只有一个是null，则直接返回false；
>
> 用mappings记录出现过的字符映射关系，遍历s和t的所有字符，遍历过程如下：
>
> - 如果mappings的key中包含s当前的字符，判断对应key的值是否等于t当前的字符，如果不相等，则返回false；
> - 如果mappings的key中不包含s当前的字符，由于相同字符只能映射到同一个字符上，判断mappings的values是否包含t当前的字符，如果包含，则返回false；如果不包含，则将s当前的字符和t当前的作为对应的key和value放入mappings，继续下一遍遍历。
>
> 最后如果遍历完了，没有匹配不成功的，则说明是同构的，返回true。

```java
import java.util.HashMap;
import java.util.Map;

public class LeetCode_205 {
    public static boolean isIsomorphic(String s, String t) {
        if (s == null && t == null) {
            return true;
        }
        if ((s == null && t != null) || (s != null && t == null)) {
            return false;
        }
        Map<Character, Character> mappings = new HashMap<>();
        for (int i = 0; i < s.length(); i++) {
            if (mappings.keySet().contains(s.charAt(i))) {
                if (!(mappings.get(s.charAt(i)) == t.charAt(i))) {
                    return false;
                }
            } else {
                if (mappings.values().contains(t.charAt(i))) {
                    return false;
                } else {
                    mappings.put(s.charAt(i), t.charAt(i));
                }
            }
        }
        return true;
    }

    public static void main(String[] args) {
        System.out.println(isIsomorphic("paper", "title"));
    }
}
```

> 【每日寄语】 *世界上所有的惊喜和好运，都是你累积的温柔和善良。* 

