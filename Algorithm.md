# Algorithm

## Introduction
### Algorithm
* Describe procedure solving problem.
* Problem requirements
  * Explicit as input and output.
  * Algorithm describes procedure making output from input  

#### Desirable Algorithm
* Clearly
* Efficiently

### Evaluation criteria for algorithms
1. Correctness
2. Amout of work done
   * Executed time of Algorithm
3. Memory space used 
4. Simplicity, Clarity
   * If algorithm is simple and clear, it is easy to write program or revise
5. Optimality
   * There is no better alogrithm than this for the problem

### Describing Language for Algorithm 
* <strong>pseudo-language</strong> => Language for describing algorithm
* <strong>pseudo-code</strong> => Code written by pseudo-language
* Example
  ```bash
  i <- -1;  flag <-  true

  while (flag)
            i <- i+1
            m <- a[i]
            flag <- false
            for j <-  0 to n-1
               if m > a[j] then flag <-  true

  3. output m;

  ```

### Analysis algorithm execution time

#### Purpose
* Calculate how long program excute
* Calculate maximum input size that program finish within proper time
* Capable of comparing several algorithms solving the problem
* Select a good algorithm

#### Analysis algorithm execution time according to input
* <strong>It is very difficult to analyze average-case running time</strong>
* <strong>Usually, analyze worst-case running time</strong>

#### Big-O
* Leave the highest degree, the others are ignored
* Ignore constant multiplied at the highest degree
 * Ex)  n log n + 5n = O(n log n)
* <strong>Frequent Big-O Symbol
  * constant O(1)
  * logarithmic  O(log n)
  * linear O(n)
  * O(n log n)
  * quadratic  O(n^2), cubic O(n^3)
  * polynomial O(n^k), k >= 1
  * Exponential O(a^n), a > 1</strong>
  * O(√n) => ex) Determining prime numbers
    * If there is no divisor in numbers under √n, there is no divisor over √n

### Recursive case (Core concept of Divide and Conquer)
* Algorithm describing a big problem into small problems about input
* Must require <strong>basecase</strong> in recursion 
* Execution time => How many times basecase calculate
<br/>

* Example 1 (n!)
  * T(n) = 1 + T(n-1) => T(n) = 1 + [1 + T(n-2)] ... T(n) = n + T(1) => O(n)
* Example 2 (x^n)
  * When n is even, square after calculate x^(n/2)
  * When n is odd, x * x^(n-1)
  * T(n) = 2 + T(n/2) ... T(n) = 2k + T(n/2^k)
  * n/2^k = 1 => n = 2^k => log n = k
  * T(n) = 2 log n + T(1) = 2 log n + 1 => O(log n)
* Example 3 (Binary Search)
  * T(n) = 2k + T(n/2^k) => O(log n)
* Example 4 (Hanoi Top)
  * When n is 1, T(n) = 1, When n is more than 1, T(n) = 2T(n-1) + 1 
  * T(n) = 2T(n-1) + 1 => T(n) = 2[2T(n-2) + 1] + 1 => T(n) = 2^k T(n-k) + 2^k-1
  * n-k = 1 => k = n-1 
  * T(n) = 2^n-1 + 2^n-2 => O(2^n) 

## Sorting

#### Sorting Algorithm Classification
* <strong>Stable sorting algorithm</strong>
  * Among data to sort, relative position of same two data is maintained after sorting 
   
   ![image](https://user-images.githubusercontent.com/64727012/172866695-a8b04e78-e7b8-4314-b855-a0c33d93bc71.png)

* <strong>In-place sorting algorithm</strong>
  * Except for memory space to save inputs for sorting, additional memory space is O(1)

### Simple Sorting Algorithms

#### Selection Sort
* O(n^2)
* Code
  ```cpp
  void selectionSort(int arr[], int n){
      for(int i=n-1; i>=0 ; i--){
          int max = 0;
          for(int j=0; j<=i; j++){
              if(arr[max] < arr[j])
                  max = j;
          }
          int temp = arr[max];
          arr[max] = arr[i];
          arr[i] = temp;
      }
  }
  ```
* Picture

  ![image](https://user-images.githubusercontent.com/64727012/173173669-2bb173c6-8ec3-447b-9472-be52a788f7ff.png)


#### Bubble sort
* O(n^2)
* Code
  ```cpp
  void bubbleSort(int arr[], int n){
      for(int i=n-1; i>0; i--){
          for(int j=0; j<i; j++){
              if(arr[j] > arr[j+1]){
                  int temp = arr[j];
                  arr[j] = arr[j+1];
                  arr[j+1] = temp;
              }
          }
      }
  }

  void improvedBubbleSort(int arr[], int n){
      int sorted = 1;
      for(int i=n-1; i>0; i--){
          for(int j=0; j<i; j++){
              if(arr[j] > arr[j+1]){
                  int temp = arr[j];
                  arr[j] = arr[j+1];
                  arr[j+1] = temp;
                  sorted = 0;
              }
          }
          if(sorted == 1)
              break;
      }
  }
  ```
* Picture
  ![image](https://user-images.githubusercontent.com/64727012/173173861-5c926e3a-4dfa-4dba-915d-4296e758c71b.png)


#### Insertion Sort
* O(n^2)
* Code
  ```cpp
  void insertSort(int arr[], int n){
      for(int i=1; i<n; i++){
          int temp = arr[i];
          int index = 0;
          for(int j=i-1; j>=0; j--){
              if(arr[j] > temp){
                  arr[j+1] = arr[j];
                 }
              else{
                  index = j+1;
                  break;
              }
          }
          arr[index] = temp;
      }
  }

  ```
* Picture
  ![image](https://user-images.githubusercontent.com/64727012/173173920-3312aa21-0158-4611-8910-67868d3555ce.png)

#### Simple Sorting Algorithms Summary

![image](https://user-images.githubusercontent.com/64727012/173173965-461429e3-2464-4aa6-8799-809275ff60ba.png)

### Sorting Algorithm by Divide and Conquer
1. Divide a problem of big input into problems of small input
2. Solve reculsively small problems of step 1 
3. By using solutions of step 2, solve the original problem

#### Algorithm finding maximum value in array
* Description
  * Save max value of left part of half in lmax
  * Save max value of right part of half in rmax
  * By comparing two value, return a bigger one
* Code
  ```cpp
  int maxReturn(int a[], int first, int last){
      if(first<last){
          int mid = (first+last)/2;
          int lmax = maxReturn(a, first, mid);
          int rmax = maxReturn(a, mid+1, last);
          if(lmax > rmax)
              return lmax;
          else
              return rmax;        
      }
      else
          return a[first];
  }

  ```
* O(n)
  * T(1) = c1
  * When n is more than 1, T(n) = 2T(n/2) + C2
  * T(n) = 2T(n/2) + C2 => T(n) = 2(2(T/2^2) + C2) + C2
  * T(n) = (2^k) * T(n/2^k) + C2*(2^k-1) => K= logn
  * T(n) = (C2+C1)n – C2 => O(n)

#### Merge Sort

#### Quick Sort

### Heap Sort

### Radix Sort


## Dynamic Programming

## Greedy Method

## Graph
