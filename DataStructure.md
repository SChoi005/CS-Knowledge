# Data Structure 

## Recursion

## Linear Data Structure
### List
#### Linear list (Array)
> Coincide logical, physical order. (Data are sequentially saved without empty space when data insert, delete.)
* <strong>Search => O(n)</strong>
* <strong>Traversal => O(n)</strong>
* <strong>Insert => (last : O(1), middle : O(n))</strong>
* <strong>Delete => O(n)</strong>
<br/>

* <strong>ArrayList.h</strong>

  ```c

  #ifndef __ARRAY_LIST_H__
  #define __ARRAY_LIST_H__

  #define TRUE 1
  #define FALSE 0
  #define LIST_LEN 100

  //ArrayList의 정의
  typedef int dataType;

  typedef struct __ArrayList
  {
    dataType arr[LIST_LEN];	 
    int numberOfData;	     
  } ArrayList; 


  //ArrayList calculation
  typedef ArrayList List; 
  void listInit(List* plist); //init
  void appendList(List* plist, dataType data); //insert
  void removeList(List* plist, dataType data); //delete
  dataType returnList(List* plist, int index); // return element
  void sortList(List* plist, int start, int end); // sort
  int searchList(List* plist, dataType data);  // search


  #endif

  ```

* <strong>main.c</strong>

  ```c
  #include<stdio.h>
  #include "ArrayList.h"

  int main()
  {
    List list; //create
    listInit(&list);//init
    appendList(&list, 20); //insert elements
    appendList(&list, 40);
    appendList(&list, 30);
    appendList(&list, 20);
    appendList(&list, 23);
    appendList(&list, 12);
    appendList(&list, 13);
    appendList(&list, 10);
    printf("현재의 데이터 수는 %d\n", list.numberOfData);
    for (int i = 0; i < list.numberOfData; i++)
    {
      printf("%d ", returnList(&list, i));
    }
    printf("\n");

    removeList(&list, 30); // delete a element

    printf("현재의 데이터 수는 %d\n", list.numberOfData);
    for (int i = 0; i < list.numberOfData; i++)
    {
      printf("%d ", returnList(&list, i));
    }
  }
  ```



#### Linked list (Pointer)
> Not Coincide logical, physical order. (Even if logical order is changed by insert and delete, change only link informtion and not change physcial order.)
* <strong>Search => O(n)</strong>
* <strong>Traversal => O(n)</strong>
* <strong>Insert => O(n)</strong>
* <strong>Delete => O(n)</strong>

### stack

### Queue

## Non-Linear Data Structure

### Tree

### Priority queue and heap

### graph

## Sort

## Search

## Table and Hash
