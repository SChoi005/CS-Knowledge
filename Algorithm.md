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
* <strong>O(n^2)</strong>
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
* <strong>O(n^2)</strong>
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
* <strong>O(n^2)</strong>
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
* <strong>O(n)</strong>
  * T(1) = c1
  * When n is more than 1, T(n) = 2T(n/2) + C2
  * T(n) = 2T(n/2) + C2 => T(n) = 2(2(T/2^2) + C2) + C2
  * T(n) = (2^k) * T(n/2^k) + C2*(2^k-1) => K= logn
  * T(n) = (C2+C1)n – C2 => O(n)

#### Merge Sort
* Description
  * Divide list of n size into two part of n/2 size
  * Sort recursively two parts of n/2 size
  * Merge two sorted parts into one by using merge function
  
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
* <strong>O(n log n)</strong>
  * T(1) = C2
  * When n is more than 1, T(n) = 2(n/2) + C2 * n
  * T(n) = 2(2T(n/2^2) + 1/2 * c2 * n ) + c2 * n
  * T(n) = (2^k)T(n/2^k) + c2 * n * k
  * K = log n
  * T(n) = c2 * nlogn + c2 * n => <strong>O(n log n), Space Complexity 🡪 O(n)</strong>
* Picture
  ![image](https://user-images.githubusercontent.com/64727012/173189866-f22081b0-69ed-44d4-a070-4d7a617fb470.png)



#### Quick Sort
* Description
  * In array a, select a pivot. The pivot becomes criteria for division
  * The values less than the pivot move into its right part 
  * Sort recursively in the same way as above
  * Kth smallest
    * Sort array a, then return a[k-1] value
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
* <strong>Ideally, when split in half, Θ(n log n)</strong>
  * T(1) = c1
  * When n is more than 1, 2T(n/2) + n
  * T(n) = 2(2T(n/2) + n/2) + n
  * T(n) = (2^k)T(n/2^k) + n * k
  * K = log n
  * T(n) = n log n + c1 * n => Θ(n log n)
* <strong>When the pivot is continuously selected maximum or minimum value, O(n^2)</strong>
  * T(1) = c1
  * When n is more than 1, T(n-1) + n + c1
  * T(n) = T(n-1) + n + c1
  * T(n) = n * k + k * c1 => n^2 + n * c1 🡪 O(n^2)
* <strong>Kth smallest : O(n^2), Θ(nlog n)</strong>
* Space analysis => need stack memory of O(n)
  * We can reduce stack memory as O(log n) by sorting the small part of two divided parts 
* Picture
  ![image](https://user-images.githubusercontent.com/64727012/173190292-e538e082-4788-4363-a3a5-e55603afe683.png)



### Heap Sort
* Description
  * Make a array max-heap by using RebuildHeap function
  * 0th index value is max value in max heap
  * This value swaps with the lastest element in the array, and reduce heap size
  * Repeat making max-heap by calling rebuildHeap
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
* <strong>O(n log n)</strong>
  * rebuildHeap => O(log n) 
  * Since rebuildHeap is called n times, it could be considered time complexity as O(n log n), but this is not a tight analysis.
* Picture

  ![image](https://user-images.githubusercontent.com/64727012/173191619-fc22d773-0020-470f-9a86-179af3295890.png)

#### Algorithm compare
![image](https://user-images.githubusercontent.com/64727012/173190986-dff1013f-471a-42c3-bf85-d23e19610379.png)


### Radix Sort
* Description
  * This is not method by compare
  * Distribute elements as criteria for the rightmost digit, and then gather them
  * Then repeat by the second, third, ... rightmost digit 
  * The elements under 10 are sorted in Bin[0]
  * When distribute and gather, use Queue
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
* <strong>O(d * (n + r))</strong>
  * d => Maximum number of digits of sort data
  * r => base
* Picture

  ![image](https://user-images.githubusercontent.com/64727012/173191491-ba50b1bd-dd23-4d5c-8e30-86666ce27a1a.png)

### Counting Sort
* Description
  * This is not method by compare
  * This must know maximum value
  * Count the number of each element
  * C is the counting array. C[i] saves the number of i
  * C[i] is stored back as the sum of numbers less than or equal to i 
  * Also stores i in B[C[i]-1]
  * The disadvantage of this is that it requires a lot of memory compared to the number of data
* Code
  ```cpp
  int c[10000];
  int* countingSort(int a[], int n, int k){
      int* b = new int[n];
      for(int i=0; i<=k; i++)
          c[i] = 0;
      for(int i=0; i<n; i++)
          c[a[i]] += 1;
      for(int i=0; i<=k; i++)
          c[i] += c[i-1];
      for(int i = n-1; i>=0; i--){
          b[c[a[i]]-1] = a[i];
          c[a[i]] -= 1;
      } 
      return b;
  }

  ```
* <strong>O(n)</strong>
* Picture

  ![image](https://user-images.githubusercontent.com/64727012/173192019-55670895-bea9-4b07-b5af-12ed8ded8763.png)


## Dynamic Programming
* <strong>Definition</strong>
  * <strong>Divide and conquer</strong> is method that divide a problem into partial problems, solve recursively them, and solve the original problem from them. (Partial problems are independent)
  * <strong>Dynamic programming</strong> solve the problem by using solution of partial problems. (Unlike divide and conquer, The needed partial problems to solve the original problem are not independent )
* <strong>Two accessable way</strong>
  * <strong>Memoization</strong>
    * Be able to define through recursion or saving results
    * After computing solution of small problems, save in a table
    * Successive calls execute the table
    * Table is a global variable(lookup)
  * <strong>Bottom-Up</strong>
    * Solve in turn by starting from small partial problems to big partial problems  
    * After getting solutions of partial problems, save them in a table
    * When solve partial problems, not calculate needed solutions of smaller partial problems, but refer the table
* <strong>Dynamic programming</strong> is used to solve problems applied <strong>Optimization Principle</strong>
  * Optimization solutions of problems include all optimization solutions of partial problems
  * If suppose a series of choices is D1,D2,D3...Dn, 
  * D2,D3,...Dn become optimization solutions after first selection is D1 
  * <strong>Optimization Principle</strong> Ex) the shortest path
  * <strong>Optimization Principle not applied</strong> Ex) the longest simple path
* <strong>Step</strong>
  * Figure out the structure of optimization solution
  * Figure out recursive definition about optimization solution
  * Solve objective function by using bottom-up or memoization and save the value in a table
  * Solve optimization solution by using information of step 3

### Fibonacci
* Description
  * Bottom-up
    * By saving value continuously through loop, solve next values
    * Prior values don't have to solve again because they have been saved
  * Memoization
    * After initialize the global variable(lookup), solve the function recursively
    * Then, if this is first value, save in lookup
    * If not, bring the value from lookup
  * Effective memory use
    * Not save values in array
    * Solve values by saving pre-value and pre-pre-value 
* Code
  * Bottom-up
    ```cpp
    int fib1(int n){
        int *f = new int[n];
        f[0] = 0; 
        f[1] = 1;
        for(int i=2; i<=n; i++){
            f[i] = f[i-1] + f[i-2];
        }    
        return f[n];
    }

    ```
  * Memoization
    ```cpp
    int lookup[100];
 
    int fib2(int n){
        if(lookup[n]==-1){
            if(n<=1)
                lookup[n] = n;
            else
                lookup[n] = fib2(n-1) + fib2(n-2);        
        }
        return lookup[n];
    }

    ```
  * Effective memory use
    ```cpp
    int fib3(int n){
        int pre_pre, pre, current;

        if(n<= 1)
            return 1;
        pre_pre = 0;
        pre = 1;
        for(int i=2; i<=n; i++){
            current = pre_pre + pre;
            pre_pre=pre;
            pre=current;
        }
        return current;
    }

    ```
* <strong>O(n)</strong>
### Binomial coefficient
### The way to represent sum of natural number n
### The way to give change
### Weighted Interval Scheduling
### Maximum sum of successive numbers
### Solve the longest increasing subsquence
### Find path in Grid
### LCS(Longest Common Subsequence)
### Assembly line scheduling


## Greedy Method

## Graph
