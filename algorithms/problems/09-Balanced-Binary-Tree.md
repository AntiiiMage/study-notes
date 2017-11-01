# Balanced Binary Tree

## Description
Given a binary tree, determine if it is height-balanced.

For this problem, a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of every node never differ by more than 1.

## Example

Given binary tree A = {3,9,20,#,#,15,7}, B = {3,#,20,15,7}
The binary tree A is a height-balanced binary tree, but B is not.



## Naive Solution
```java
    public String addBinary(String a, String b) {
        StringBuilder tempSum = new StringBuilder(a);
        StringBuilder tempCarries = new StringBuilder(b);
        while(tempSum.length() > 0 && tempCarries.length() > 0){
            if(tempSum.length() > tempCarries.length()) {
                merge(tempSum, tempCarries);
            }else{
                merge(tempCarries, tempSum);
            }

        }
        if(tempCarries.length() > 0) return tempCarries.toString();
        if(tempSum.length() > 0) return tempSum.toString();
        return "0";
    }

    /**
     * @param sum
     * @param carries
     */
    private void merge(StringBuilder sum, StringBuilder carries) {
        int flag = 0;
        while (flag < carries.length()) {
            int comparIndexInSum = sum.length() - 1 - flag;
            int comparIndexInCarries = carries.length() - 1 - flag;
            char c1 = sum.charAt(comparIndexInSum);
            char c2 = carries.charAt(comparIndexInCarries);
            if (c1 == c2) {
                sum.setCharAt(comparIndexInSum, '0');
                if (c2 == '1') {
                    carries.setCharAt(comparIndexInCarries, '1');
                }
            } else {
                sum.setCharAt(comparIndexInSum, '1');
                carries.setCharAt(comparIndexInCarries, '0');
            }
            flag++;
        }
        removeFirstZeros(sum);
        removeFirstZeros(carries);
        if(carries.length() > 0) carries.append('0');

    }

    private void removeFirstZeros(StringBuilder sb) {
        while (sb.length() > 0) {
            if (sb.charAt(0) == '0') {
                sb.deleteCharAt(0);
            } else
                break;
        }
    }
```

## Elegant Way
```java
public String addBinary(String a, String b) {
        // Write your code here
        String ans = "";

        int carry = 0;
        for (int i = a.length() - 1, j = b.length() - 1; i >= 0 || j >= 0; i--, j--) {
            int sum = carry;
            sum += (i >= 0) ? a.charAt(i) - '0' : 0;
            sum += (j >= 0) ? b.charAt(j) - '0' : 0;
            ans = (sum % 2) + ans;
            carry = sum / 2;
        }
        if (carry != 0) {
            ans = carry + ans;
        }
        return ans;
    }
```