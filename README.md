
# EX 1A Print All Numbers 
## AIM:
To Write a Java program that takes an integer input N from the user and prints all the numbers from 1 to N, separated by spaces, on a single line..

## Algorithm
1. Start the program and import the `Scanner` class to take user input.
2. Create a `Scanner` object to read an integer input `N` from the user.
3. Check if `N` is greater than 0; if not, display `"Invalid input. N must be greater than 0."`
4. Use a `for` loop to iterate from 1 to `N`.
5. Print each number separated by a space on the same line.


## Program:
```
/*
Program to implement Reverse a String
Developed by: Vignesh M
Register Number: 212223240176
*/

import java.util.*;
public class PrintNum{
    public static void main(String[] args){
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        for(int i=1;i<=n;i++){
            System.out.print(i+" ");
        }
    }
}
```

## Output:
<img width="491" height="159" alt="image" src="https://github.com/user-attachments/assets/ef5e3fdf-c4da-46c2-b207-43343d9ccad8" />



## Result:
The program successfully print all the numbers from 1 to N. 




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
Developed by: Vignesh M
Register Number: 212223240176
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



# EX 1C Valid Pairs using Brute Force Approach
## AIM:
To write a Java program to for given constraints.
Given an integer array nums and an integer k, return the number of pairs (i, j) where i < j such that |nums[i] - nums[j]| == k.

The value of |x| is defined as:

x if x >= 0.
-x if x < 0.

## Algorithm
1. Start the program and import the `Scanner` class to take user input.
2. Read the number of elements `n` and then input the array elements.
3. Read the integer value `k` representing the required absolute difference.
4. Use nested loops to compare each pair `(i, j)` where `i < j` and check if `|nums[i] - nums[j]| == k`.
5. Count and display the total number of valid pairs that satisfy the condition.

## Program:
```
/*
Program to implement Reverse a String
Developed by: Vignesh M
Register Number: 212223240176
*/
import java.util.Scanner;
public class CountPairsWithDifference {
    public static int countKDifference(int[] nums, int k) {        
          int count = 0;
          for (int i = 0; i < nums.length; i++)
          {
          for (int j = i + 1; j < nums.length; j++) 
          {
         if (Math.abs(nums[i] - nums[j]) == k) 
         {
            count++;
        }
    }
}
       return count;    
        
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] nums = new int[n];
        for (int i = 0; i < n; i++) {
            nums[i] = sc.nextInt();
        }
        int k = sc.nextInt();
        int result = countKDifference(nums, k);
        System.out.println(result);
        sc.close();
    }
}

```

## Output:
<img width="449" height="279" alt="image" src="https://github.com/user-attachments/assets/b95f37b4-158a-4748-abd7-3ec4b3a32a9d" />



## Result:
The program successfully implemented and the expected output is verified.




# EX 1D Sorted Array using Divide and Conquer Approach.
## AIM:
To write a Java program to for given constraints.
Given two sorted arrays nums1 and nums2 of size m and n respectively, return the median of the two sorted arrays.

The overall run time complexity should be O(log (m+n)).

## Algorithm
1. Start the program and import the `Scanner` class to take user input.
2. Read the sizes of the two sorted arrays and store their elements in `nums1` and `nums2`.
3. Calculate the total length of both arrays combined.
4. Use the `getMin()` method to sequentially retrieve the smallest elements from both arrays until reaching the median position.
5. Display the median value of the merged sorted arrays as the final output.
  

## Program:
```
/*
Program to implement Reverse a String
Developed by: Vignesh M
Register Number: 212223240176
*/

import java.util.Scanner;

public class Solution {
    private int p1 = 0, p2 = 0;

    // Get the smaller value between nums1[p1] and nums2[p2], and move the pointer forward
    private int getMin(int[] nums1, int[] nums2) {
        if (p1 < nums1.length && p2 < nums2.length) {
            return nums1[p1] < nums2[p2] ? nums1[p1++] : nums2[p2++];
        } else if (p1 < nums1.length) {
            return nums1[p1++];
        } else if (p2 < nums2.length) {
            return nums2[p2++];
        }
        return -1; // Should not reach here if input is valid
    }

    // Main logic to find median of two sorted arrays
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
       //Type code here...
       int m=nums1.length;
        int n=nums2.length;
        int total=m+n;
        if(total%2==0)
        {
            for(int i=0;i<total/2-1;++i)
            {
                getMin(nums1,nums2);
            }
            return (double)(getMin(nums1,nums2)+getMin(nums1,nums2))/2;
        }
        else
        {
            for(int i=0;i<total/2;++i)
            {
                getMin(nums1,nums2);
            }
            return getMin(nums1,nums2);
        }
    }

    // Main method with user input
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Solution sol = new Solution();

        // Input for nums1
        //System.out.print("Enter size of first sorted array: ");
        int m = sc.nextInt();
        int[] nums1 = new int[m];
        //System.out.println("Enter " + m + " sorted integers for first array:");
        for (int i = 0; i < m; i++) {
            nums1[i] = sc.nextInt();
        }

        // Input for nums2
        //System.out.print("Enter size of second sorted array: ");
        int n = sc.nextInt();
        int[] nums2 = new int[n];
        //System.out.println("Enter " + n + " sorted integers for second array:");
        for (int i = 0; i < n; i++) {
            nums2[i] = sc.nextInt();
        }

        // Find and display the median
        double median = sol.findMedianSortedArrays(nums1, nums2);
        System.out.println("Median of the two sorted arrays = " + median);
        
        sc.close();
    }
}

```

