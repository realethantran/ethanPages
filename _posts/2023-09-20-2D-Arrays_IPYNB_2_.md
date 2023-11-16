---
layout: post
title: 2D Arrays
description: Lesson on 2D Arrays
courses: {'csa': {'week': 1}}
type: hacks
toc: True
comments: True
---

# APCSA Unit 8 College Board Learning Objectives and Standards

## Learning Objectives

The objective of today's lesson is to...

- Learn about 2D arrays, their use cases, and how to create them.

## Essential Knowledge

College Board wants you to know...

- How to declare/initialize 2D arrays.
- How to determine their size.
- How to access and update the values of a 2D array.
- How to traverse/access elements of a 2D array using nested iteration statements. 
- How nested iteration statements can be used to traverse 2D arrays in “row-major order” vs “column-major order.”
- How to create algorithms that require the use of 2D array traversals.

## Warm Up

Answer the following questions as a group or individually. Write down your answers in your hacks notebook.

- What are 2D arrays?
- How are 2D arrays organized?
- What are some real-world examples of 2D arrays?


## The Basics/Recap

2D arrays, and higher dimension arrays overall, can be thought of as just an array that's made up of other arrays or an array of arrays. One way of looking at 2D arrays is by thinking of them as a chess board. They have rows and columns, and every element is identified via row or column number or index.

Below is an illustration of a 2D array:
![2D Array Image](https://raw.githubusercontent.com/The-Code-Monkeys/Monkeys38/main/images/2dArray.png)



## 1) How to declare/initialize 2D arrays

Initializing 2D arrays can be done in multiple different ways. Note: In Java whenever we declare an array we must specify the datatype of the elements in the array. The most common include:

1) Initializing and populating the array in one go:


```Java
public class Main {
    public static void main(String[] args) {
        int[][] Array1 = { // 2d Array of integers
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };

        for (int i = 0; i < Array1.length; i++) { // Loop through the rows
            for (int j = 0; j < Array1[i].length; j++) { // Loop through the columns
                System.out.print(Array1[i][j] + " "); // Print out the element
            }
            System.out.println(); // Print a new line
        }
    }
}

Main.main(null)
```

    1 2 3 
    4 5 6 
    7 8 9 



```Java
public class Main {
    public static void main(String[] args){
    String[][] Array2 = { // 2d Array of strings
        {"one", "two", "three"},
        {"four", "five", "six"},
        {"seven", "eight", "nine"}
    };
    
    for (int i = 0; i < Array2.length; i++) { // Loop through the rows
        for (int j = 0; j < Array2[i].length; j++) { // Loop through the columns
            System.out.print(Array2[i][j] + " "); // Print out the element
        }
            System.out.println(); // Print a new line
        }
    }
}

Main.main(null)

```

    one two three 
    four five six 
    seven eight nine 



```Java
public class Main {
    public static void main(String[] args){
        Object[][] Array3 = { // 2d Array of objects allows for having varying types in the same 2d array
            {1, "two", 3.0},
            {4, "five", 6.0},
            {7, "eight", 9.0}
        };

        for (int i = 0; i < Array3.length; i++) { // Loop through the rows
            for (int j = 0; j < Array3[i].length; j++) { // Loop through the columns
                System.out.print(Array3[i][j] + " "); // Print out the element
            }
            System.out.println(); // Print a new line
        }
    }
} 

Main.main(null)
```

    1 two 3.0 
    4 five 6.0 
    7 eight 9.0 


2) Creating an empty 2D array and then assigning values to individual elements as through accessing and changing each value via their corresponding row and column index: 


```Java
public class Main {
    public static void main(String[] args){
        int[][] myArray = new int[3][3]; // Defines the size of the array, think of the first number as x and the second number as y, for rows and columns.
        
        myArray[0][0] = 1; //  Maps the desired value to a specific point in the array, think of this as an (x,y) coordinate.
        myArray[0][1] = 2;
        myArray[0][2] = 3;
        myArray[1][0] = 4;
        myArray[1][1] = 5;
        myArray[1][2] = 6;
        myArray[2][0] = 7;
        myArray[2][1] = 8;
        myArray[2][2] = 9;

        for (int i = 0; i < myArray.length; i++) { // Loop through the rows
            for (int j = 0; j < myArray[i].length; j++) { // Loop through the columns
                System.out.print(myArray[i][j] + " "); // Print out the element
            }
            System.out.println(); // Print a new line
        }
    }
}

Main.main(null)
```

    1 2 3 
    4 5 6 
    7 8 9 


