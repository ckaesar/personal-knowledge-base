#### 有效的数独

> 题目描述：请你判断一个 9x9 的数独是否有效。只需要 根据以下规则 ，验证已经填入的数字是否有效即可。
>
> 数字 1-9 在每一行只能出现一次。
> 数字 1-9 在每一列只能出现一次。
> 数字 1-9 在每一个以粗实线分隔的 3x3 宫内只能出现一次。（请参考示例图）
> 数独部分空格内已填入了数字，空白格用 '.' 表示。
>
> 注意：
>
> - 一个有效的数独（部分已被填充）不一定是可解的。
> - 只需要根据以上规则，验证已经填入的数字是否有效即可。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/valid-sudoku/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：数组遍历

> 分为3种情况判断，分别是行判断、列判断、3*3宫内判断，判断逻辑是利用Set判重，如果在同一行（或同一列、同一宫内）有重复的数字，则返回false；如果都符合，最后返回true。

```java
import javafx.util.Pair;

import java.util.ArrayList;
import java.util.HashSet;
import java.util.List;
import java.util.Set;

public class LeetCode_036 {
    public static List<Pair<Integer, Integer>> all = new ArrayList<>();

    static {
        all.add(new Pair<>(0, 0));
        all.add(new Pair<>(0, 3));
        all.add(new Pair<>(0, 6));
        all.add(new Pair<>(3, 0));
        all.add(new Pair<>(3, 3));
        all.add(new Pair<>(3, 6));
        all.add(new Pair<>(6, 0));
        all.add(new Pair<>(6, 3));
        all.add(new Pair<>(6, 6));
    }

    public static boolean isValidSudoku(char[][] board) {
        // 行判断
        for (int i = 0; i < board.length; i++) {
            Set<Character> nums = new HashSet<>();
            for (int j = 0; j < board[i].length; j++) {
                if (board[i][j] != '.' && !nums.add(board[i][j])) {
                    return false;
                }
            }
        }
        // 列判断
        for (int i = 0; i < board.length; i++) {
            Set<Character> nums = new HashSet<>();
            for (int j = 0; j < board.length; j++) {
                if (board[j][i] != '.' && !nums.add(board[j][i])) {
                    return false;
                }
            }
        }
        // 宫内判断
        for (Pair<Integer, Integer> integerIntegerPair : all) {
            Set<Character> nums = new HashSet<>();
            for (int x = integerIntegerPair.getKey(); x < integerIntegerPair.getKey() + 3; x++) {
                for (int y = integerIntegerPair.getValue(); y < integerIntegerPair.getValue() + 3; y++) {
                    if (board[x][y] != '.' && !nums.add(board[x][y])) {
                        return false;
                    }
                }
            }
        }

        return true;
    }

    public static void main(String[] args) {
        char[][] board = new char[][]{{'5', '3', '.', '.', '7', '.', '.', '.', '.'}
                , {'6', '.', '.', '1', '9', '5', '.', '.', '.'}
                , {'.', '9', '8', '.', '.', '.', '.', '6', '.'}
                , {'8', '.', '.', '.', '6', '.', '.', '.', '3'}
                , {'4', '.', '.', '8', '.', '3', '.', '.', '1'}
                , {'7', '.', '.', '.', '2', '.', '.', '.', '6'}
                , {'.', '6', '.', '.', '.', '.', '2', '8', '.'}
                , {'.', '.', '.', '4', '1', '9', '.', '.', '5'}
                , {'.', '.', '.', '.', '8', '.', '.', '7', '9'}};
        System.out.println(isValidSudoku(board));
    }
}
```

> 【每日寄语】 *希望生活给予你风浪的同时，也给你阳光作为回报，让你感受到这个世界的温柔。* 

