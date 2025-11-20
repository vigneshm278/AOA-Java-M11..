
# EX 1B Power of 2
## AIM:
To write a Java program to for given constraints.Given an integer n, return true if it is a power of two. Otherwise, return false.

An integer n is a power of two, if there exists an integer x such that n == 2x.

## Algorithm
1. Start the program and import the `Scanner` class to take input from the user.
2. Read an integer `n` using the `Scanner` object.
3. Check if `n` is less than or equal to 0 — if true, return `false`.
4. Use the bitwise operation `(n & (n - 1)) == 0` to check if `n` is a power of two.
5. Print `true` if the condition holds, otherwise print `false`.


## Program:
```
/*
Program to implement Reverse a String
Developed by: K ABHINESWAR REDDY
Register Number:  212223040084
*/
import java.util.Scanner;

public class Solution {

    public boolean isPowerOfTwo(int n) {
     if (n<=0){
         return false;
     }
     return (n&(n-1))==0;
     
     
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Solution sol = new Solution();
        int n = scanner.nextInt();

        boolean result = sol.isPowerOfTwo(n);
        System.out.println(result);

        scanner.close();
    }
}

```

## Output:

<img width="419" height="186" alt="image" src="https://github.com/user-attachments/assets/f9c06840-da38-4cd9-ba23-55b69673e617" />


## Result:
The program successfully implemented and the expected output is verified.
