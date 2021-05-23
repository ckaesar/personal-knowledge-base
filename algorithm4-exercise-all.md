## chapter1

#### section1

###### Exercise1

```java
/**
 * @author chengk
 * @date 2021-05-14 15:05:39
 */
public class Exercise1 {
    public static void main(String[] args) {
        int resultA = (0 + 15) / 2;
        double resultB = 2.0e-6 * 100000000.1;
        boolean resultC = true && false || true && true;

        System.out.println("a) " + resultA);
        System.out.println("b) " + resultB);
        System.out.println("c) " + resultC);
    }
}

/*
 * 输出为：
 * a) 7
 * b) 200.0000002
 * c) true
 */
```

###### Exercise2

```java
/**
 * @author chengk
 * @date 2021-05-14 15:10:04
 */
public class Exercise2 {
    public static void main(String[] args) {
        double resultA = (1 + 2.236) / 2;
        double resultB = 1 + 2 + 3 + 4.0;
        boolean resultC = 4.1 >= 4;
        String resultD = 1 + 2 + "3";

        System.out.println("a) " + resultA);
        System.out.println("b) " + resultB);
        System.out.println("c) " + resultC);
        System.out.println("d) " + resultD);
    }
}

/*
 * 输出为：
 * a) 1.618
 * b) 10.0
 * c) true
 * d) 33
 */
```

###### Exercise3

```java
/**
 * @author chengk
 * @date 2021-05-14 15:14:49
 */
public class Exercise3 {
    public static void main(String[] args) {
        // 从请求命令中读取参数
        int integer1 = Integer.parseInt(args[0]);
        int integer2 = Integer.parseInt(args[1]);
        int integer3 = Integer.parseInt(args[2]);

        isEqual(integer1, integer2, integer3);
    }

    private static void isEqual(int num1, int num2, int num3) {
        if (num1 == num2 && num2 == num3) {
            System.out.println("Equal");
        } else {
            System.out.println("Not equal");
        }
    }
}
```

###### Exercise5

```java
/**
 * @author chengk
 * @date 2021-05-14 15:18:52
 */
public class Exercise5 {
    public static void main(String[] args) {
        isStrictlyBetween0And1(1.12, 1.33);
        System.out.println("Expected: false");

        isStrictlyBetween0And1(0.2, 1);
        System.out.println("Expected: false");

        isStrictlyBetween0And1(0.5, 0.75);
        System.out.println("Expected: true");
    }

    private static void isStrictlyBetween0And1(double x, double y) {
        if (x > 0 && x < 1 && y > 0 && y < 1) {
            System.out.println("true");
        } else {
            System.out.println("false");
        }
    }
}

/*
 * 输出为：
 * false
 * Expected: false
 * false
 * Expected: false
 * true
 * Expected: true
 */
```

###### Exercise6

```java
/**
 * 斐波那契数列
 * 
 * @author chengk
 * @date 2021-05-14 15:21:26
 */
public class Exercise6 {
    public static void main(String[] args) {
        int f = 0;
        int g = 1;

        for (int i = 0; i <= 15; i++) {
            System.out.println(f);
            f = f + g;
            g = f - g;
        }
    }
}

/*
 * 输出为：
 * 0
 * 1
 * 1
 * 2
 * 3
 * 5
 * 8
 * 13
 * 21
 * 34
 * 55
 * 89
 * 144
 * 233
 * 377
 * 610
 */
```

###### Exercise7

```java
/**
 * @author chengk
 * @date 2021-05-14 15:23:56
 */
public class Exercise7 {
    public static void main(String[] args) {
        funcA();
        funcB();
        funcC();
    }

    private static void funcA() {
        double t = 9.0;

        while (Math.abs(t - 9.0 / t) > .001) {
            t = (9.0 / t + t) / 2.0;
        }

        System.out.printf("%.5f\n", t);
    }

    private static void funcB() {
        int sum = 0;

        for (int i = 1; i < 1000; i++) {
            for (int j = 0; j < i; j++) {
                sum++;
            }
        }

        System.out.println(sum);
    }

    private static void funcC() {
        int sum = 0;

        for (int i = 1; i < 1000; i *= 2) {
            for (int j = 0; j < 1000; j++) {
                sum++;
            }
        }

        System.out.println(sum);
    }
}

/*
 * 输出为：
 * 3.00009
 * 499500
 * 10000
 */
```

