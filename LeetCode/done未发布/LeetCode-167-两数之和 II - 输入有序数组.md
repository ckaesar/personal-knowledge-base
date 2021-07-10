#### 两数之和 II - 输入有序数组

> 题目描述：给定一个已按照 升序排列  的整数数组 numbers ，请你从数组中找出两个数满足相加之和等于目标数 target 。
>
> 函数应该以长度为 2 的整数数组的形式返回这两个数的下标值。numbers 的下标 从 1 开始计数 ，所以答案数组应当满足 1 <= answer[0] < answer[1] <= numbers.length 。
>
> 你可以假设每个输入只对应唯一的答案，而且你不可以重复使用相同的元素。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/two-sum-ii-input-array-is-sorted/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：二分查找

> 首先，如果数组numbers只有2个数字，直接判断是否满足并返回结果；
>
> 如果numbers的长度大于2，则用二分查找的方式解决。
>
> 首先，固定第一个数字的位置first，first从第一位开始，然后用二分查找法从数字的`first+1`位到数字的最后一位，查找数字`target - numbers[first]`是否存在，如果存在，则返回结果；如果不存在，则将first后移一位，重新查找，直到first移动到数字的倒数第二位，最后如果没有找到符合条件的结果，返回null。

```java
public class LeetCode_167 {
    public static int[] twoSum(int[] numbers, int target) {
        if (numbers.length == 2) {
            if (numbers[0] + numbers[1] == target) {
                return new int[]{1, 2};
            } else {
                return null;
            }
        }
        for (int first = 0; first < numbers.length; first++) {
            int targetNum = target - numbers[first];
            int result = find(numbers, first + 1, numbers.length - 1, targetNum);
            if (result != -1) {
                return new int[]{first + 1, result + 1};
            }
        }
        return null;
    }

    /**
     * 二分法查找第二个数字
     *
     * @param numbers
     * @param left
     * @param right
     * @param target
     * @return 返回-1说明没有找到；否则返回对应的索引位置
     */
    public static int find(int[] numbers, int left, int right, int target) {
        while (left <= right) {
            int mid = (left + right) / 2;
            if (numbers[mid] > target) {
                right--;
            } else if (numbers[mid] == target) {
                return mid;
            } else {
                left++;
            }

        }
        return -1;
    }

    public static void main(String[] args) {
        int[] numbers = new int[]{2, 7, 11, 15};
        int[] result = twoSum(numbers, 9);
        System.out.println(result[0] + " " + result[1]);
    }
}
```

> 【每日寄语】 *你一定要站在自己所热爱的世界里，闪闪发亮。* 

