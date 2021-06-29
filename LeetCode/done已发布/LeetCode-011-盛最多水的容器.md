#### 盛最多水的容器

> 题目描述：给你 n 个非负整数 a~1~，a~2~，...，a~n~，每个数代表坐标中的一个点 (i, a~i~) 。在坐标内画 n 条垂直线，垂直线 i 的两个端点分别为 (i, a~i~) 和 (i, 0) 。找出其中的两条线，使得它们与 x 轴共同构成的容器可以容纳最多的水。 
>
> 说明：你不能倾斜容器。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/container-with-most-water/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：暴力求解法

> 双重循环求解所有可能的值，取得最大的值。 
>
> **这个方法能得到结果，但是效率极低，提交时超时了。**

###### 解法二：双指针法

> 从左右两边开始遍历，2个指针p和q分别指向左右两边的值，计算容量，和最大值比较，然后p和q中指向的较小的值的指针移动一位，因为宽度一定容量取决于高度，如果移动较大的值，则不会获得更大的容量。
>
> 重复这个过程，知道p和q指针相交，得到最大容量值。

```java
public class Solution {
    /**
     * 方法一：暴力求解法
     *
     * @param height
     * @return
     */
    public static int maxArea(int[] height) {
        int max = 0;
        for (int i = 0; i < height.length - 1; i++) {
            for (int j = i + 1; j < height.length; j++) {
                int length = j - i;
                int high = Math.min(height[i], height[j]);
                if (length * high > max) {
                    max = length * high;
                }
            }
        }
        return max;
    }

    /**
     * 双指针法
     *
     * @param height
     * @return
     */
    public static int maxArea2(int[] height) {
        int left = 0, right = height.length - 1, max = 0;
        while (left < right) {
            int length = right - left;
            int high = Math.min(height[left], height[right]);
            if (length * high > max) {
                max = length * high;
            }
            if (height[left] > height[right]) {
                right--;
            } else {
                left++;
            }
        }
        return max;
    }

    public static void main(String[] args) {
        int[] height = new int[]{1, 8, 6, 2, 5, 4, 8, 3, 7};
        System.out.println(maxArea(height));
        System.out.println(maxArea2(height));
    }
}
```