###### Exercise8

```java
/**
 * @author chengk
 * @date 2021-05-17 13:25:35
 */
public class Exercise8 {
    public static void main(String[] args) {
        System.out.println('b');
        System.out.println('b' + 'c');
        System.out.println((char) ('a' + 4));
    }
}

/*
 * 输出为：
 * b
 * 197
 * e
 */
```

###### Exercise9

```java
/**
 * @author chengk
 * @date 2021-05-18 09:41:28
 */
public class Exercise9 {
    public static void main(String[] args) {
        System.out.println(intToBinary(32));
        System.out.println("Expected: 100000");
    }

    private static String intToBinary(int n) {
        String result = "";

        while (n > 0) {
            result = n % 2 + result;

            n /= 2;
        }

        return result;
    }
}

/*
 * 输出为：
 * 100000
 * Expected: 100000
 */
```

###### Exercise11

```java
/**
 * @author chengk
 * @date 2021-05-18 09:43:58
 */
public class Exercise11 {
    public static void main(String[] args) {
        boolean[][] array = {{true, false, true},
                        {false, true, false}};
        printArray(array);
    }

    private static void printArray(boolean[][] array) {
        for (int i = 0; i < array.length; i++) {
            for (int j = 0; j < array[i].length; j++) {

                if (array[i][j]) {
                    System.out.print("+");
                } else {
                    System.out.print("-");
                }

            }
            System.out.println();
        }
    }
}

/*
 * 输出为：
 * +-+
 * -+-
 */
```

###### Exercise12

```java
/**
 * @author chengk
 * @date 2021-05-18 09:54:15
 */
public class Exercise12 {
    public static void main(String[] args) {
        int[] a = new int[10];

        for (int i = 0; i < 10; i++) {
            a[i] = 9 - i;
        }

        for (int i = 0; i < 10; i++) {
            a[i] = a[a[i]];
        }

        for (int i = 0; i < 10; i++) {
            System.out.println(i);
        }
    }
}

/*
 * 输出为：
 * 0
 * 1
 * 2
 * 3
 * 4
 * 5
 * 6
 * 7
 * 8
 * 9
 */
```

###### Exercise13

```java
/**
 * @author chengk
 * @date 2021-05-18 09:57:22
 */
public class Exercise13 {
    public static void main(String[] args) {
        int[][] mat = {
                        {1, 2, 3},
                        {4, 5, 6}
        };

        transpose(mat);
        System.out.println("\nExpected:");
        System.out.println("1 4 \n" +
                        "2 5 \n" +
                        "3 6 ");
    }

    private static void transpose(int[][] mat) {

        int[][] newMat = new int[mat[0].length][mat.length];

        for (int i = 0; i < mat.length; i++) {
            for (int j = 0; j < mat[0].length; j++) {
                newMat[j][i] = mat[i][j];
            }
        }
        print(newMat);
    }

    private static void print(int[][] mat) {
        for (int i = 0; i < mat.length; i++) {
            for (int j = 0; j < mat[0].length; j++) {
                System.out.print(mat[i][j] + " ");
            }
            System.out.println();
        }
    }
}

/*
 * 输出为：
 * 1 4
 * 2 5
 * 3 6
 * 
 * Expected:
 * 1 4
 * 2 5
 * 3 6
 */
```

###### Exercise14

```java
/**
 * @author chengk
 * @date 2021-05-19 13:18:49
 */
public class Exercise14 {
    public static void main(String[] args) {
        System.out.print(lg(15));
        System.out.println("\nExpected: 3");
    }

    private static int lg(int n) {

        int logInt = 0;

        while (n > 0) {
            logInt++;

            n /= 2;
        }

        return logInt - 1;
    }
}

/*
 * 输出为：
 * 3
 * Expected: 3
 */
```

###### Exercise15

