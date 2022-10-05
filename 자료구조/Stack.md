# Stack
```C
// 파일명 : stack.c
// 목표 : 배열과 연결리스트를 사용해서 
// 스택(push, pop, peek)의 기능을 구현
#include<stdio.h>
#include<stdlib.h>

// 1. 배열 기반 구현
#define STACK_SIZE 10
int topIdx;        // 스택의 맨 위 데이터가 어디에 저장?
int aryStack[STACK_SIZE];

void init() {
	topIdx = -1;
}

void push(int data) {
	aryStack[++topIdx] = data;
}
```