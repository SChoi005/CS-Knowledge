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
* Code
  ```cpp
  int temp[10001];
  void merge(int a[], int first, int mid, int last)
  {
      int i = first;
      int j = mid + 1;
      int k = first;

      while (i <= mid && j <= last){
          if (a[i] <= a[j]){
              temp[k] = a[i];
              i++;
          }
          else{
              temp[k] = a[j];
              j++;
          }
          k++;
      }

      if (i > mid){
          for (int t = j; t <= last; t++){
              temp[k] = a[t];
              k++;
          }
      }
      else{
          for (int t = i; t <= mid; t++){
              temp[k] = a[t];
              k++;
          }
      }

      for (int t = first; t <= last; t++)
          a[t] = temp[t];
  }

  void mergeSort(int a[], int first, int last){
      if(first<last){
          int mid = (first+last)/2;
          mergeSort(a, first, mid);
          mergeSort(a, mid+1, last);
          merge(a, first, mid, last);
      }
  }

  ```


#### Quick Sort
* Code
  * Divide
    ```cpp
    void quickSort(int num[], int left, int right){
        if(left<=right){
            int pivot=partition(num,left,right);
            quickSort(num,left,pivot-1);
            quickSort(num,pivot+1,right);
        }
    }

    ```
  * Partition
    ```cpp
    int partition(int num[], int left, int right){
        //피봇을 랜덤하게 선택
        int pivotIndex = rand()%(right+1-left)+left;
        int pivot=num[pivotIndex];

        //피봇을 맨 왼쪽과 교환한다.
        int tmp = num[pivotIndex];
        num[pivotIndex] = num[left];
        num[left] = tmp;

        int low=left+1;
        int high=right;

        while(low<=high){
            //pivot보다 큰 low인덱스를 찾음
            while(low<=right && pivot>=num[low]){
                low++;
            }
            //pivot보다 작은 high인덱스를 찾음
            while(high>=left+1 && pivot<=num[high]){
                high--;
            }
            //low와 high를 바꿈
            if(low<=high){
                int temp=num[low];
                num[low]=num[high];
                num[high]=temp;
            }
        }
        //high가 멈춘곳과 pivot값을 교환함
        int temp=num[left];
        num[left]=num[high];
        num[high]=temp;

        //high값을 기준으로 분리해야하므로 high리턴
        return high;
    }

    ```
  * Kth Smallest Element 
    ```cpp
    int kthSmallest(int a[], int first, int last, int k){
        if(k>0 && k<=last-first+1){
            int pos = partition(a, first, last);
            if(pos-first == k-1)
                return a[pos];
            else if(pos-first > k-1)
                return kthSmallest(a, first, pos-1, k);
            else
                return kthSmallest(a, pos+1, last, k-pos+first-1);
        }
        return INT32_MAX;
    }

    
    ```

### Heap Sort
* Code
  * rebuildHeap
    ```cpp
    void rebuildHeap(int a[], int root, int n){

        int current = root;

        while(2 * current + 1 < n){
            int leftChild = 2 * current + 1;
            int rightChild = leftChild + 1;
            int largerChild;

            if(rightChild < n){
                if(a[rightChild] > a[leftChild])
                    largerChild = rightChild;
                else
                    largerChild = leftChild;
            }
            else
                largerChild = leftChild;

            if(a[largerChild] > a[current]){
                int temp = a[largerChild];
                a[largerChild] = a[current];
                a[current] = temp;
            }
            else
                break;
            current = largerChild;
        }
    }

    for(int root = n/2 - 1; root >= 0; root--)
        rebuildHeap(arr, root, n);
    ```
  * Heap Sort
    ```cpp
    void heapSort(int a[], int n){
        int heap_size = n;
        for(int last = n-1; last > 0; last--){
            int temp = a[0];// 최댓값
            a[0] = a[last];
            a[last] = temp;
            heap_size--;
            rebuildHeap(a, 0, heap_size);
        }
    }

    ```
  * Priority Queue
    * insertHeap
      ```cpp
      void insertHeap(int a[], int &n, int key){
          a[n] = key;
          n++;
          int i = n-1;
          int parent = (i-1)/2;

          while(i>0){
              if(a[parent] < a[i]){
                  int temp = a[parent];
                  a[parent] = a[i];
                  a[i] = temp;
                  i = parent;
                  parent = (i-1)/2;
              }
              else
                  break;            
          }
      }
      ```
    * deleteHeap  
      ```cpp
      void deleteHeap(int a[], int &n){
          int temp = a[n-1];
          a[n-1] = a[0];
          a[0] = temp;
          n--;
          rebuildHeap(a, 0, n);
      }

      ```


### Radix Sort
* Code
  ```cpp
  void radixSort(int a[], int n){
      queue<int>Q[10];
      int max = a[0], radix = 1;

      for(int i=0; i<n; i++){
          if(max < a[i])
              max = a[i];
      }
      while(1){//최댓값찾기
          if(radix >= max)
              break;
          radix *= 10;
      }
      for(int i=1; i<=radix; i*=10){
          //분할
          for(int j=0; j<n; j++){
              int k;
              if(a[j]<i)
                  k=0;
              else
                  k=(a[j]/i)%10;
                  Q[k].push(a[j]);            
          }
          //모으기
          int idx = 0;
          for(int j=0; j<10; j++){
              while(Q[j].empty()==0){
                  a[idx] = Q[j].front();
                  Q[j].pop();
                  idx++;
              }
          }
      }  
  }

  ```



## Dynamic Programming

## Greedy Method

## Graph