```java
/**
 * @author chengk
 * @date 2021-05-19 13:21:05
 */
public class Exercise15 {
    public static void main(String[] args) {
        int[] a = {1, 2, 3, 4};

        int[] newArrA = histogram(a, 5);

        int[] b = {1, 2, 3, 9};

        int[] newArrB = histogram(b, 7);

        for (int i = 0; i < newArrA.length; i++) {
            System.out.print(newArrA[i] + " ");
        }
        System.out.println("\nExpected: 0 1 1 1 1");

        System.out.println();

        for (int i = 0; i < newArrB.length; i++) {
            System.out.print(newArrB[i] + " ");
        }
        System.out.println("\nExpected: 0 1 1 1 0 0 0");
    }

    private static int[] histogram(int[] a, int m) {
        int[] newArr = new int[m];

        for (int i = 0; i < a.length; i++) {
            if (a[i] < m) {
                newArr[a[i]]++;
            }
        }

        return newArr;
    }
}

/*
 * 输出为：
 * 0 1 1 1 1
 * Expected: 0 1 1 1 1
 * 
 * 0 1 1 1 0 0 0
 * Expected: 0 1 1 1 0 0 0
 */
```

###### Exercise16

```java
/**
 * @author chengk
 * @date 2021-05-21 12:19:26
 */
public class Exercise16 {
    public static void main(String[] args) {
        System.out.println(exR1(6));
    }

    private static String exR1(int n) {
        if (n <= 0) {
            return "";
        }
        return exR1(n - 3) + n + exR1(n - 2) + n;
    }
}

/*
 * 输出为：
 * 311361142246
 */
```

###### Exercise18

```java
/**
 * @author chengk
 * @date 2021-05-21 12:23:21
 */
public class Exercise18 {
    public static void main(String[] args) {
        System.out.println(mystery(2, 25));
        System.out.println(mystery(3, 11));
        System.out.println(mystery2(2, 25));
        System.out.println(mystery2(3, 11));
    }

    // mystery(a,b) computes a * b
    private static int mystery(int a, int b) {
        if (b == 0) {
            return 0;
        }
        if (b % 2 == 0) {
            return mystery(a + a, b / 2);
        }
        return mystery(a + a, b / 2) + a;
    }

    // mystery2(a,b) computes a^b
    private static int mystery2(int a, int b) {
        if (b == 0) {
            return 1;
        }
        if (b % 2 == 0) {
            return mystery2(a * a, b / 2);
        }
        return mystery2(a * a, b / 2) * a;
    }
}

/*
 * 输出为：
 * 50
 * 33
 * 33554432
 * 177147
 */
```

###### Exercise19

```java
/**
 * @author chengk
 * @date 2021-05-21 12:29:59
 */
public class Exercise19 {
    public static void main(String[] args) {
        // for (int n = 0; n < 90; n++) {
        // StdOut.println(n + " - " + F(n));
        // }

        for (int n = 0; n < 90; n++) {
            int[] arr;

            if (n == 0 || n == 1) {
                arr = new int[2];
            } else {
                arr = new int[n + 1];
            }

            arr[0] = 0;
            arr[1] = 1;

            System.out.println(n + " - " + enhancedF(n, arr));
        }
    }

    private static int F(int n) {
        if (n == 0)
            return 0;
        if (n == 1)
            return 1;
        return F(n - 1) + F(n - 2);
    }

    private static int enhancedF(int n, int[] arr) {
        if (n == 0)
            return arr[0];
        if (n == 1)
            return arr[1];

        for (int i = 2; i <= n; i++) {
            arr[i] = arr[i - 2] + arr[i - 1];
        }

        return arr[n];
    }
}

/*
 * 输出为：
 * 0 - 0
 * 1 - 1
 * 2 - 1
 * 3 - 2
 * 4 - 3
 * 5 - 5
 * 6 - 8
 * 7 - 13
 * 8 - 21
 * 9 - 34
 * 10 - 55
 * 11 - 89
 * 12 - 144
 * 13 - 233
 * 14 - 377
 * 15 - 610
 * 16 - 987
 * 17 - 1597
 * 18 - 2584
 * 19 - 4181
 * 20 - 6765
 * 21 - 10946
 * 22 - 17711
 * 23 - 28657
 * 24 - 46368
 * 25 - 75025
 * 26 - 121393
 * 27 - 196418
 * 28 - 317811
 * 29 - 514229
 * 30 - 832040
 * 31 - 1346269
 * 32 - 2178309
 * 33 - 3524578
 * 34 - 5702887
 * 35 - 9227465
 * 36 - 14930352
 * 37 - 24157817
 * 38 - 39088169
 * 39 - 63245986
 * 40 - 102334155
 * 41 - 165580141
 * 42 - 267914296
 * 43 - 433494437
 * 44 - 701408733
 * 45 - 1134903170
 * 46 - 1836311903
 * 47 - -1323752223
 * 48 - 512559680
 * 49 - -811192543
 * 50 - -298632863
 * 51 - -1109825406
 * 52 - -1408458269
 * 53 - 1776683621
 * 54 - 368225352
 * 55 - 2144908973
 * 56 - -1781832971
 * 57 - 363076002
 * 58 - -1418756969
 * 59 - -1055680967
 * 60 - 1820529360
 * 61 - 764848393
 * 62 - -1709589543
 * 63 - -944741150
 * 64 - 1640636603
 * 65 - 695895453
 * 66 - -1958435240
 * 67 - -1262539787
 * 68 - 1073992269
 * 69 - -188547518
 * 70 - 885444751
 * 71 - 696897233
 * 72 - 1582341984
 * 73 - -2015728079
 * 74 - -433386095
 * 75 - 1845853122
 * 76 - 1412467027
 * 77 - -1036647147
 * 78 - 375819880
 * 79 - -660827267
 * 80 - -285007387
 * 81 - -945834654
 * 82 - -1230842041
 * 83 - 2118290601
 * 84 - 887448560
 * 85 - -1289228135
 * 86 - -401779575
 * 87 - -1691007710
 * 88 - -2092787285
 * 89 - 511172301
 */
```

