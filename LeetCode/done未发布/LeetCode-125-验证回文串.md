#### 验证回文串

> 题目描述：给定一个字符串，验证它是否是回文串，只考虑字母和数字字符，可以忽略字母的大小写。
>
> 说明：本题中，我们将空字符串定义为有效的回文串。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/valid-palindrome/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：字符串遍历

> 主要是使用一些库函数来遍历字符串。
>
> 首先，如果s是空或者s的长度为1，则直接返回true；
>
> 否则，从s的第一位front和最后一位end开始遍历，遍历过程为：
>
> - 如果front对应位置的字符frontChar不是字母或数字字符，则front向后挪一位，进行下一轮遍历；
> - 如果end对应位置的字符endChar不是字母或数字字符，则end向前挪一位，进行下一轮遍历；
> - 如果front和end对应位置的字符都是字母或者数字字符，首先，如果frontChar或endChar是字母，则先将之转化为大写字符（因为不需要区分大小写），然后比较frontChar和endChar是否相等，如果不相等，则返回false；如果相等，则front向后挪一位，同时end向前挪一位，进行下一轮遍历。
> - 遍历结束的条件就是front不小于end。

```java
public class LeetCode_125 {
    public static boolean isPalindrome(String s) {
        if (s == null || s.length() == 1) {
            return true;
        }
        int front = 0, end = s.length() - 1;
        while (front <= end) {
            char frontChar = s.charAt(front);
            char endChar = s.charAt(end);
            if ((frontChar >= 'a' && frontChar <= 'z') || (frontChar >= 'A' && frontChar <= 'Z') ||
                    (frontChar >= '0' && frontChar <= '9')) {
                if ((endChar >= 'a' && endChar <= 'z') || (endChar >= 'A' && endChar <= 'Z') ||
                        (endChar >= '0' && endChar <= '9')) {
                    if (Character.isAlphabetic(frontChar)) {
                        frontChar = Character.toUpperCase(frontChar);
                    }
                    if (Character.isAlphabetic(endChar)) {
                        endChar = Character.toUpperCase(endChar);
                    }
                    if (frontChar != endChar) {
                        return false;
                    } else {
                        front++;
                        end--;
                    }
                } else {
                    end--;
                }
            } else {
                front++;
            }
        }
        return true;
    }

    public static void main(String[] args) {
        System.out.println(isPalindrome("A man, a plan, a canal: Panama"));
    }
}
```

> 【每日寄语】 *人生似水岂无崖，浮云吹作雪，世味煮成茶。* 

