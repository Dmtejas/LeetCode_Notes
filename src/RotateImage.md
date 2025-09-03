<h1 align="center">Rotate Image (2D Matrix)</h1>

## Problem Description : 
You are given an n x n 2D matrix representing an image, rotate the image by 90 degrees (clockwise).

You have to rotate the image in-place, which means you have to modify the input 2D matrix directly. DO NOT allocate another 2D matrix and do the rotation.

 

Example 1:
![alt text](mat1.jpg)
Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]
Output: [[7,4,1],[8,5,2],[9,6,3]]

## My Approach
* First, We will copy our entire array into another matrix to keep the elements even after the swap,
* We will have two variables start and end. The idea is copiedMatrix[j][i] that means column wise will be copied into actual matrix[i][end] where It will be from row wise but from the last element that's why end will be equal to length - 1 in every iteration of the outer loop

* For example - (0, 2) is copied by (0, 0) then (0, 1) is copied by (1, 0) then (0, 0) is copied by the position (2, 0)

* Then outer loop incremnets then - (1, 2) is copied by position (0, 1) then (1, 1) is copied by (1, 1) and then (1, 0) is copied from (2, 1) and then continue until the end of the matrix

### Time complexity - O(N^2)

```java
class Solution {
    public void rotate(int[][] matrix) {
        int length = matrix.length;
        int[][] copiedMatrix = new int[length][length];
        for(int i=0;i<length;i++) {
            for(int j=0;j<length;j++) {
                copiedMatrix[i][j] = matrix[i][j];
            }
        }
        for(int j=0;j<length;j++) {
            int end = length-1;
            for(int i=0;i<length;i++) {
                matrix[j][end] = copiedMatrix[i][j];
                end--;
            }
        }
    }
}
```