3) Using a nested loop to manually populate each element:


```Java
public class Main {
        public static void main(String[] args){
        int rows = 3; // Define number of rows and columns here as variables
        int columns = 4;
        int[][] myArray = new int[rows][columns];  // Create an array based on the values of the aforementioned variables.
        // Create a nested for loop that iterates based on the number of rows and columns.
        for (int i = 0; i < rows; i++) { 
            for (int j = 0; j < columns; j++) {
                // You can assign values to each element here
                myArray[i][j] = i * columns + j;

            }
        }
        // Print out the array
        for (int i = 0; i < myArray.length; i++) { // Loop through the rows
            for (int j = 0; j < myArray[i].length; j++) { // Loop through the columns
                System.out.print(myArray[i][j] + " "); // Print out the element
            }
            System.out.println(); // Print a new line
        }
    }
}

Main.main(null)
```

    0 1 2 3 
    4 5 6 7 
    8 9 10 11 


### Popcorn Hack: Create a 2D Array with random values


```Java
import java.util.Random;

public class Main {
    public static void main(String[] args) {
        int rows = 3; 
        int cols = 4; 
        int[][] newArray = new int[rows][cols];
        
        // create Random object
        Random rand = new Random();
        
        // fill array with random values
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                newArray[i][j] = rand.nextInt(100); // random integers between 0 and 99
            }
        }
        
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                System.out.print(newArray[i][j] + " ");
            }
            System.out.println(); // move to next row
        }
    }
}

Main.main(null);
```

    7 93 0 35 
    17 6 72 28 
    88 25 32 69 


## 2) Accessing and updating the values of a 2D array

In order to access the value of a 2D array, you must use array indexing notation, which is as follows:

```java
// Say you have myArray:
int[][] myArray = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

// To access the third number of the third column, use array indexing notation:
int desiredValue = myArray[2][2]; // REMEMBER BASE 0!

// And print the value:
System.out.print(desiredValue);
```
Assign the "coordinate point" of the desired value as a variable, using the "x" value for row number and "y" value for column number.


```Java
// Executable Version:
public class Main {
    public static void main(String[] args) {
        int[][] myArray = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };

        int desiredValue = myArray[2][2];

        System.out.print(desiredValue);

    }
}

Main.main(null)
```

    9

In order to update the value of a specific point in a 2D array, assign the desired value to a specific point in the array, denoted by array indexing notation:

```java
// Say you have myArray:
int[][] myArray = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

// To change the third number of the third column, use array indexing notation:
int desiredValue = 10; // Define what you want the new value to be.
myArray[2][2] = desiredValue; // Use array indexing notation to insert the desired value at the specific desired point.

// And print the updated value at the desired location:
System.out.print(myArray[2][2]);
```


```Java
// Executable Version:
public class Main {
    public static void main(String[] args) {
        int[][] myArray = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };

        int desiredValue = 10; 
        myArray[2][2] = desiredValue; 

        System.out.print(myArray[2][2]);

    }
}

Main.main(null)
```

    10

### Popcorn Hack: Print all the values on this 2D Array and update the last value to be 12.


```Java
// basic scaffolding to get you started :)
public class Main {
    public static void main(String[] args) {
        int[][] myArray = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };

        // print all values in the 2D array
        for (int i = 0; i < myArray.length; i++) {
            for (int j = 0; j < myArray[i].length; j++) {
                System.out.print(myArray[i][j] + " ");
            }
        }
        
        // update last value to 12
        myArray[myArray.length - 1][myArray[myArray.length - 1].length - 1] = 12;

        // print array after update
        System.out.println("\nArray after updating the last value to 12:");
        for (int i = 0; i < myArray.length; i++) {
            for (int j = 0; j < myArray[i].length; j++) {
                System.out.print(myArray[i][j] + " ");
            }
        }
    }
}
Main.main(null)
```

    1 2 3 4 5 6 7 8 9 
    Array after updating the last value to 12:
    1 2 3 4 5 6 7 8 12 



