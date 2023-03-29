# Data Structure

### 자료구조

- 효율적으로 데이터를 관리하고
- 수정, 삭제, 탐색, 저장할 수 있는
- **데이터의 집합**

### 목차

1. 복잡도
    1. 시간 복잡도
    2. 공간 복잡도
    3. 자료구조의 복잡도
2. 선형 자료 구조
    1. 연결 리스트(list)
    2. 배열(array)
    3. 벡터(vector)
    4. 스택(stack)
    5. 큐(queue)
3. 비선형 자료 구조
    1. 그래프
    2. 트리
        1. 이진 트리
        2. 이진 탐색 트리
        3. AVL 트리
        4. 레드 블랙 트리
    3. 힙
    4. 우선순위 큐
    5. 맵
    6. 셋
    7. 해시 테이블

## 복잡도

### 시간 복잡도

- 문제를 해결하는 데 걸리는 시간(t)과 입력(n)의 **함수 관계**
- why 시간 복잡도
    - 효율적인 코드로 개선하는 데 쓰이는 척도
      
        ![image-20230329224628979](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230329224628979.png)

### 공간 복잡도

- 프로그램을 실행시켰을 때 필요한 **자원 공간의 양**
- 예시)
    - `int a[1004]`
      
        ⇒ a배열은 1004 x 4바이트의 크기
        

### 자료구조에서의 복잡도

- 표
  
    ![image-20230329224646851](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230329224646851.png)
    

---

## 자료 구조 전체 개요

![image-20230329224701617](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230329224701617.png)

---

## 선형 자료 구조

- 요소가 일렬로 나열되어 있는 자료 구조
- ↔ 요소가 일렬로 나열하지 않고 자료 순서나 관계가 복잡한 자료구조 : 비선형 자료 구조

### 1. 연결 리스트(linked list)

- 데이터를 감싼 노드를 포인터로 연결해서 공간적인 효율성을 극대화시킨 자료 구조
- why 공간적인 효율성인가?(양창배)
    - 배열과 비교해보자
    - 배열은 크기가 정해져있다. 따라서 안쓰는 공간도 있어야하고, 부족할 경우, 문제가 될 수 있다.
    - 따라서 크기를 동적으로 할 수 있다는 장점이 있다.
- **삽입, 삭제** → O(1) : 연결만 잘 만들어 주면 된다.
- **탐색** → O(n) : 이동하면서 상자를 다 열어봐야한다.(랜덤 접근x, 순차적 접근)
- 종류
    - 싱글 연결 리스트 : next 포인터만 갖는다.
    - 이중 연결 리스트 : next / prev 포인터를 갖는다.
    - 원형 이중 연결 리스트 : next / prev 포인터를 갖고, 마지막 노드의 next 포인터가 헤드 노드를 가리킨다.
- C++에서의 활용예시
  
    ```cpp
    list<int> a;
    a.push_back(1); // a = 1
    a.push_back(2); // a = 1 2
    a.insert(1, 3); // a = 1 3 2 (1의 위치에 3을 집어넣는다.)
    a.pop_front();  // 맨 앞의 요소를 뺀다 a = 1 3
    a.pop_back();   // 맨 뒤의 요소를 뺀다. a = 3
    ```
    

### 2. 배열(array)

- 같은 타입의 변수들로 이루어져 있다.
- 크기가 정해져 있다.
- 순서가 있다.
- 인접한 메모리 위치에 있는 데이터들을 모아놓은 집합
- 중복 허용
- **접근** → O(1): **랜덤 접근**이 가능하다(랜덤 접근 ↔ 순차 접근)
- **삽입, 삭제** → O(n)

> 배열은 검색이 빠르고, 연결 리스트는 삽입과 삭제가 빠르다. 따라서 탐색이 많은 때는 배열, 삽입과 삭제가 자주 일어날 때는 연결 리스트를 활용하는 것이 좋다.
> 

### 랜덤 접근 vs 순차적 접근

- 랜덤 접근 : 동일한 시간에 배열과 같은 순차적인 데이터가 있을 때 임의의 데이터 인덱스에 해당하는 데이터에 접근할 수 있는 기능
- 순차적 접근 : 데이터를 저장된 순서대로 검색해야 한다.

