# 연결 리스트
파일명 : linkedList.c

연결리스트의 특징
데이터가 물리적으로 인접해있지는 않으나
데이터간의 '연결고리'를 사용하여 연속적으로 저장(하는 것처럼) 관리

'노드' : 데이터를 저장하는 하나의 단위
'노드'에는 '데이터'를 저장 + '다음 노드를 찾아갈 수 있는 주소'를 저장
```c
#include<stdio.h>
typedef struct _node {
	int data;
	struct _node* next;
} Node;

// '가변적', '동적' 데이터를 저장하는 길이가 정해져 있지 않음 => C에서의 '동적 할당'
Node* head;
Node* tail;
Node* cur;			// current(현재 위치와 관련된 포인터
int main() {
	Node n1, n2, n3;
	n1.data = 10;
	n1.next = &n2;
	n2.data = 20;
	n2.next = &n3;
	n3.data = 30;
	n3.next = NULL;

	head = &n1;
}

void insert(int data) {
	// 1. 새로운 노드를 만듦
	Node* newNode = (Node*)malloc(sizeof(Node));
	Node n1;
	newNode->data = data;
	newNode->next = NULL;

	n1.data = data;
	n1.next = NULL;
	// 상황에 따라 삽입하는 방식이 약간 달랐음
	if (head == NULL) {		// 연결리스트에 노드가 전혀 존재하지 않을 때
		head = newNode;
		tail = newNode;
	}
	else {
		head->next = newNode;
	}
	tail = newNode;
}
```