## 3) Traversing 2D Arrays 
- When we traverse a regular array we use a singular for loop to iterate through each element in the array. However, when we have 2D array we need to use nested for loops to iterate through each element in the array. Below is the difference between the two:

```java
// Regular array traversal
for(int i = 0; i < myArray.length; i++){
    System.out.println(myArray[i]);
}

// 2D array traversal
for(int i = 0; i < myArray.length; i++){
    for(int j = 0; j < myArray[i].length; j++){
        System.out.println(myArray[i][j]);
    }
}
```


```Java
public class Main {
    public static void main(String[] args){
        int[] myArray = {1, 2, 3, 4, 5, 6, 7, 8, 9}; // 1d array of integers
        int[][] my2dArray = { // 2d array of integers
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };
        
        System.out.println("1D Array\n"); // Print a new line

        for (int i = 0; i < myArray.length; i++) { // Loop through the 1d array
            System.out.print(myArray[i] + " "); // Print out the element
        }

        System.out.println("\n\n2D Array\n"); // Print a new line
        

        for (int i = 0; i < my2dArray.length; i++) { // First traversal condition
            for (int j = 0; j < my2dArray[i].length; j++) { // Second traversal condition
                System.out.print(my2dArray[i][j] + " "); // Print out the element
            }
            System.out.println(); // Print a new line
        }
    }
}

Main.main(null)
```

    1D Array
    
    1 2 3 4 5 6 7 8 9 
    
    2D Array
    
    1 2 3 
    4 5 6 
    7 8 9 


### Popcorn Hack: Traverse the following array and only print the values divisible by 7


```Java
public class Main {
    public static void main(String[] args) {
        int[][] myArray = {
            {1, 2, 11},
            {14, 5, 21},
            {25, 28, 70}
        };

        for (int i = 0; i < myArray.length; i++) {
            for (int j = 0; j < myArray[i].length; j++) {
                if (myArray[i][j] % 7 == 0) {
                    System.out.println(myArray[i][j]);
                }
            }
        }
    }
}
Main.main(null)
```

    14
    21
    28
    70


## Row-Major Order vs Column-Major Order

### Row-Major-Order: 
- The outer loop traverses the rows and the inner loop traverses the columns or the elements within the rows. Here is an example bellow of row-major order traversals:


```Java
public class rowMajorOrder {
    public static void main(String[] args){
        int[][] my2dArray = { // 2d array of integers
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };
        
        System.out.println("Row Major Order\n"); // Print a new line

        for (int i = 0; i < my2dArray.length; i++) { // First traversal traverses by rows condition

            for (int j = 0; j < my2dArray[i].length; j++) { // Iterates through the columns
                if (my2dArray[i][j] % 2 == 0) { // If the element is even
                } else{
                    my2dArray[i][j] = 0; // Otherwise set the element to 0
                }
                System.out.print(my2dArray[i][j] + " "); // Print out the element
            }
            System.out.println(); // Print a new line
        }
    }
}

rowMajorOrder.main(null)
```

    Row Major Order
    
    0 2 0 
    4 0 6 
    0 8 0 



```Java
// Variation that only applies to forward row-wise major traversal

public class rowMajorTraversalAlt{
    public static void rowMajorOrderAlt(int[][] array){
        for (int[] row: array){
            for (int element: row){
                System.out.print(element + " ");
            }
            System.out.println();
        }
    }
}

rowMajorTraversalAlt.rowMajorOrderAlt(new int[][]{
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
});
```

    1 2 3 
    4 5 6 
    7 8 9 


### Column-Major-Order: 
- The outer loop will traverse through the columns and the inner loop will traverses through each element in the columns or the rows. Here is an example bellow of column-major order traversals: 