### 3. 벡터(vector)

- 동적으로 요소를 할당할 수 있음 → 동적 배열
- 컴파일 시점에 요소의 개수를 모를 때 사용한다.
- 중복 허용, 순서가 있음
- 배열과 마찬가지로 **랜덤 접근** 가능! 탐색 → O(1)
- C++ 활용 예시
  
    ```cpp
    vector<int> v;
    v.push_back(1); // 시간복잡도 : O(1)
    v.pop_back();   // 시간복잡도 : O(1)
    v.erase(v.begin(), v.begin() + 1);      // [first, last) 범위의 요소를 삭제한다.
    v.count(v.begin(), v.end(), 값); // [first, last) 범위에서 해당 값이 몇 개인지 찾음 : O(n)
    find(v.begin(), v.end(), 값); // [first, last) 범위에서 해당 값을 찾는다. : O(n)
    fill(v.begin(), v.end(), 값); // [first, last) 범위에 해당 값을 넣는다. : O(n)
    v.clear();  // 배열을 초기화한다. -> 안에 있는 값을 다 지운다.
    ```
    

### 4. 스택(stack)

- LIFO(Last In First Out) : 가장 마지막으로 들어간 데이터가 가장 첫 번째로 나오는 성질
- 활용 예시 : 재귀적인 함수, 웹 브라우저 방문 기록, DFS(재귀적으로 자동)
- **삽입, 삭제** → O(1)
- 탐색 → O(n)
- C++ 활용 예시
  
    ```cpp
    stack<int> stk;
    stk.push(1); // 1 <->
    stk.push(2); // 1 2 <->
    stk.push(3); // 1 2 3 <->
    stk.top();   // 3
    stk.size();  // 3
    stk.pop();   // 1 2 <->
    stk.size();  // 2
    ```
    

### 5. 큐(queue)

- FIFO(First In First Out) : 가장 처음으로 들어간 데이터가 가장 첫 번째로 나오는 성질
- 활용 예시 : BFS, 프로세스, 스레드 행렬, 네트워크 기다리는 행렬, 캐시
- **삽입, 삭제** → O(1)
- 탐색 → O(n)
- C++ 활용 예시
  
    ```cpp
    queue<int> q;
    q.push(1); // <- 1 <-
    q.push(2); // <- 1 2 <-
    q.push(3); // <- 1 2 3 <-
    q.front(); // 1
    q.size();  // 3
    q.pop();   // <- 1 2 <-
    q.size();  // 2
    ```
    

> 스택과 큐는 삽입, 삭제에 능한 자료구조이다.
> 

---

## 비선형 자료 구조

- 일렬로 나열하지 않고 자료 순서나 관계가 복잡한 구조
- 트리, 그래프

### 1. 그래프(Graph)

- 정점(Vertex)과 간선(Edge)으로 이루어진 집합, 자료구조
- 가중치 : 간선과 정점 사이에 드는 비용

### 2. 트리(Tree)

- 그래프 중 하나
- 계층적 구조
- (양창배) 싸이클을 이루지 않는다.
- 루트 노드, 내부 노드, 리프 노드로 이루어져 있다.
  
    ![image-20230329224722062](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230329224722062.png)
    
    - 루트 노드 : 가장 위에 있는 노드
    - 내부 노드 : 루트 노드와 리프 노드 사이에 있는 노드
    - 리프 노드 : 자식 노드가 없는 노드
- 참고) 트리로 이루어진 집합을 ‘숲’이라고 한다.
- 트리의 높이와 레벨
  
    ![image-20230329224732928](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230329224732928.png)
    
    - 깊이
        - 루트 노드에서 특정 노드까지 최단 거리로 갔을 때의 거리
        - 그림에서 4번 노드의 깊이는 2이다.
    - 높이
        - 루트 노드에서 리프 노드와의 거리 중 가장 긴 거리
    - 레벨
        - 보통 깊이와 같은 의미를 지닌다.
        - 위의 그림에서 1번 노드가 0레벨이라면, 2번, 3번 노드는 1레벨이다.
        - 위의 그림에서 1번 노드가 1레벨이라면, 2번, 3번 노드는 2레벨이다.
        - 차이의 절댓값으로 인지하면 될 듯하다.
    - 서브 트리
        - 트리 내의 하위 집합
        - 트리 내에 있는 부분집합
        - 5, 6, 7번 노드가 그림에서의 전체 트리의 하위 집합으로, “저 노드들은 서브트리”라고 함.

