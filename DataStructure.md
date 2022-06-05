# Data Structure 

## Recursion
> During executing algorithm or function, technique solving problem by recalling itself
* Example
  ```c
  #include <stdio.h>

  int fibonacci(int num)
  {
      if (num<=0)
          return 0;
      else if (num == 1)
          return 1;
      return fibonacci(num - 2) + fibonacci(num - 1);
  }

  int main()
  {
      int input = 0;
      int i = 0;

      printf("입력: ");
      scanf("%d", &input);

      for ( i = 0; i < input; i++)
      {
          printf("%d ", fibonacci(i));
      }
      puts("");
  }
  
  ```

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
* <strong>Accessible only at top position
* Last-In-First-Out (LIFO) 
  * Insert/Delete : only at top postition => O(1)
  * Peek => O(1)</strong>
  
  ![image](https://user-images.githubusercontent.com/64727012/172039199-c91b3a75-1b54-4559-ad3e-9d6522a31be2.png)

* Example (Infix)
  ```c
  #include<stdio.h>
  #include<string.h>
  #include<stdlib.h>

  typedef struct StackNode {
    char data;
    struct StackNode* front;
  } Node;

  typedef struct ArrayStack {
    Node* top;
    int index;
  } Stack;

  Stack* init() {
    Stack* pstack = (Stack*)malloc(sizeof(Stack));
    pstack->top = (Node*)malloc(sizeof(Node));
    pstack->index = -1;
    return pstack;
  }

  void push(Stack* pstack, int a) {
    Node* node = (Node*)malloc(sizeof(Node));
    node->front = NULL;
    node->data = a;
    if (pstack->index == -1) {
      pstack->top->front = node;
    }
    else {
      node->front = pstack->top->front;
      pstack->top->front = node;
    }
    pstack->index++;
  }

  void pop(Stack* pstack) {
    Node* temp;
    temp = pstack->top->front;
    pstack->top->front = pstack->top->front->front;
    free(temp);
    pstack->index--;
  }

  void infixToPostfix(char* exp) {
    Stack* operator = init();
    Stack* sen = init();
    int i = 0, count = 0;

    while (exp[i] != '\0') {
      if (exp[i] == '+' || exp[i] == '-' || exp[i] == '*' || exp[i] == '/') {
        if (exp[i] == '+' || exp[i] == '-') {
          push(operator, exp[i]);
        }
        else {
          push(sen, exp[i + 1]);
          push(sen, exp[i]);
          i += 2;
          count += 2;
          continue;
        }
      }
      else if (exp[i] == ')') {
        push(sen, operator->top->front->data);
        pop(operator);
        count++;
      }
      else if (exp[i] == '(') {
        i++;
        continue;
      }
      else {
        push(sen, exp[i]);
        count++;
      }
      i++;
    }
    if (operator->index != -1) {
      for (int i = 0; i <= operator->index; i++) {
        push(sen, operator->top->front->data);
        pop(operator);
        count++;
      }
    }

    char* temp = (char*)malloc(sizeof(char) * count);
    for (int i = 0; i < count; i++) {
      temp[count - 1 - i] = sen->top->front->data;
      pop(sen);
    }
    for (int i = 0; i < count; i++)
      exp[i] = temp[i];
    for (int i = count; i < strlen(exp); i++) {
      exp[i] = '\0';
    }
  }

  int evalPostfix(char *exp) {
    int result = 0;
    int i = 0;
    int temp1;
    int temp2;
    int sum;
    int tmp;
    Stack* num = init();
    char c;

    while (exp[i] != '\0') {
      if (exp[i] == '+') {
        temp1 = num->top->front->data;
        pop(num);
        temp2 = num->top->front->data;
        pop(num);
        sum = temp2 + temp1;
        push(num, sum);
      }
      else if (exp[i] == '-') {
        temp1 = num->top->front->data;
        pop(num);
        temp2 = num->top->front->data;
        pop(num);
        sum = temp2 - temp1;
        push(num, sum);
      }
      else if (exp[i] == '/') {
        temp1 = num->top->front->data;
        pop(num);
        temp2 = num->top->front->data;
        pop(num);
        sum = temp2 / temp1;
        push(num, sum);
      }
      else if (exp[i] == '*') {
        temp1 = num->top->front->data;
        pop(num);
        temp2 = num->top->front->data;
        pop(num);
        sum = temp1 * temp2;
        push(num, sum);
      }
      else {
        c = exp[i];
        push(num, atoi(&c));
      }
      i++;
    }
    return num->top->front->data;
  }


  int main(void) {
    int result;
    char express[] = "((2-5)+(3*4-1)-(9/3))";	// 중위 연산식


    printf("중위 표기식 : %s\n", express);

    infixToPostfix(express);                            // 후위 표기법
    printf("후위 표기식 : %s", express);

    result = evalPostfix(express);                    // 후위 연산식 계산
    printf("\n\n연산 결과 => %d", result);

    getchar();
  }

  
  ```

### Queue
* <strong>A first-In element is deleted first
* First-In-First-out (FIFO)
  * Insert/Delete => O(1)</strong>

  ![image](https://user-images.githubusercontent.com/64727012/172039374-76223ce2-b179-4d19-b838-0418f9d8c6d5.png)
* Example
  ```c
  #include <stdio.h>
  #include <stdlib.h>
  #define MAX_QUEUE_SIZE	200 

  typedef struct TaskCustomer {
    int	id;
    int	tArrival;
    int	tService;
  } Customer;

  typedef Customer Element;

  typedef struct CircularQueue {
    Element data[MAX_QUEUE_SIZE];	// 요소의 배열
    int	front;			// 전단
    int	rear;			// 후단
  } Queue;

  void error(char* str)
  {
    fprintf(stderr, "%s\n", str);
    exit(1);
  };
  // 큐의 주요 연산: 공통
  void init_queue(Queue *q) { q->front = q->rear = 0; ; }
  int is_empty(Queue *q) { return q->front == q->rear; }
  int is_full(Queue *q) { return q->front == (q->rear + 1) % MAX_QUEUE_SIZE; }
  int size(Queue *q) { return(q->rear - q->front + MAX_QUEUE_SIZE) % MAX_QUEUE_SIZE; }

  void enqueue(Queue *q, Element val)
  {
    if (is_full(q))
      error("  큐 포화 에러");
    q->rear = (q->rear + 1) % MAX_QUEUE_SIZE;
    q->data[q->rear] = val;
  }
  Element dequeue(Queue *q)
  {
    if (is_empty(q))
      error("  큐 공백 에러");
    q->front = (q->front + 1) % MAX_QUEUE_SIZE;
    return q->data[q->front];
  }
  Element peek(Queue *q)
  {
    if (is_empty(q))
      error("  큐 공백 에러");
    return q->data[(q->front + 1) % MAX_QUEUE_SIZE];
  }

  int	nSimulation;		// 시뮬레이션 시간 
  double probArrival;		// 단위시간에 도착하는 평균 고객 수 
  int	tMaxService;		// 한 고객에 대한 최대 서비스 시간 
  int	totalWaitTime;		// 전체 대기 시간 
  int	nCustomers;		    // 전체 고객의 수 
  int	nServedCustomers;	// 서비스를 받은 전체 고객 수 

  double rand0to1() { return rand() / (double)RAND_MAX; }

  void insert_customer(Queue *q, int arrivalTime)
  {
    Customer a;

    a.id = ++nCustomers;
    a.tArrival = arrivalTime;
    a.tService = (int)(tMaxService*rand0to1()) + 1;
    printf("  고객 %d 방문 (서비스 시간:%d분)\n", a.id, a.tService);
    enqueue(q, a);
  }
  void read_sim_params()
  {
    printf("시뮬레이션 할 최대 시간 (예:20) = ");
    scanf("%d", &nSimulation);
    printf("단위시간에 도착하는 고객 수 (예:0.5) = ");
    scanf("%lf", &probArrival);
    printf("한 고객에 대한 최대 서비스 시간 (예:~6) = ");
    scanf("%d", &tMaxService);
    printf("====================================================\n");
  }
  void run_simulation()
  {
    Queue q;
    Customer a;

    int clock = 0;
    int serviceTime = -1;

    init_queue(&q);
    nCustomers = totalWaitTime = nServedCustomers = 0;
    while (clock < nSimulation) {
      clock++;
      printf("현재시각=%d\n", clock);

      if (rand0to1() > probArrival)
        insert_customer(&q, clock);
      if (serviceTime>0) serviceTime--;
      else {
        if (is_empty(&q)) {
          printf("  현재 대기 고객 수       = %d\n", nCustomers - nServedCustomers);
          continue;
        }
        a = dequeue(&q);
        nServedCustomers++;
        totalWaitTime += clock - a.tArrival;
        printf("  고객 %d 서비스 시작 (대기시간:%d분)\n", a.id, clock - a.tArrival);
        serviceTime = a.tService - 1;
      }
      printf("  현재 대기 고객 수       = %d\n", nCustomers - nServedCustomers);
    }
  }

  void print_result()
  {
    printf("=================================================\n");
    printf("  서비스 받은 고객수      = %d\n", nServedCustomers);
    printf("  전체 대기 시간          = %d분\n", totalWaitTime);
    printf("  서비스고객 평균대기시간 = %-5.2f분\n",
      (double)totalWaitTime / nServedCustomers);
    printf("  현재 대기 고객 수       = %d\n", nCustomers - nServedCustomers);

  }
  #include <time.h>
  void main()
  {
    srand((unsigned int)time(NULL));
    read_sim_params();
    run_simulation();
    print_result();
  }
  ```

#### Deque (Double-Ended Queue)
* Expanded queue capable of insertion and deletion at both ends.

  ![image](https://user-images.githubusercontent.com/64727012/172039685-b590b1f1-74ed-4d6e-bbdd-ee9cf36eb063.png)
* Example
  ```c
  #include<stdio.h>

  typedef char Datatype;

  typedef struct QueueNode {
      Datatype data;
      struct QueueNode* next;
  }Node;

  typedef struct ArrayQueue {
      int index;
      Node* rear;
      Node* front;
  }Queue;

  Queue* init() {
      Queue* temp = (Queue*)malloc(sizeof(Queue));
      temp->front = (Node*)malloc(sizeof(Node));
      temp->rear = (Node*)malloc(sizeof(Node));
      temp->index = -1;
      return temp;
  }
  int isEmpty(Queue* pQueue) {
      if (pQueue->index == -1) {
          return 1;
      }
      else return 0;
  }

  void qInsertRear(Queue* pQueue, char data) {
      Node* temp = (Node*)malloc(sizeof(Node));
      Node* tmp = pQueue->front->next;
      temp->data = data;
      temp->next = NULL;

      if (isEmpty(pQueue) == 1) {
          pQueue->front->next = temp;
          pQueue->rear->next = temp;
          temp->next = temp;
      }
      else {
          pQueue->rear->next->next = temp;
          temp->next = pQueue->front->next;
          pQueue->rear->next = temp;
      }
      pQueue->index++;
  }

  void qInsertFront(Queue* pQueue, char data) {
      Node* temp = (Node*)malloc(sizeof(Node));

      temp->data = data;
      temp->next = NULL;

      if (isEmpty(pQueue) == 1) {
          pQueue->front->next = temp;
          pQueue->rear->next = temp;
          temp->next = temp;
      }
      else {
          temp->next = pQueue->front->next;
          pQueue->rear->next->next = temp;
          pQueue->front->next = temp;
      }
      pQueue->index++;
  }

  void qDeleteFront(Queue* pQueue) {
      if (isEmpty(pQueue) == 1)return 0;
      else {
          Node* tempF = (Node*)malloc(sizeof(Node));
          tempF = pQueue->front->next;
          pQueue->rear->next->next = pQueue->front->next->next;
          free(tempF);
          pQueue->front->next = pQueue->rear->next->next;
      }
      pQueue->index--;
  }

  void qDeleteRear(Queue* pQueue) {

      if (isEmpty(pQueue) == 1)return 0;
      else {
          Node* tempR = (Node*)malloc(sizeof(Node));
          Node* tmp = (Node*)malloc(sizeof(Node));
          tmp = pQueue->rear->next;
          tempR = pQueue->front->next;

          for (int i = 0; i < pQueue->index - 1; i++) {
              tempR = tempR->next;
          }
          tempR->next = pQueue->front->next;
          pQueue->rear->next = tempR;
          free(tmp);
      }
      pQueue->index--;
  }
  Datatype getQueueFront(Queue* pQueue) {
      return pQueue->front->next->data;
  }
  Datatype getQueueRear(Queue* pQueue) {
      return pQueue->rear->next->data;
  }
  void Palindrome(char* str) {
      printf("%s\n", str);
      int i = 0;
      Queue* sen = init();
      while (str[i] != '\0') {
          if (str[i] == ' ') {
              i++;
              continue;
          }
          else {
              qInsertRear(sen, str[i]);
              i++;
          }
      }

      int count = sen->index;

      if ((sen->index + 1) % 2 == 1) {
          for (int i = 0; i < count / 2; i++) {
              if (getQueueFront(sen) == getQueueRear(sen)) {
                  qDeleteFront(sen);
                  qDeleteRear(sen);

              }
              else {
                  printf("회문이아닙니다.\n\n");
                  return 0;
              }
          }
          printf("회문입니다.\n\n");
          return 0;
      }
      else {
          for (int i = 0; i < (count+1) / 2; i++) {
              if (getQueueFront(sen) == getQueueRear(sen)) {
                  qDeleteFront(sen);
                  qDeleteRear(sen);
              }
              else {
                  printf("회문이아닙니다.\n\n");
                  return 0;
              }
          }
          printf("회문입니다.\n\n");
          return 0;
      }
  }

  int main() {

      char str0[] = "madondam";
      char str1[] = "radar";
      char str2[] = "rotavator";
      char str3[] = "madam";
      char str4[] = "was it an cat i saw";
      char str5[] = "a man a plan a canal panama";
      char str6[] = "race car";
      char str7[] = "was it a cat i saw";
      char str8[] = "nurses run";
      char str9[] = "a man a plan an canal panama";

      // Palindrome checker
      Palindrome(str0);
      Palindrome(str1);
      Palindrome(str2);
      Palindrome(str3);
      Palindrome(str4);
      Palindrome(str5);
      Palindrome(str6);
      Palindrome(str7);
      Palindrome(str8);
      Palindrome(str9);

      return 0;
  }
  ```

## Non-Linear Data Structure

### Tree
* <strong>Non-linear data structure having 1:n relation between elements
* Hierarchical Data Structure</strong>

#### Term
* <strong>Position in tree
  * Root node => A first node of tree
  * Leaf node => nodes not having child nodes
  * Internal node => nodes having child nodes
* Relation between nodes
  * Parent node => Parent and child node are connected by edge
  * Child node
  * Ancestor node => All nodes in route from root node to parent node
  * descendent node => All nodes below a specific node
  * Sibling node => Child nodes of same parent node
* Property of node
  * Level => Distance from root node
  * Height => Value that plus 1 at height of a child node that is at the longest distance from a root node 
  * Degree => number of child node that a node has </strong> 

#### Complete Binary Tree
* <strong>All levels except last level are filled completely
* Even if last level is not filled fully, a node must be filled from left to right
* Implementation way : Array, Linked Data structure
* Example : Preorder, Inorder, Postorder</strong>
  ```c
  #include<stdio.h>

  typedef char datatype;

  typedef struct BinaryTree {
    datatype data;
    struct BinaryTree* lLink;
    struct BinaryTree* rLink;
  }Tree;

  Tree* init() {
    Tree* temp = (Tree*)malloc(sizeof(Tree));
    temp->lLink = NULL;
    temp->rLink = NULL;
  }

  void setData(Tree* pTree, datatype data) {
    pTree->data = data;
  }

  void makeLeftTree(Tree* sub, Tree* main) {
    main->lLink = sub;
  }
  void makeRightTree(Tree* sub, Tree* main) {
    main->rLink = sub;
  }


  void preorder(Tree* pTree) {
    if (pTree == NULL) return 0;
    printf("%c ", pTree->data);
    preorder(pTree->lLink);
    preorder(pTree->rLink);
  }
  void inorder(Tree* pTree) {
    if (pTree == NULL) return 0;
    inorder(pTree->lLink);
    printf("%c ", pTree->data);
    inorder(pTree->rLink);
  }
  void postorder(Tree* pTree) {
    if (pTree == NULL) return 0;
    postorder(pTree->lLink);
    postorder(pTree->rLink);
    printf("%c ", pTree->data);
  }

  int wholeNodeCount(Tree* pTree) {
    if (pTree == NULL) return 0;
    int left = wholeNodeCount(pTree->lLink);
    int right = wholeNodeCount(pTree->rLink);
    return 1 + left + right;
  }

  int terminalNodeCount(Tree* pTree) {
    if (pTree == NULL) return 0;
    if (pTree->lLink == NULL && pTree->rLink == NULL) return 1;
    int left = terminalNodeCount(pTree->lLink);
    int right = terminalNodeCount(pTree->rLink);
    return left + right;
  }
  int rootNodeHeight(Tree* pTree) {
    if (pTree == NULL) return 0;
    int left = rootNodeHeight(pTree->lLink);
    int right = rootNodeHeight(pTree->rLink);
    if (left > right) {
      return 1 + left;
    }
    else
      return 1 + right;
  }

  int main()
  {
    Tree* head = init();
    Tree* t1 = init();
    Tree* t2 = init();
    Tree* t3 = init();
    Tree* t4 = init();
    Tree* t5 = init();
    Tree* t6 = init();
    Tree* t7 = init();
    Tree* t8 = init();
    Tree* t9 = init();
    Tree* t10 = init();

    setData(head, 'A');
    setData(t1, 'B');
    setData(t2, 'C');
    setData(t3, 'D');
    setData(t4, 'E');
    setData(t5, 'F');
    setData(t6, 'G');
    setData(t7, 'H');
    setData(t8, 'I');
    setData(t9, 'J');
    setData(t10, 'K');

    makeLeftTree(t1, head);
    makeRightTree(t2, head);
    makeLeftTree(t3, t1);
    makeRightTree(t4, t1);
    makeLeftTree(t5, t2);
    makeRightTree(t6, t2);
    makeLeftTree(t7, t3);
    makeLeftTree(t8, t4);
    makeRightTree(t9, t4);
    makeRightTree(t10, t6);

    printf("preorder : ");
    preorder(head);
    printf("\n\ninorder : ");
    inorder(head);
    printf("\n\npostorder : ");
    postorder(head);
    printf("\n\n이진 트리 노드 개수 : %d", wholeNodeCount(head));
    printf("\n\n이진 트리 단말 노드 개수 : %d", terminalNodeCount(head));
    printf("\n\n이진 트리 높이 : %d", rootNodeHeight(head));
  }
  
  ```



### Priority queue and heap

### graph

## Sort

## Search

## Hashing
