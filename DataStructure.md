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

<strong>1. Singly Linked List</strong>
  * A node has structure linked next node by a link field
    ![image](https://user-images.githubusercontent.com/64727012/172037978-e2ee555b-f297-44e8-9d4f-cb7d8dafe62d.png)

  * Example
  ```c
  #include <stdio.h>
  #include <stdlib.h>
  #include <string.h>

  // 단순 연결 리스트의 노드 구조를 구조체로 정의
  typedef struct ListNodeType {
    char data[2];
    struct ListNodeType* link;
  } ListNode;

  // 리스트의 시작을 나타내는 header 노드를 구조체로 정의
  typedef struct LinkedListType{
    ListNode* headerNode;
  } LinkedList;

  // 공백 연결 리스트를 생성하는 연산
  LinkedList* createLinkedList(void) {
    LinkedList* pList;
    pList = (LinkedList*)malloc(sizeof(LinkedList));
    pList->headerNode = NULL;		// 공백 리스트이므로 NULL로 설정
    return pList;
  }

  // 연결 리스트의 전체 메모리를 해제하는 연산
  void freeLinkedList(LinkedList* pList) {
    ListNode* pNode;
    while (pList->headerNode != NULL) {
      pNode = pList->headerNode;
      pList->headerNode = pList->headerNode->link;
      free(pNode);
      pNode = NULL;
    }
  }

  // 연결 리스트를 순서대로 출력하는 연산
  void displayList(LinkedList* pList) {
    ListNode* pNode;
    printf("pList = (");
    pNode = pList->headerNode;
    while (pNode != NULL) {
      printf("%s", pNode->data);
      pNode = pNode->link;
      if (pNode != NULL) printf(", ");
    }
    printf(") \n");
  }

  // 맨 앞 노드로 삽입하는 연산
  void insertFrontNode(LinkedList* pList, char* a) {
    ListNode* newNode;
    newNode = (ListNode*)malloc(sizeof(ListNode));	// 삽입할 새 노드 할당
    strcpy(newNode->data, a);						// 새 노드의 데이터 필드에 a 저장  
    newNode->link = pList->headerNode;
    pList->headerNode = newNode;
  }

  // 노드를 pre 뒤에 삽입하는 연산
  void insertMiddleNode(LinkedList* pList, ListNode* pre, char* a) {
    ListNode* newNode;
    newNode = (ListNode*)malloc(sizeof(ListNode));
    strcpy(newNode->data, a);
    if (pList == NULL) {				// 공백 리스트인 경우
      newNode->link = NULL;		// 새 노드를 첫 번째이자 마지막 노드로 연결
      pList->headerNode = newNode;
    }
    else if (pre == NULL) {			// 삽입 위치를 지정하는 포인터 pre가 NULL인 경우
      pList->headerNode = newNode;			// 새 노드를 첫 번째 노드로 삽입
    }
    else {
      newNode->link = pre->link;	// 포인터 pre의 노드 뒤에 새 노드 연결
      pre->link = newNode;
    }
  }

  // 마지막 노드로 삽입하는 연산 
  void insertEndNode(LinkedList* pList, char* a) {
    ListNode* newNode;
    ListNode* temp;
    newNode = (ListNode*)malloc(sizeof(ListNode));
    strcpy(newNode->data, a);
    newNode->link = NULL;
    if (pList->headerNode == NULL) {			// 현재 리스트가 공백인 경우					
      pList->headerNode = newNode;			// 새 노드를 리스트의 시작 노드로 연결
      return;
    }
    // 현재 리스트가 공백이 아닌 경우 	
    temp = pList->headerNode;
    while (temp->link != NULL) temp = temp->link;	// 현재 리스트의 마지막 노드를 찾음
    temp->link = newNode;							// 새 노드를 마지막 노드(temp)의 다음 노드로 연결 
  }

  // 리스트에서 노드 pNode를 삭제하는 연산
  void removeNode(LinkedList* pList, ListNode* pNode) {
    ListNode* pre;					// 삭제할 노드의 선행자 노드를 나타낼 포인터	
    if (pList->headerNode == NULL) return;		// 공백 리스트라면 삭제 연산 중단	
    if (pList->headerNode->link == NULL) {    // 리스트에 노드가 한 개만 있는 경우
      free(pList->headerNode);				// 첫 번째 노드를 메모리에서 해제하고
      pList->headerNode = NULL;				// 리스트 시작 포인터를 NULL로 설정
      return;
    }
    else if (pNode == NULL) return;		// 삭제할 노드가 없다면 삭제 연산 중단	
    else {							// 삭제할 노드 pList의 선행자 노드를 포인터 pre를 이용해 찾음
      pre = pList->headerNode;
      while (pre->link != pNode) {
        pre = pre->link;
      }
      pre->link = pNode->link;			// 삭제할 노드 pNode의 선행자 노드와 다음 노드를 연결
      free(pNode);					// 삭제 노드의 메모리 해제	 		
    }
  }

  // 리스트에서 a 값을 가지고 있는 노드를 탐색하는 연산
  ListNode* searchNode(LinkedList* pList, char* a) {
    ListNode *temp;
    temp = pList->headerNode;
    while (temp != NULL) {
      if (strcmp(temp->data, a) == 0) return temp;
      else temp = temp->link;
    }
    return temp;
  }


  int main() {
    LinkedList* pList;
    ListNode* pNode;
    pList = createLinkedList();		// 공백 리스트 생성

    printf("(1) 리스트에 [료], [조] 노드 삽입하기! \n");
    insertFrontNode(pList, "료"); 
    insertEndNode(pList, "조"); 
    displayList(pList); 
    getchar();

    printf("(2) 리스트에서 [료] 노드 탐색하기! \n");
    pNode = searchNode(pList, "료");
    if (pNode == NULL) printf("찾는 데이터가 없습니다.\n");
    else printf("pNode = [%s] 찾았습니다.\n", pNode->data);
    getchar();

    printf("(3) 리스트의 [료] 노드 뒤에 [의]노드 삽입하기! \n");
    insertMiddleNode(pList, pNode,  "의"); 
    displayList(pList); 
    getchar();

    printf("(4) 리스트에 [자] 노드를 노드의 첫번째에 삽입하기! \n");
    insertFrontNode(pList, "자");
    displayList(pList); 
    getchar();

    printf("(5) 리스트에서 [의] 노드 탐색하기! \n");
    pNode = searchNode(pList, "의");
    if (pNode == NULL) printf("찾는 데이터가 없습니다.\n");
    else printf("pNode = [%s] 찾았습니다.\n", pNode->data);
    getchar();

    printf("(6) 리스트의 [의] 노드 뒤에 [구] 노드 삽입하기! \n");
    insertMiddleNode(pList, pNode, "구");
    displayList(pList); 
    getchar();

    printf("(7) 리스트에서 [의] 노드 삭제하기! \n");
    pNode = searchNode(pList, "의");		// 삭제할 노드 위치 pNode를 찾음
    removeNode(pList, pNode);			// 포인터 pNode 노드 삭제
    displayList(pList); 
    getchar();

    printf("(8) 리스트에서 [의] 노드 탐색하기! \n");
    pNode = searchNode(pList, "의");
    if (pNode == NULL) printf("찾는 데이터가 없습니다.\n");
    else printf("pNode = [%s] 찾았습니다.\n", pNode->data);
    getchar();

    printf("(9) 리스트의 메모리 해제! \n");
    freeLinkedList(pList);		// 리스트의 메모리 해제
    displayList(pList); 
    getchar();

    return 0;
  }

  ```

<strong>3. Circular Linked List</strong>
  * same with Singly Linked List except for part linking a last node to a first node 
    ![image](https://user-images.githubusercontent.com/64727012/172038139-f53e4372-3ce1-4a9e-995c-dd146150867b.png)
  * Example
    ```c
    
    #include <stdio.h>
    //원형연결리스트 정의
    typedef char dataType;
    //리스트 노드구조
    typedef struct CircularLinkedNodeType {
      dataType data;
      struct CircularLinkedNodeType* tail;
    } CLinkedNode;

    //원형연결리스트 생성(front) head->tail이 첫 인덱스
    typedef struct CircularLinkedList {
      CLinkedNode* head;
      int nodeCount;
    }CLinkedList;

    //원형연결리스트 생성
    CLinkedList* createCLinkedList()
    {
      CLinkedList* pList = (CLinkedList*)malloc(sizeof(CLinkedList));
      pList->head = (CLinkedNode*)malloc(sizeof(CLinkedNode));;
      pList->nodeCount = 0;
      return pList;
    }
    //원형연결리스트 노드삽입(변수 세개)(공백리스트, 번호, 데이터)
    void insertCLinkedList(CLinkedList* plist, unsigned int index, dataType data)
    {
      CLinkedNode* preNode = plist->head->tail;
      CLinkedNode* newNode = (CLinkedNode*)malloc(sizeof(CLinkedNode));

      newNode->data = data;//데이터 삽입
      if (plist->nodeCount == 0) {
        newNode->tail = newNode;
        plist->head->tail = newNode;
        plist->nodeCount++;
        return 0;
      }

      if (index == 0) {
        for (int i = 0; i < plist->nodeCount - 1; i++) {
          preNode = preNode->tail;
        }
        preNode->tail = newNode;
        newNode->tail = plist->head->tail;
        plist->head->tail = newNode;
      }
      else {
        for (int i = 0; i < index - 1; i++) {
          preNode = preNode->tail;
        }
        newNode->tail = preNode->tail;
        preNode->tail = newNode;
      }
      plist->nodeCount++;
    }
    //원형연결리스트 노드삭제
    void removeCLinkedList(CLinkedList* plist, unsigned int index) {

      CLinkedNode* pre = plist->head->tail;
      CLinkedNode* temp;
      for (int i = 0; i < index - 1; i++) {
        pre = pre->tail;
      }
      temp = pre->tail;
      pre->tail = pre->tail->tail;
      free(temp);

      plist->nodeCount--;
    }
    //원형연결리스트 노드탐색(원소값찾기)
    dataType returnNodeData(CLinkedList* plist, int index) {

      CLinkedNode* temp = plist->head->tail;

      for (int i = 0; i < index; i++) {
        temp = temp->tail;
      }
      return temp->data;
    }
    //원형연결리스트 노드개수반환
    int returnNodeCount(CLinkedList* plist) {
      return plist->nodeCount;
    }
    //원형연결리스트 전체원소반환
    void display(CLinkedList* plist) {
      int i;
      CLinkedNode* node = (CLinkedNode*)malloc(sizeof(CLinkedNode));
      node = plist->head->tail;
      printf("( ");
      for (i = 0; i < plist->nodeCount; i++) {
        printf("%c ", node->data);
        node = node->tail;
      }
      printf(")\n");
    }
    int main()
    {
      //원형 리스트 생성
      CLinkedList *list = createCLinkedList();
      //원형 리스트 삽입
      insertCLinkedList(list, 0, 'S');
      insertCLinkedList(list, 0, 'F');
      insertCLinkedList(list, 0, 'U');
      insertCLinkedList(list, 0, 'H');
      insertCLinkedList(list, 4, '/');
      insertCLinkedList(list, 5, 'S');
      insertCLinkedList(list, 5, 'E');
      insertCLinkedList(list, 5, 'C');

      //리스트 노드 갯수 반환
      printf("현재 리스트의 갯수는 %d입니다.\n", returnNodeCount(list));
      //전체 리스트 노드 원소 반환
      display(list);
      //노드탐색 인덱스원소반환
      printf("%d번 인덱스의 문자는 %c입니다.\n", 6, returnNodeData(list, 6));
      //노드삭제 인덱스노드삭제
      removeCLinkedList(list, 3);
      display(list);
      printf("현재 리스트의 갯수는 %d입니다.\n", returnNodeCount(list));
      removeCLinkedList(list, 4);
      display(list);
      printf("현재 리스트의 갯수는 %d입니다.\n", returnNodeCount(list));
    }

    
    ```


<strong>4. Doubly Linked List</strong>
  * Improved Linked List adding a link for pointing a prior node
    * Doubly Linked List
    
      ![image](https://user-images.githubusercontent.com/64727012/172038334-f4dc4d8e-d485-49fc-a0b6-ab6aadb796fb.png)
    * Circular Doubly Linked List
    
      ![image](https://user-images.githubusercontent.com/64727012/172038347-b0bb2773-9e65-4dd7-997d-3dc77b414610.png)

  * Example
    ```c
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>

    // 이중 연결 리스트의 노드 구조를 구조체로 정의
    typedef struct ListNodeType {
      struct ListNodeType* llink;   // 왼쪽(선행) 노드에 대한 링크
      char data[2];
      struct ListNodeType* rlink;   // 오른쪽(다음) 노드에 대한 링크
    } DListNode;

    // 리스트 시작을 나타내는 HeaderNode 노드를 구조체로 정의
    typedef struct {
      DListNode* headerNode;
    } DLinkedList;


    // 공백 이중 연결 리스트를 생성하는 연산
    DLinkedList* createDLinkedList(void) {
      DLinkedList* pDList;
      pDList = (DLinkedList*)malloc(sizeof(DLinkedList));	// 헤드 노드 할당
      pDList->headerNode = NULL;					// 공백 리스트이므로 NULL로 설정
      return pDList;
    }

    // 연결 리스트의 전체 메모리를 해제하는 연산
    void freeLinkedList(DLinkedList* pDList) {
      DListNode* pNode;
      while (pDList->headerNode != NULL) {
        pNode = pDList->headerNode;
        pDList->headerNode = pDList->headerNode->rlink;
        free(pNode);
        pNode = NULL;
      }
    }

    // 이중 연결 리스트를 순서대로 출력하는 연산
    void displayList(DLinkedList* pDList) {
      DListNode* pNode;
      printf(" pDList = (");
      pNode = pDList->headerNode;
      while (pNode != NULL) {
        printf("%s", pNode->data);
        pNode = pNode->rlink;
        if (pNode != NULL) printf(", ");
      }
      printf(") \n");
    }
    // 맨 앞 노드로 삽입하는 연산
    void insertFrontNode(DLinkedList* pDList, char* a) {
      DListNode* newNode;
      newNode = (DListNode*)malloc(sizeof(DListNode));	// 삽입할 새 노드 할당
      strcpy(newNode->data, a);						// 새 노드의 데이터 필드에 a 저장  

      if (pDList== NULL)         // 공백 리스트인 경우
        newNode->rlink = NULL;
      else
          newNode->rlink = pDList->headerNode;
      newNode->llink = NULL;
      pDList->headerNode = newNode;
    }

    // pre 뒤에 노드를 삽입하는 연산
    void insertMiddleNode(DLinkedList* pDList, DListNode* pre, char* a) {
      DListNode* newNode;
      newNode = (DListNode*)malloc(sizeof(DListNode));
      strcpy(newNode->data, a);

      if ((pDList== NULL)|| (pre == NULL)) {         // 공백 리스트 or pre가 NULL인 경우
        newNode->rlink = NULL;
        newNode->llink = NULL;
        pDList->headerNode = newNode;   // 새 노드를 첫 번째이자 마지막 노드로 연결
      }
      else {
        newNode->rlink = pre->rlink;
        pre->rlink = newNode;
        newNode->llink = pre;
        if (newNode->rlink != NULL)	// 삽입 자리에 다음 노드가 있는 경우
          newNode->rlink->llink = newNode;
      }
    }
    // 마지막 노드로 삽입하는 연산 
    void insertEndNode(DLinkedList* pDList, char* a) {
      DListNode* newNode;
      DListNode* temp;
      newNode = (DListNode*)malloc(sizeof(DListNode));
      strcpy(newNode->data, a);

      if (pDList->headerNode == NULL) {			// 현재 리스트가 공백인 경우			
        newNode->rlink = NULL;
        newNode->llink = NULL;	
        pDList->headerNode = newNode;			// 새 노드를 리스트의 시작 노드로 연결
        return;
      }
      // 현재 리스트가 공백이 아닌 경우 	
      temp = pDList->headerNode;
      while (temp->rlink != NULL) temp = temp->rlink;	// 현재 리스트의 마지막 노드를 찾음
      newNode->llink = temp;
      temp->rlink = newNode;							// 새 노드를 마지막 노드(temp)의 다음 노드로 연결 
      newNode->rlink = NULL;
    }

    // 이중 연결 리스트에서 del 노드를 삭제하는 연산
    void removeNode(DLinkedList* pDList, DListNode* del) {
      if (pDList->headerNode == NULL) return;	// 공백 리스트인 경우, 삭제 연산 중단		
      else if (del == NULL) return;	// 삭제할 노드가 없는 경우, 삭제 연산 중단	
      else {
        del->llink->rlink = del->rlink;
        del->rlink->llink = del->llink;
        free(del);					// 삭제 노드의 메모리 해제	 		
      }
    }

    // 리스트에서 a 노드를 탐색하는 연산
    DListNode* searchNode(DLinkedList* pDList, char* a) {
      DListNode *temp;
      temp = pDList->headerNode;
      while (temp != NULL) {
        if (strcmp(temp->data, a) == 0) return temp;
        else temp = temp->rlink;
      }
      return temp;
    }

    int main() {
      DLinkedList* pDList;
      DListNode *pNode;
      pDList = createDLinkedList();  // 공백 리스트 생성

      printf("(1) 이중 연결 리스트 생성하기! \n");
      displayList(pDList); 
      getchar();

      printf("(2) 이중 연결 리스트의 첫번째에 [료] 노드 삽입하기! \n");
      insertFrontNode(pDList, "료");
      displayList(pDList); 
      getchar();

      printf("(3) 이중 연결 리스트의 [료] 노드 뒤에 [의] 노드 삽입하기! \n");
      pNode = searchNode(pDList, "료"); 
      insertMiddleNode(pDList, pNode, "의");
      displayList(pDList); 
      getchar();

      printf("(4) 이중 연결 리스트의 마지막에 [조] 노드 삽입하기! \n");
      insertEndNode(pDList, "조");
      displayList(pDList); 
      getchar();

      printf("(5) 이중 연결 리스트의 첫번째에 [자] 노드 삽입하기! \n");
      insertFrontNode(pDList, "자");
      displayList(pDList); 
      getchar();

      printf("(6) 리스트에서 [의] 노드 탐색하기! \n");
      pNode = searchNode(pDList, "의");
      if (pNode == NULL) printf("찾는 데이터가 없습니다.\n");
      else printf("pNode = [%s] 찾았습니다.\n", pNode->data);
      getchar();

      printf("(7) 이중 연결 리스트의 [의] 노드 뒤에 [구] 노드 삽입하기! \n");
      insertMiddleNode(pDList, pNode, "구");
      displayList(pDList); 
      getchar();

      printf("(8) 이중 연결 리스트에서 [의] 노드 삭제하기! \n");
      pNode = searchNode(pDList, "의");      	
      removeNode(pDList, pNode);
      displayList(pDList); 
      getchar();

      printf("(9) 리스트에서 [의] 노드 탐색하기! \n");
      pNode = searchNode(pDList, "의");
      if (pNode == NULL) printf("찾는 데이터가 없습니다.\n");
      else printf("pNode = [%s] 찾았습니다.\n", pNode->data);
      getchar();

      printf("(10) 리스트의 메모리 해제! \n");
      freeLinkedList(pDList);		// 리스트의 메모리 해제
      displayList(pDList); 
      getchar();
      return 0;
    }
    
    ```

### stack

### Queue

## Non-Linear Data Structure

### Tree

### Priority queue and heap

### graph

## Sort

## Search

## Table and Hash