```Java
public class columnWiseTraversal{
    public static void main(String[] args){
        int[][] my2dArray = { // 2d array of integers
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };
        
        System.out.println("Column Wise Traversal\n"); // Print a new line

        for (int j = 0; j < my2dArray[0].length; j++) { // First traversal traverses by columns condition

            for (int i = 0; i < my2dArray.length; i++) { // Iterates through the rows
                if (my2dArray[j][i] % 2 == 0) { // If the element is even
                } else{
                    my2dArray[j][i] = 0; // Otherwise set the element to 0
                }
                System.out.print(my2dArray[j][i] + " "); // Print out the element
            }
            System.out.println(); // Print a new line
        }
    }
}

columnWiseTraversal.main(null)

// Both row and column wise traversals in our examples do the same thing, but in different orders. However for certain functions one may be easier to use than the other.  

```

    Column Wise Traversal
    
    0 2 0 
    4 0 6 
    0 8 0 


# Algoirthms 2D Array Java

Linear search is a simple and sequential searching algorithm. It is used to find whether a particular element is present in the array or not by traversing every element in the array. While searching in the 2D array is exactly the same but here all the cells need to be traversed In this way, any element is searched in a 2D array. 

Below is the implementation for linear search in 2D arrays


```Java
// Linear Search in 2D arrays
import java.util.Arrays;
 
public class GFG {
    public static void main(String[] args)
    {
        int arr[][] = { { 3, 12, 9 },
                        { 5, 2, 89 },
                        { 90, 45, 22 } };
        int target = 89;
        int ans[] = linearSearch(arr, target);
        System.out.println("Element found at index: "
                           + Arrays.toString(ans));
    }
 
    static int[] linearSearch(int[][] arr, int target)
    {
        for (int i = 0; i < arr.length; i++) {
            for (int j = 0; j < arr[i].length; j++) {
                if (arr[i][j] == target) {
                    return new int[] { i, j };
                }
            }
        }
        return new int[] { -1, -1 };
    }
}
```

Summary:
Linear Search involves iterating through all elements in the matrix.
Binary Search is applicable when the matrix is sorted.
Binary Search treats the 2D matrix as a 1D array by converting the indices.
These searching algorithms are fundamental and widely used. Practice applying them to different scenarios to solidify your understanding. Additionally, consider exploring more advanced searching techniques for 2D arrays as you become more proficient.


```Java
public class Main {
    public static int[] binarySearch(int[][] matrix, int target) {
        int rows = matrix.length;
        int cols = matrix[0].length;
        int left = 0;
        int right = rows * cols - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;
            int midValue = matrix[mid / cols][mid % cols];

            if (midValue == target) {
                return new int[] {mid / cols, mid % cols};
            }

            if (midValue < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }

        return new int[] {-1, -1}; // Target not found
    }
}

```

### Binary Search in a 2D Array: 

Binary search is an efficient method of searching in an array. Binary search works on a sorted array. At each iteration the search space is divided in half, this is the reason why binary search is more efficient than linear search


```Java
// Binary Search on sorted 2D array
import java.util.Arrays;
 
class GFG {
 
    static int[] findAns(int[][] arr, int target)
    {
        int row = 0;
        int col = arr[row].length - 1;
        while (row < arr.length && col >= 0) {
            if (arr[row][col] == target) {
                return new int[] { row, col };
            }
 
            // Target lies in further row
            if (arr[row][col] < target) {
                row++;
            }
            // Target lies in previous column
            else {
                col--;
            }
        }
        return new int[] { -1, -1 };
    }
 
    // Driver Code
    public static void main(String[] args)
    {
 
        // Binary search in sorted matrix
        int arr[][] = { { 1, 2, 3, 4 },
                        { 5, 6, 7, 8 },
                        { 9, 10, 11, 12 } };
        int[] ans = findAns(arr, 12);
        System.out.println("Element found at index: "
                           + Arrays.toString(ans));
    }
}
```

## Popcorn Hack - EXTRA!
Create a program that implements binary search on 2D Arrays.


