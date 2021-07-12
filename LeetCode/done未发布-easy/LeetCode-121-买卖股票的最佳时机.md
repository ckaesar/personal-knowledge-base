#### 买卖股票的最佳时机

> 题目描述：给定一个数组 prices ，它的第 i 个元素 prices[i] 表示一支给定股票第 i 天的价格。
>
> 你只能选择 某一天 买入这只股票，并选择在 未来的某一个不同的日子 卖出该股票。设计一个算法来计算你所能获取的最大利润。
>
> 返回你可以从这笔交易中获取的最大利润。如果你不能获取任何利润，返回 0 。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：动态规划

> 如果prices为空或者prices只有一个值，直接返回0；
>
> 否则，声明一个变量result为0，buyPrice为prices的第一个值，从prices的第2个值开始遍历：
>
> - 如果当前值等于buyPrice，则跳过处理下一个值；
> - 如果当前值小于buyPrice，则更新buyPrice为当前值；
> - 如果当前值大于buyPrice，判断当前值和buyPrice的差值是否比result大，如果更大，则更新result的值。
>
> 遍历完成后，返回result。

```java
public class LeetCode_121 {
    public static int maxProfit(int[] prices) {
        if (prices == null || prices.length < 2) {
            return 0;
        }
        int result = 0;
        int buyPrice = prices[0];
        for (int i = 1; i < prices.length; i++) {
            if (prices[i] == buyPrice) {
                continue;
            } else if (prices[i] < buyPrice) {
                buyPrice = prices[i];
            } else {
                if (prices[i] - buyPrice > result) {
                    result = prices[i] - buyPrice;
                }
            }
        }
        return result;
    }

    public static void main(String[] args) {
        int[] prices = new int[]{7, 1, 5, 3, 6, 4};
        System.out.println(maxProfit(prices));
    }
}
```

> 【每日寄语】 *三月悄然去，四月翩然来。最美四月天，莫负春光美。前路皆坦荡，万事皆可期。* 

