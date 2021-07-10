#### x 的平方根

> 题目描述：实现 int sqrt(int x) 函数。
>
> 计算并返回 x 的平方根，其中 x 是非负整数。
>
> 由于返回类型是整数，结果只保留整数的部分，小数部分将被舍去。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/sqrtx/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：二分法

> 首先设置一个最小值min为1，最大值max为46340是`Math.sqrt(Integer.MAX_VALUE)`的约等值，然后mid是中间值：
>
> - 如果`mid*mid`等于x，则直接返回**mid**；
> - 如果`mid*mid`小于x，则将min设置为mid+1，重新进行下一轮判断；
> - 如果`mid*mid`大于x，则将max设置为mid-1，重新进行下一轮判断；
> - 终止条件就是max不大于min。
>
> 最后返回mid。

```java
public class LeetCode_069 {
    public static int mySqrt(int x) {
        int min = 1, max = 46340, mid = 1;
        mid = (min + max) / 2;
        while (min < max) {
            int temp = mid * mid;
            if (temp == x) {
                return mid;
            } else if (temp < x) {
                min = mid + 1;
            } else {
                max = mid - 1;
            }
            mid = (min + max) / 2;
        }
        return mid;
    }

    public static void main(String[] args) {
        System.out.println(mySqrt(4));
    }
}
```

> 【每日寄语】 *你今天的努力，是幸运的伏笔，当下的付出，是明日的花开。* 