```Java
public class BinarySearch {

    // binary search within a sorted column of a 2D array
    public static boolean binarySearchColumn(int[][] matrix, int target, int col) {
        int rows = matrix.length;
        int low = 0;
        int high = rows - 1;

        while (low <= high) {
            int mid = low + (high - low) / 2;

            if (matrix[mid][col] == target) {
                return true; // Element found
            } else if (matrix[mid][col] < target) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }

        return false; // if element not found
    }

    public static void main(String[] args) {
        int[][] matrix = {
            {1, 3, 5},
            {7, 9, 11},
            {13, 15, 17}
        };

        int target = 9;
        int colToSearch = 1;

        if (binarySearchColumn(matrix, target, colToSearch)) {
            System.out.println("Element " + target + " was found in column " + colToSearch);
        } else {
            System.out.println("Element " + target + " not found in column " + colToSearch);
        }
    }
}
BinarySearch.main(null);
```

    Element 9 was found in column 1


# Enhanced For-Each Loop for 2D Arrays 
Since 2D arrays are really arrays of arrays you can also use a nested enhanced for-each loop to loop through all elements in an array. We loop through each of the inner arrays and loop through all the values in each inner array. Notice the type of the outer loop array variable – it is an array that will hold each row, String[] in the example below for a 2D String array. The type of the variables in the for-each loops must match the type of the array. For-each loops are much simpler since you don’t have to use the indices and the []’s, but you can only use them if you are not going to change the values in an array of primitive types since the variable val below will not change the original array.




```Java
String[][] array;
// Nested For-each loops that traverse a 2D String array
for (String[] innerArray : array)
{
   for (String val : innerArray)
   {
       System.out.println(val);
   }
}
```


```Java
public class Average
{

    public static double getAvg(int[][] a)
    {
        double total = 0;
        for (int[] innerArray : a)
        {
            for (int val : innerArray)
            {
                total = total + val;
            }
        }
        return total / (a.length * a[0].length);
    }

    public static void main(String[] args)
    {
        int[][] theArray = { {80, 90, 70}, {20, 80, 75}};
        System.out.println(getAvg(theArray));
    }
}

Average.main(null);
```

    69.16666666666667


# 4) How to create an algorithm that involves traversing a 2D Array

During the APCSA AP exam, we will be required to write an algorithm for a 2D array that solves a problem discussed in the prompt. Collegeboard will give you a situation, and you will have to write an algorithm based on said situation. 

Here's an example of an algorithm that was needed for the real Collegeboard APCSA exam in 2022:

For this problem, the question asked for the student to write the `countIncreasingCols` method, which returns the number of columns in `grid` that are in increasing order. `grid` is a 2D array with randomly populated numbers.


```Java
public int countIncreaseCols() {
    int count = 0;
    for (int j = 0; j < grid[0].length; j++) { // Iterates through columns
        boolean isIncreasing = true; 
        if (grid[0].length > 1) { // Checks if there is more than one column to prevent out of bounds error
            for (int i = 1; i < grid.length; i++) {  // Iterates through rows
                if (grid[i][j] <= grid[i - 1][j]) { // Checks if the current element is less than or equal to the previous element
                    isIncreasing = false; // If so set isIncreasing to false and break out of loop
                    break; 
                }
            }
    
            if (isIncreasing) { // If the column is increasing increment count as if 
                count++;        // the value is not less than or equal to the previous 
                                // element then it must be increasing 
            }
        }
        
        else if (grid[0].length == 1) { // To match the criteria of a single column being increasing
            count++;
        }
        
        else { // If there are no columns then break out of loop
            break;
        }
    }
    return count; 
}
```

# Hacks:

### 1) 
Initialize a 5 x 5 2D array that is populated by random values.


```Java
import java.util.Random;

public class random2DA {
    public static void main(String[] args) {
        int[][] randomArray = new int[5][5];
        Random random = new Random();

        for (int i = 0; i < 5; i++) {
            for (int j = 0; j < 5; j++) {
                randomArray[i][j] = random.nextInt(20);
            }
        }

        // print the 2D array
        for (int i = 0; i < 5; i++) {
            for (int j = 0; j < 5; j++) {
                System.out.print(randomArray[i][j] + " ");
            }
            System.out.println();
        }
    }
}
random2DA.main(null);
```

    16 3 9 8 17 
    8 14 7 4 11 
    3 17 6 8 15 
    2 13 19 1 7 
    5 3 11 2 14 


