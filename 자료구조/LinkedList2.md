# LinkedList
파일명 : linkedList.c

연결리스트의 특징
데이터가 물리적으로 인접해있지는 않으나
데이터간의 '연결고리'를 사용하여 연속적으로 저장(하는 것처럼) 관리

'노드' : 데이터를 저장하는 하나의 단위
'노드'에는 '데이터'를 저장 + '다음 노드를 찾아갈 수 있는 주소'를 저장
```c
#include<stdio.h>
#include<stdlib.h>
typedef struct _node {
	int data;
	struct _node* next;
} Node;

// '가변적', '동적' 데이터를 저장하는 길이가 정해져 있지 않음 => C에서의 '동적 할당'
Node* head;
Node* tail;
Node* cur;			// current(현재 위치와 관련된 포인터

void insert(int data) {
	// 1. 새로운 노드를 만듦
	Node* newNode = (Node*)malloc(sizeof(Node));
	newNode->data = data;
	newNode->next = NULL;


	// 상황에 따라 삽입하는 방식이 약간 달랐음
	if (head == NULL) {		// 연결리스트에 노드가 전혀 존재하지 않을 때
		head = newNode;
	}
	else {
		tail->next = newNode;
	}
	tail = newNode;
}
// 출력, 조회 (-> 변경, 삭제)
void printAll() {
	Node* cur = head;
	while (cur != NULL) {
		// 1. 읽어들이고
		printf("[%d]", cur->data);
		// 2. 이동시키고
		cur = cur->next;
	}
	
}
// 조회(-> 변경, 삭제)
int find(int findData) {
	Node* cur = head;
	while (cur != NULL) {
		// 1. 존재할 경우
		if (cur->data == findData) {
			return cur->data;
		}
		// 다음 노드를 방문하기 위한 코드
		cur = cur->next;
	}
	// 2. 그렇지 않을 경우
	return -1;
}
// 삽입(데이터의 첫 번째 위치에 새로운 데이터가 삽입되도록 하기)
// 삽입(데이터가 정렬되어서 삽입되도록 하기)
int main() {
	insert(1); insert(3); insert(5); insert(7); insert(9);
	printAll();
}
```