## Output:
<img width="813" height="349" alt="image" src="https://github.com/user-attachments/assets/08406be8-2afd-44a0-9914-d05d68b1ea25" />



## Result:
The program successfully implemented and the expected output is verified.



# EX 1E Integer Multiplication using Divide and Conquer Approach(Strassen’s algorithm).
## AIM:
To write a Java program to for given constraints.
You are given two square matrices A and B of size n × n (where n is a power of 2). Your task is to compute their matrix product using Strassen’s Matrix Multiplication algorithm and return the resulting matrix.

Unlike traditional matrix multiplication which takes O(n3)O(n^3)O(n3) time, Strassen’s algorithm improves this by reducing the number of recursive multiplications from 8 to 7, achieving approximately O(n2.81)O(n^{2.81})O(n2.81) complexity.
## Algorithm
1. Start the program and import the `Scanner` class to take user input.
2. Read the matrix size `n` and input the two square matrices `A` and `B`.
3. Divide both matrices into four equal submatrices recursively.
4. Use Strassen’s algorithm to compute the seven matrix products and combine them to form the resulting matrix.
5. Display the final multiplied matrix as the output.


## Program:
```
/*
Program to implement Reverse a String
Developed by: Vignesh M
Register Number: 212223240176
*/
import java.util.Scanner;

public class StrassenMatrix {

    // Add two matrices
    static int[][] add(int[][] A, int[][] B) {
        int n = A.length;
        int[][] C = new int[n][n];
        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++)
                C[i][j] = A[i][j] + B[i][j];
        return C;
    }

    // Subtract matrix B from A
    static int[][] subtract(int[][] A, int[][] B) {
        int n = A.length;
        int[][] C = new int[n][n];
        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++)
                C[i][j] = A[i][j] - B[i][j];
        return C;
    }

    // Strassen recursive multiplication
    static int[][] strassen(int[][] A, int[][] B) {
        //Type code here...
           
        int n = A.length;
        int[][] C = new int[n][n];

        // Base case
        if (n == 1) {
            C[0][0] = A[0][0] * B[0][0];
            return C;
        }

        int newSize = n / 2;
        int[][] A11 = new int[newSize][newSize];
        int[][] A12 = new int[newSize][newSize];
        int[][] A21 = new int[newSize][newSize];
        int[][] A22 = new int[newSize][newSize];

        int[][] B11 = new int[newSize][newSize];
        int[][] B12 = new int[newSize][newSize];
        int[][] B21 = new int[newSize][newSize];
        int[][] B22 = new int[newSize][newSize];

        // Divide matrices into 4 submatrices
        for (int i = 0; i < newSize; i++) {
            for (int j = 0; j < newSize; j++) {
                A11[i][j] = A[i][j];
                A12[i][j] = A[i][j + newSize];
                A21[i][j] = A[i + newSize][j];
                A22[i][j] = A[i + newSize][j + newSize];

                B11[i][j] = B[i][j];
                B12[i][j] = B[i][j + newSize];
                B21[i][j] = B[i + newSize][j];
                B22[i][j] = B[i + newSize][j + newSize];
            }
        }

        // Compute the 7 products
        int[][] M1 = strassen(add(A11, A22), add(B11, B22));
        int[][] M2 = strassen(add(A21, A22), B11);
        int[][] M3 = strassen(A11, subtract(B12, B22));
        int[][] M4 = strassen(A22, subtract(B21, B11));
        int[][] M5 = strassen(add(A11, A12), B22);
        int[][] M6 = strassen(subtract(A21, A11), add(B11, B12));
        int[][] M7 = strassen(subtract(A12, A22), add(B21, B22));

        // Compute C11, C12, C21, C22
        int[][] C11 = add(subtract(add(M1, M4), M5), M7);
        int[][] C12 = add(M3, M5);
        int[][] C21 = add(M2, M4);
        int[][] C22 = add(subtract(add(M1, M3), M2), M6);

        // Combine results into one matrix
        for (int i = 0; i < newSize; i++) {
            for (int j = 0; j < newSize; j++) {
                C[i][j] = C11[i][j];
                C[i][j + newSize] = C12[i][j];
                C[i + newSize][j] = C21[i][j];
                C[i + newSize][j + newSize] = C22[i][j];
            }
        }

        return C;
    }

    

    // Function to print matrix
    static void printMatrix(int[][] matrix) {
        for (int[] row : matrix) {
            for (int val : row)
                System.out.print(val + " ");
            System.out.println();
        }
    }

    // Main method to get input and run Strassen multiplication
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Read size of matrix
        //System.out.print("Enter matrix size (power of 2): ");
        int n = sc.nextInt();

        int[][] A = new int[n][n];
        int[][] B = new int[n][n];

        // Input Matrix A
        //System.out.println("Enter elements of matrix A:");
        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++)
                A[i][j] = sc.nextInt();

        // Input Matrix B
        //System.out.println("Enter elements of matrix B:");
        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++)
                B[i][j] = sc.nextInt();

        // Multiply using Strassen
        int[][] result = strassen(A, B);

        // Output the result matrix
        System.out.println("Result of Strassen Matrix Multiplication:");
        printMatrix(result);
    }
}


```

## Output:
<img width="893" height="297" alt="image" src="https://github.com/user-attachments/assets/3262a3b9-02ed-4ee9-b08d-fc0dd0eab14f" />



## Result:
The program successfully implemented and the expected output is verified.



 
