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

## Dynamic Programming

## Greedy Method

## Graph
