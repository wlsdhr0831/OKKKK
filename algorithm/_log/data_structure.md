# List

- **순서를 가진 데이터의 집합**을 가리키는 추상자료형
- 동일한 데이터 가능

# 구현 종류

### 1. 순차 리스트

- **배열** 기반 리스트
- **문제점**

    : 삽입 / 삭제 연산 과정에서 **원소 갯수가 많으면 연산이 늘어나고 작업시간 증가**

    : 배열 크기가 정해져 있어서 **메모리 낭비 / 새로운 배열** 필요

### 2. 연결 리스트

- **메모리 동적할당** 기반 리스트
- 논리적인 순서와 메모리 상의 물리적인 순서가 일치 하지 않음
- 개별적 위치 원소 레퍼런스를 연결 → 하나의 전체적인 자료구조
- **링크를 통해 원소에 접근** → 후작업 필요 없다
- **자료구조 크기를 동적으로 할당** → 효율적인 메모리 사용

## 연결 리스트 (Linked List)

### Node

- 하나의 원소에 필요한 데이터를 가지고 있는 자료 단위
- **데이터 필드** (멤버 변수)

    : **원소의 값**을 저장하는 자료구조 ( ex : char, student, book, ... )

- **링크 필드** (다음 노드와의 연결)

    : **다음 노드의 주소** (참조 값)를 저장하는 자료구조

### Head

- 리스트의 **처음 노드를 가리키는** 레퍼런스

### 1. 단순 연결 리스트 (Singly Linked List)

- 노드가 하나의 링크 필드에 의해 다음 노드와 연결
- 헤드가 가장 앞의 노드를 가리킴
- 최종적으로 NULL을 가리키는 노드가 리스트의 가장 마지막 노드

    ⇒ 마지막 노드를 찾고자 할 때는 반복문 수행

### 2. 이중 연결 리스트 (Doubly Linked List)

- 양쪽 방향으로 순회할 수 있도록 노드 연결
- 2개의 링크 필드, 1개의 데이터 필드
- 관리가 어렵다.

### 3. 원형 연결 리스트

- 각 노드는 다음 노드를 가리키고, 마지막 노드가 처음 노드를 가리키는 연결 리스트

### 4. 환형 이중 연결 리스트

- 처음 노드가 이전 노드로 마지막 노드를 가리키고, 마지막 노드가 다음 노드로 처음 노드를 가리키는 이중 연결 리스트

### 5. 해시 테이블

- 개체가 해시값에 따라 인덱싱

# 형태 종류

## 선형구조

- 자료 간의 관계가 **1:1 관계**
- **stack, queue, deque**

## 1. Stack

- **후입선출** (**LIFO**, Last-In-First-Out)

```java
top : 마지막 삽입된 원소 위치
push : top으로 값 삽입
pop : top 값 꺼내기
isEmpty : 공백 여부 ( O : true, X : false )
peek : top 값 반환
```

ex) 괄호 검사, 함수 호출, 중위 표기법을 후위 표기법으로 변환

## 2. Queue

- **선입선출** (**FIFO**, First-In-First-Out)

```java
front : 머리
rear : 꼬리
enqueue: rear으로 값 삽입
dequeue : front 값 꺼내기
isEmpty : 공백 여부 ( O : true, X : false )
isFull : 포화 여부 ( O : true, X : false )
peek : front 값 반환
```

## 비선형구조

- 자료 간의 관계가 **1:N 관계**
- **graph, tree**

## 1. graph

- 아이템 (사물, 추상적 개념)들과 이들 사이의 연결 관계
- **정점(vertex)들의 집합과 연결하는 간선(Edge)들의 집합으로 구성**된 자료구조
- M:N 관계를 가지는 원소 표현에 용이

```java
M : 정점의 갯수
|E| : 간선의 갯수
=> |E| <= M*(M-1) / 2
```