### 이진 트리

- 자식 노드의 개수가 2개 이하의 트리
- 분류
    - **정이진 트리(full binary tree)** : 자식 노드가 0 또는 2개인 이진 트리
      
        ![image-20230329224758428](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230329224758428.png)
        
    - **완전 이진 트리(complete binary tree)**
      
        ![image-20230329224810157](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230329224810157.png)
        
        - 왼쪽부터 채워져 있는 이진 트리
        - 마지막 레벨을 제외하고 완전히 채워져 있음
        - 마지막 레벨의 경우, 왼쪽부터 채워져 있음
    - **변질 이진 트리(degenerate binary tree)**
      
        !![image-20230329224821680](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230329224821680.png)
        
        - 자식 노드가 하나밖에 없는 이진 트리(한 줄짜리!)
    - **포화 이진 트리(perfect binary tree)**
      
        ![image-20230329224833123](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230329224833123.png)
        
        - 모든 노드가 꽉 차 있는 이진 트리
    - **균형 이진 트리(balanced binary tree)**
      
        ![image-20230329224844095](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230329224844095.png)
        
        - 왼쪽과 오른쪽 노드의 높이 차이가 1이하인 이진 트리
        - map, set을 구현하는 레드 블랙트리도 균형 이진 트리 중 하나이다.
- 이진트리의 구현(객체지향)
  
    ```cpp
    #include<bits/stdc++.h>
    using namespace std;
    
    class Node{
        public:
            int data;
            Node* left;
            Node* right;
        
        // 생성자 함수
        Node(int val){
            data = val;
            left = NULL;
            right = NULL;
        }
    };
    
    int main(){
        Node* root = new Node(1);
        /*
                1
               / \
            NULL NULL
        */
        root->left = new Node(2);
        /*
                1
               / \
              2  NULL
             / \
           NULL NULL
        */
        root->right = new Node(3);
        /*
                  1
               /    \
              2      3
            /  \    /   \
         NULL NULL NULL NULL
        */
        root->left->left = new Node(4);
        /*
                  1
                /    \
               2      3
             /  \    /  \
            4  NULL NULL NULL
          /  \
        NULL NULL
        */
        cout << root->data << "\n";
        return 0;    
    }
    ```
    
    - 마지막 줄을 통해서 한 가지 사실을 알 수 있다.
      
        ⇒ root는 포인터인데, 해당 포인터의 멤버변수의 값을 `→` 화살표를 통해서 확인할 수 있다.
        

> 실제 알고리즘 풀이에서는 객체지향으로 풀기 보단, 벡터를 통해서 간단하게 푸는 경우가 많다.
> 

### 이진 탐색 트리

- BST(Binary Search Tree)
  
    ![image-20230329224855795](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230329224855795.png)
    
- 왼쪽 노드 값 < 노드 값 < 오른쪽 노드 값
- 검색에 용이하다 → O(logN), 최악 O(N): 선형적일 때
  
    ![image-20230329224904293](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230329224904293.png)
    
    평균
    
    ![image-20230329224912147](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230329224912147.png)
    
    최악
    

### AVL 트리

- AVL(Adelson-Velsky and Landis tree)
  
    ![image-20230329224920563](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230329224920563.png)
    
- 이진 탐색 트리의 최악의 경우(O(n)), 즉 선형 적인 트리가 되는 것을 방지한다
- 스스로 균형을 잡는 이진 탐색 트리
- 두 자식 서브트리의 높이는 항상 최대 1만큼 차이 난다.
- 탐색, 삽입, 삭제 → O(logN)
- 삽입, 삭제를 할 때마다 균형이 안 맞는 것을 맞추기 위해 트리 일부를 왼쪽 혹은 오른쪽으로 회전시키며 균형을 잡는다.

