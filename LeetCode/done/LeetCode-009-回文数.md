#### 回文数

> 题目描述：给你一个整数 x ，如果 x 是一个回文整数，返回 true ；否则，返回 false 。
>
> 回文数是指正序（从左向右）和倒序（从右向左）读都是一样的整数。例如，121 是回文，而 123 不是。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/palindrome-number/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：前后遍历

> 如果是负数，直接返回false；
>
> 否则，将整数转化为字符串，左右2个指针left和right同时从前后开始遍历，如果相应left和right的值不同，则返回false，知道left大于right，遍历结束。

```java
public class Solution {
    public static boolean isPalindrome(int x) {
        if (x < 0) {
            return false;
        }
        String xStr = String.valueOf(x);
        int left = 0, right = xStr.length() - 1;
        while (left <= right) {
            if (xStr.charAt(left) == xStr.charAt(right)) {
                left++;
                right--;
            } else {
                return false;
            }
        }
        return true;
    }

    public static void main(String[] args) {
        System.out.println(isPalindrome(1231321));
    }
}
```
