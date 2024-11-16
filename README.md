# Assignment 2: Classify

TODO: Add your own descriptions here.

**abs.s:**  
Calculate the absolute value of an integer.  

**Example:**  
- Input: `-5` -> Output: `5`  
- Input: `3` -> Output: `3` 

---

**argmax.s:**
Find maximum value Index,and returns the position of its first occurrence.

**Example:**  
- Inpur: `8,1,2,1,5` -> Output: `1`

---

**dot.s:**
Computee the dot product of two arrays with support for strides.

**Example:**  
- v0 :`[1, 2, 3, 4, 5]`
- v1 :`[5, 6, 7, 8, 9]`
- a2 (Number of elements to process) : 3
- stride 0(a3) , stride 1 (a4) =2
- [1, 3, 5] ．[5, 7, 9]＝71

---

**relu.s:**

Convert negative numbers to **0** while keeping positive numbers unchanged.

---

**matmul.s:**

Matrix Multtiplication.

-  Validate that the input matrices are compatible for multiplication
-  Outer Loop : Iterate through the rows of matrix m0 
-  Inner Loop : Iterate through the columns of matrix m1 . 
-  Use the dot.s to compute the dot product of the current row from m0 and the corresponding column from m1 .

**Example:**  
```
Assume m0 is 2*3 matrix  , m1 is 3*2 matrix
m0 = [ 1 2 3 ]  x  m1 = [ 7  8  ]  =  D =[58   64 ]
     [ 4 5 6 ]          [ 9  10 ]        [139  154]
                        [ 11 12 ]
```

---
**Matrix File Format**

- Plaintext: Begins with two integers (rows, columns), followed by matrix rows.
- Binary: Stores matrix dimensions in the first 8 bytes (two 4-byte integers), followed by matrix elements in row-major order.

**read_matrix.s :**

Read matrix data from a binary file and store it in allocated memory.

**write_matrix.s :**

Write matrix data to a binary file.

**classify.s :**

1.  Read pretrained matrixes m0 and m1,along with the input matrix
2. Compute the hidden layer . **h = matmul(m0, input)** , **h = relu(h)**
3. Compute the output layer . **o = matmul(m1, h)**
4. Find the index of the maximum value in the output matrix o 

**Example:**  
```
m0 =[0.1 0.2 0.3]   m1 = [0.7 0.8]  input= [1]
    [0.4 0.5 0.6]        [0.9 1  ]         [2]
                         [1   1  ]         [3]
1. hidden layer ,  h = matmul(m0, input)  , h = relu(h)
   h = relu( m0．input )= relu ([1.4]) = [1.4]
                              ([3.2])    [3.2]
2. output layer   o = matmul(m1, h)   
o =    [0.98 + 2.56] = [3.54]
       [1.26 + 3.2 ]   [4.46]
       [1.4 + 3.2  ]   [4.6 ]
3. Find the index of the maximum value ( 4.6,index = 2 ) 
   argmax(o) = 2
```