```java
1. 무향 그래프 (Undirected Graph)
2. 유향 그래프 (Directed Graph)
3. 가중치 그래프 (Weighted Graph)
4. 사이클 없는 방향 그래프 (DAG, Directed Acyclic Graph)
5. 완전 그래프 : 정점에 대해 가능한 모든 간선들을 가진 그래프
6. 부분 그래프 : 원래 그래프에서 일부의 정점, 간선을 제외한 그래프
```

### 인접 (Adjacency)

### 인접 (Adjacency)

- **두 정점에 간선이 존재한 상태**
- 완전 그래프에서는 임의의 두 정점들은 모두 인접 상태

```java
경로 : 간선들을 순서대로 나열한 것
단순 경로 : 경로 중 한 정점을 최대 한번만 지남
사이클 : 경로 중 시작한 정점 = 끝 정점
```

### 표현방법

- 간선의 정보를 저장하는 방식
- 메모리나 성능 고려해서 결정

**1) 인접 배열**

- M*M 크기의 2차원 배열 이용
- **두 정점을 연결하는 간선의 유(1)무(0)을 행렬**로 표현
- 행-열 번호는 그래프의 정점에 대응
- 단점 : 메모리 낭비

```java
[ 무향 그래프 ]
- 행 i합 = 열 i합 = i의 차수 = 인접 정점의 갯수
[ 유향 그래프 ]
- 행 i합 = i의 진출 차수
- 열 i합 = i의 진입 차수
```

**2) 인접 리스트**

- **각 정점마다 해당 정점으로 나가는 간선의 정보 저장**
- 각 정점에 대한 인접정점들을 순차적으로 표현
- 각 노드를 저장하는 연결리스트로 저장

```java
[ 무향 그래프 ]
- 노드 수 = 간선의 수 * 2
- 각 정점의 노드 수 = 정점의 차수
[ 유향 그래프 ]
- 노드 수 = 간선의 수
- 각 정점의 노드수 = 정점의 진출 차수
```

**3) 간선 리스트**

- **간선 (시작정점, 끝정잠)의 정보를 가진 객체로 표현**하여 리스트에 저장

### 서로소 집합 (Disjoint-Sets, 상호 배타 집합)

- **서로 중복된 원소가 없어 교집합이 없는 집합**
- 집합에 속한 하나의 대표자 ( **루트노드** )로 집합 구분
- 싸이클이 있는 그래프의 경우 재귀로 만들면 시간 오래 걸림 → 서로소로 해결

### 표현방법

: 리스트, 트리

### 집합연산

**1) 초기 값**

```java
void makeSet(int N){
	for(int i = 0; i < N; i++){
		root[i] = i;
	}
}
```

**2) 같은 집합인지 확인 후 연산**

```java
void union(int a, int b){
	int rootA = find(a);
	int rootB = find(b);
		
	if(rootA != rootB) {
		root[rootB] = a;
	}
}
```

**3) 부모 따라가며 루트 찾기**

```java
int find(int a){
	if(a == root[a]) return a;
	else return find(root[a]);
}
```

**⇒ 단점 : find 연산 시 시간 증가**

### 단점 해결 방법

**1) Rank-Rank를 이용한 Union**

- 트리의 높이를 관리해서 rank가 낮은 집합을 높은 집합에 붙인다

**2) Path Compression**

- 내 부모가 아닌 최종 루트를 알고 있자
- 특정 노르에서 루트까지 경로를 찾아가며 만나는 모든 조상 노드들의 값도 루트로 변경

```java
int find(int a){
	if(a != root[a]) {
		root[a] = find(root[a]);
	}
	return root[a];
}
```

## 2. tree

- **계층 관계**
- **상위 원소에서 하위 원소로 확장**되는 트리(나무) 모양 구조

    ⇒ 각 노드는 최대 1개의 부모 노드 존재

    ⇒ 각 노드는 자식 노드가 없거나 하나 이상 존재

- **간선(Edge)로 노드(Node) 들이 이어져 있음**

    ⇒ 2개의 노드 사이에는 **1개의 간선만** 존재

- 한개 이상의 노드로 이루어진 **유한 집합**
- **싸이클 없는 무향 연결 그래프**

