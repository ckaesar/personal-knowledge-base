#### 加一

> 题目描述：给定一个由 整数 组成的 非空 数组所表示的非负整数，在该数的基础上加一。
>
> 最高位数字存放在数组的首位， 数组中每个元素只存储单个数字。
>
> 你可以假设除了整数 0 之外，这个整数不会以零开头。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/plus-one/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：遍历数组

> 初始化一个进位的值**addOne**为1，从数组digits的最后一位往前开始遍历：
>
> - 把当前位置的值和**addOne**相加；
> - 如果相加结果为10，则产生进位，**addOne**设置为1，并且当前为值的值设置为0；
> - 如果相加结果小于10，则不会产生进位，**addOne**设置为0，并且当前为值的值设置为相加结果；
> - 直到遍历结束。
>
> 遍历结束后，如果**addOne**为0，则直接返回digits；如果**addOne**为1，则把1放在digits的第一位，然后返回。

```java
import java.util.Arrays;

public class LeetCode_066 {
    public static int[] plusOne(int[] digits) {
        int addOne = 1;
        for (int i = digits.length - 1; i >= 0; i--) {
            if (addOne + digits[i] == 10) {
                addOne = 1;
                digits[i] = 0;
            } else {
                digits[i] = addOne + digits[i];
                addOne = 0;
            }
        }
        if (addOne == 1) {
            int[] result = new int[digits.length + 1];
            result[0] = addOne;
            for (int i = 0; i < digits.length; i++) {
                result[i + 1] = digits[i];
            }
            return result;
        } else {
            return digits;
        }
    }

    public static void main(String[] args) {
        int[] digits = new int[]{4, 3, 2, 1};
        Arrays.stream(plusOne(digits)).forEach(digit -> {
            System.out.print(digit + " ");
        });
    }
}
```

> 【每日寄语】 *清晨，带着一颗雀跃的心醒来，感谢又一个充满爱的日子。* 