###### Exercise20

```java
/**
 * @author chengk
 * @date 2021-05-21 12:34:17
 */
public class Exercise20 {
    public static void main(String[] args) {
        System.out.println("ln(5!) = " + lnFactorial(5));
        System.out.println("Expected: 4.787491742782046");
    }

    private static double lnFactorial(int n) {
        if (n == 1) {
            return 0;
        }
        return Math.log(n) + lnFactorial(n - 1);
    }
}

/*
 * 输出为：
 * ln(5!) = 4.787491742782046
 * Expected: 4.787491742782046
 */
```

###### Exercise21

```java
/**
 * @author chengk
 * @date 2021-05-21 13:17:03
 */
public class Exercise21 {

    // Parameters example:
    // Rene 2 1
    // Bacon 4 3
    // Abcdef 6 2
    public static void main(String[] args) {
        System.out.printf("%8s %7s %7s %7s", "Names", "Number1", "Number2", "Result\n");

        Scanner in = new Scanner(System.in);

        while (in.hasNextLine()) {
            String line = in.nextLine();
            String[] values = line.split(" ");
            formattedPrint(values);
        }
    }

    private static void formattedPrint(String[] values) {
        System.out.printf("%8s", values[0]);
        System.out.printf("%8s", values[1]);
        System.out.printf("%8s", values[2]);

        double value1 = Double.parseDouble(values[1]);
        double value2 = Double.parseDouble(values[2]);
        double result = value1 / value2;
        System.out.printf("%7.3f \n", result);
    }

}
```

###### Exercise22

```java
import java.util.Arrays;

/**
 * @author chengk
 * @date 2021-05-21 13:18:15
 */
public class Exercise22 {
    public static void main(String[] args) {
        int arr[] = {1, 2, 3, 4, 5, 6, 7};
        int key = 2;

        Arrays.sort(arr);

        int index = rank(key, arr, 0, arr.length - 1, 0);

        System.out.println();
        System.out.println("Index: " + index);

        System.out.println("\nExpected:");
        System.out.println("lo: 0 - hi: 6\n" +
                        " lo: 0 - hi: 2\n" +
                        "Index: 1");
    }

    /**
     * 二分查找
     * 
     * @param key
     * @param arr
     * @param lo
     * @param hi
     * @param depth
     * @return
     */
    private static int rank(int key, int[] arr, int lo, int hi, int depth) {

        if (depth != 0) {
            System.out.println();
        }

        for (int i = 0; i < depth; i++) {
            System.out.print(" ");
        }

        System.out.print("lo: " + lo + " - hi: " + hi);

        if (lo <= hi) {
            int mid = lo + (hi - lo) / 2;

            if (key < arr[mid]) {
                return rank(key, arr, lo, mid - 1, ++depth);
            } else if (key > arr[mid]) {
                return rank(key, arr, mid + 1, hi, ++depth);
            } else {
                return mid;
            }
        } else {
            return -1;
        }
    }
}

/*
 * 输出为：
 * lo: 0 - hi: 6
 * lo: 0 - hi: 2
 * Index: 1
 * 
 * Expected:
 * lo: 0 - hi: 6
 * lo: 0 - hi: 2
 * Index: 1
 */
```

###### 