```java
루트 (root) : 최상위 노드
부트리 (subroot) : 자식 노드들이 부모와 연결된 간선이 끊기면 생성 (자식 노드가 루트)

단말노드 (leaf node) : 자식 노드 없는 마지막 노드
형제노드 (sibling node) : 부모 노드가 같은 노드들
조상노드 : 간선을 따라 루트 노드까지 가는 경로에 있는 모든 노드들
자손노드 : 부트리에 연결된 하위레벨의 모든 노드들

차수 (degree) : 노드의 차수 (자식노드 갯수) / 트리의 차수 (노드의 차수 중 최댓값)
높이 : 노드의 높이 (루트노드까지의 간선 갯수) / 트리의 높이 ( 노드의 높이 중 최댓값)
```

### 이진 트리 (Binary Tree)

- 모든 트리들이 **최대 2개의 서브 트리**를 갖는 특별한 형태의 트리
- 왼쪽 자식 노드, 오른쪽 자식 노드
- 높이가 h인 이진 트리의 노드 갯수 : **h+1** ( 자식 노드 1개 ) ~ **2^(h+1) - 1** ( 포화 이진 트리)
- 탐색 시간 : **O( log2 N)**

### 완전 이진 트리 (Complete Binary Tree)

- 포화 이진 트리의 노드 번호 1번부터 n번까지 **빈자리가 없는 이진트리**
- 높이 : h
- 노드수 : n
- h+1 ≤ n ≤ 2^(h+1) - 1

### 편향 이진 트리 (Skewed Binary Tree)

- 높이 h에 대한 최소 개수의 노드 가짐
- 한쪽 방향의 자식 노드만 가짐
- 왼쪽 / 오른쪽 편향 이진 트리

### 수식 이진 트리 (Expression Binary Tree)

- 수식 트리라고도 함
- 연산자 (루트노드, 가지노드) / 피연산자, 숫자 (잎 노드)

### 이진 탐색 트리

- 탐색 작업을 효율적으로 하기 위한 자료구조
- 모든 원소는 서로 다른 유일한 키
- 왼쪽 서브 트리 < 루트 노드 < 오른쪽 서브 트리 : 노드 값 비교

    ⇒ 중위 순위하면 정렬된 값 나옴

```java
순위 (Traversal)
- 트리의 노드들을 체계적으로 방문 하는 것

1. 전위 순위 (Preorder Traversal)
: VLR
: 부모 - 왼쪽 자식 - 오른쪽 자식

2. 중위 순위 (Inorder Traversal)
: LVR
: 왼쪽 자식 - 부모 - 오른쪽 자식

3. 후위 순위 (Postorder Traversal)
: LRV
: 왼쪽 자식 - 오른쪽 자식 - 부모
```

```java
배열을 이용한 이진트리 표현
- 루트 번호 : 1
- 레벨 n에 있는 노드들 : 2^n ~ 2^(n+1)-1
- 왼쪽 자식 번호 = 부모 번호 * 2
- 오른쪽 자식 번호 = 부모 번호 * 2 + 1
- 단점
	: 편향 이진트리의 경우 메모리 공간 낭비
	: 트리 중간에 새로운 노드 삽입 혹은 삭제 시 배열 크기 변경 어려움 / 효율성 떨어짐
```

### 신장트리

- n개의 정점으로 이루어진 무향 그래프에서 **n개의 정점과 n-1개의 간선으로 이루어진 트리**

### 최소신장트리 ( MST, Minimum Spanning Tree )

- 무향 가중치 그래프에서 **신장트리를 구성하는 간선들의 가중치 합이 최소**인 신장트리
- 그래프에서의 **최소 비용 문제**

    : 두 정점 사이의 최소 비용 경로찾기

- E개의 간선, V개의 정점 ⇒ E**C**(V-1) 경우의 수

### Heap

- **완전 이진 트리**
- key 값을 가진 노드가 항상 root

    ⇒ 최소 힙은 최솟값, 최대 힙은 최댓값

### Priority Queue

- **Heap 자료구조**
- **우선 순위 높은 순**으로 꺼냄