### 2)
- a) Print the values 47, 51, and 20 by accessing them in the the given two-dimensional array.
- b) Find the values from part a) using row major and column major order and print the values in each respective order.


```Java
public class Problem2
{
    public static void main(String[] args)
    {
        int[][] arr = { {47, 3, 12}, {51, 74, 20} };

        // access values in row-major order
        System.out.println("Row-major order:");
        for (int i = 0; i < arr.length; i++) {
            for (int j = 0; j < arr[i].length; j++) {
                System.out.println(arr[i][j]);
            }
        }

        // access values in column-major order
        System.out.println("Column-major order:");
        for (int j = 0; j < arr[0].length; j++) {
            for (int i = 0; i < arr.length; i++) {
                System.out.println(arr[i][j]);
            }
        }
    }
}

Problem2.main(null);
```

    Row-major order:
    47
    3
    12
    51
    74
    20
    Column-major order:
    47
    51
    3
    74
    12
    20


### 3) 
The following 2d array `myArray` is populated with integers 1-9. Write an algorithm thath sorts the 2D array by column and returnst the values of the array in increaing order.

The expected output is:
`1 4 7`<br>
`2 5 8`<br>
`3 6 9`<br>




```Java
public class Problem3 {
    public static void main(String[] args) {
        int[][] myArray = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };

        // transpose the 2D array
        int numRows = myArray.length;
        int numCols = myArray[0].length;
        int[][] transposedArray = new int[numCols][numRows];

        for (int i = 0; i < numRows; i++) {
            for (int j = 0; j < numCols; j++) {
                transposedArray[j][i] = myArray[i][j];
            }
        }

        // sort each row in ascending order
        for (int i = 0; i < numCols; i++) {
            Arrays.sort(transposedArray[i]);
        }

        // transpose the sorted array back to its original form
        int[][] sortedArray = new int[numRows][numCols];

        for (int i = 0; i < numCols; i++) {
            for (int j = 0; j < numRows; j++) {
                sortedArray[j][i] = transposedArray[i][j];
            }
        }

        // sorted array
        for (int i = 0; i < numRows; i++) {
            for (int j = 0; j < numCols; j++) {
                System.out.print(sortedArray[i][j] + " ");
            }
            System.out.println();
        }
    }
}
Problem3.main(null);
```

    1 2 3 
    4 5 6 
    7 8 9 


### 4) 
Replace the “ADD CODE HERE” below with the code to declare and create a 3 by 3 two-dimensional int array named table. The finished code will print the values 0 to 8.


```Java
public class Test1 {
    public static void main(String[] args) {
        // declare and create a 3 by 3 two-dimensional int array named table
        int[][] table = new int[3][3];

        // print the values in table
        int count = 0;
        for (int row = 0; row < table.length; row++) {
            for (int col = 0; col < table[row].length; col++) {
                table[row][col] = count;
                count++;
                System.out.print(table[row][col] + " ");
            }
            System.out.println();
        }
    }
}
Test1.main(null);
```

    0 1 2 
    3 4 5 
    6 7 8 


### 5)
Replace the “ADD CODE HERE” below with the code to declare and initialize a two-dimensional String array called students with the names “Brice, Marvin, Anna” in the first row and “Kamal, Maria, Elissa” in the second. The finished code will print all the names in the array starting with all in the first row followed by all in the second row.


```Java
public class Test1 {
    public static void main(String[] args) {
        // declare and initialize the two-dimensional String array students
        String[][] students = {
            {"Tom", "Johnny", "Jim"},
            {"Laurie", "Pam", "Chet"}
        };

        // print the values in students in order
        for (int row = 0; row < students.length; row++) {
            for (int col = 0; col < students[row].length; col++) {
                System.out.print(students[row][col] + " ");
            }
        }
    }
}
Test1.main(null);
```

    Tom Johnny Jim Laurie Pam Chet 
