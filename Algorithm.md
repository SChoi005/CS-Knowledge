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

## Sorting

#### Sorting Algorithm Classification
* <strong>Stable sorting algorithm</strong>
  * Among data to sort, relative position of same two data is maintained after sorting 
   
   ![image](https://user-images.githubusercontent.com/64727012/172866695-a8b04e78-e7b8-4314-b855-a0c33d93bc71.png)

* <strong>In-place sorting algorithm</strong>
  * Except for memory space to save inputs for sorting, additional memory space is O(1)

### Simple Sorting Algorithms

#### Selection Sort
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
  

#### Bubble sort
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


#### Insertion Sort
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


### Sorting Algorithm by Divide and Conquer


## Dynamic Programming

## Greedy Method

## Graph