### 레드-블랙 트리

- 균형 이진 트리의 일종
    - 균형 이진 트리? → 왼쪽과 오른쪽 노드의 높이 차이가 1이하인 이진 트리
- 탐색, 삽입, 삭제 → O(logN)
- 각 노드는 빨간색 혹은 검은색의 색상을 추가 비트를 저장하며, 삽입 및 삭제 중에 트리가 균형을 유지하도록 하는 데에 사용
- C++의 set, multiset, map, and multimap을 구현하는 데에 사용함
- 모든 리프 노드와 로트 노드는 블랙, 어떤 노드가 레드이면 그 노드의 자식은 반드시 블랙
  
    ⇒ 이 방법으로 균형을 잡는다.
    

## 3. 힙(Heap)

- 완전 이진 트리 기반 자료구조
    - 완전 이진 트리? → 왼쪽부터 채워지는 이진트리
- 최소 힙, 최대 힙 두 가지가 존재한다.
- 해당 힙에 따라 특정한 특징을 지킨 트리
- **최소 힙**
    - 루트 노드에 있는 키는 모든 자식에 있는 키 중 가장 커야한다.(루트 노드-최솟 값)
    - 각 노드의 자식 노드와의 관계도 이와 같은 특징이 재귀적으로 이루어져 있다.
- **최대 힙**
    - 루트 노드에 있는 키는 모든 자식에 있는 키중 가장 작아야 한다.(루트 노드-최댓 값)
    - 각 노드의 자식 노드와의 관계도 이와 같은 특징이 재귀적으로 이루어져 있다.

### 최대 힙의 삽입

- 새로운 요소가 들어오면, 일단 새로운 노드를 힙의 마지막 노드에 이어서 삽입
- 새로운 노드를 부모 노드들과의 크기를 비교하여 교환해서 힙의 성질을 만족 시킨다.

### 최대 힙의 삭제

- 루트 노드가 삭제되고, 그 이후 마지막 노드와 루트 노드를 스왑하여 또다시 스왑 등의 과정을 거쳐 재구성된다.

## 4. 우선순위 큐

- 우선순위 대기열
- 대기열에서 우선순위가 높은 요소가 우선순위가 낮은 요소보다 먼저 제공되는 자료구조
- 힙을 기반으로 구현된다.

## 5. 맵

- 특정 순서에 따라 키와 매핑된 값의 조합으로 형성된 자료구조
- 레드 블랙 트리 기반 구조를 기반으로 형성
- 삽입되면 자동으로 정렬
- **해시 테이블을 구현할 때 사용한다.(by unordered_map)**
- 맵의 종류
    - map(정렬 보장)
    - unordered_map(정렬 보장 x)

## 6. 셋(set)

- 특정 순서에 따라 고유한 요소를 저장하는 **컨테이너**
- 중복되는 요소는 없고, 오로지 희소한(unique) 값만 저장하는 자료 구조

## 7. 해시 테이블

[노마드코더 hash table 설명](https://www.youtube.com/watch?v=HraOg7W3VAM)

- 무한에 가까운 데이터들을 유한한 개수의 해시 값으로 매핑한 테이블
- 삽입, 삭제, 탐색 → 평균 O(1)
- unordered_map으로 구현

추가

- 대부분의 프로그래밍 언어에 자체적으로 내장 (똑똑한 사람들이 hash function을 잘 만들어 놨다)
- python에서 dictionary 조회의 시간 복잡도가 O(1)인 이유

원리

- hash table에는 내부적으로 array가 존재 (`index : value` 쌍의 array)
- hash function `f`에 대해, `f(key)`를 계산하면 `value`와 연관된 `index`가 출력됨
    - 즉 `f(key) == index`, `hash_table[index] = value`
- 만약 key1, key2 가 hash function에 대해 같은 값을 출력한다면?
    - 해당 `index` 안에 `key, value` 들로 이루어진 배열을 다시 저장, 그곳에서 선형탐색