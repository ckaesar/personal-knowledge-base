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

###### 
