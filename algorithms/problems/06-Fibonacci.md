## Description
Find the Nth number in Fibonacci sequence.

A Fibonacci sequence is defined as follow:

* The first two numbers are 0 and 1.
* The i th number is the sum of i-1 th number and i-2 th number.

The first ten numbers in Fibonacci sequence is:

0, 1, 1, 2, 3, 5, 8, 13, 21, 34 ...

### Notice

The Nth fibonacci number won't exceed the max value of signed 32-bit integer in the test cases.

### Example
Given 1, return 0

Given 2, return 1

Given 10, return 34



## Naive Solution
```java
public int fibonacci(int n) {
        // write your code here
//        if(1 == n) return 0;
//        if(2 == n) return 1;
//        int left = fibonacci(n - 1);
//        int right = fibonacci(n - 2);
//        return left + right;
        int a = 0;
        int b = 1;
        for(int i = 0 ; i < n - 1; i++){
            int c = a + b;
            a = b;
            b = c;
        }
        return a;
    }
```