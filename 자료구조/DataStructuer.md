# 자료구조
자료구조란 자료의 집합을 의미한다. 자료를 효율적으로 관리하고 사용할 수 있도록 자료를 구분하여 표현한 것을 말한다.


### 배열
데이터들을 나열하고 각 데이터에 인덱스를 부여하여 그 인덱스로 배열속에 데이터로 접근한다.

+ 배열은 같은 종류의 데이터를 저장하기에 간편하다.
+ 인덱스로 인한 빠른 접근이 가능하다.
+ 미리 배열의 크기를 정해야하기 때문에, 배열의 크기보다 더 많은 데이터를 추가하기에는 힘들다.
+ 배열속에 데이터를 삭제시키면 뒤에 데이터를 앞으로 당겨와야 하는 어려움이 있다.

### 큐
데이터들을 순차적으로 나열한다. 마치 줄을 서는 것과 같은 행위이다.<br>
`FIFO`와 `LILO`라는 특징을 가졌다
+ FIFO : First In First Out
    + 가장 먼저 들어온 값이 가장 먼저 나간다.
+ LILO : Last In Last Out
    + 가장 늦게 들어온 값이 가장 늦게 나간다.

### 스택
데이터를 제한적으로 접근할 수 있는 구조<br>
한쪽 끝에서만 데이터를 빼낼수있따.

![stack](https://miro.medium.com/max/473/1*IOwNU1HsdBktmOqChSjKoA.jpeg)

`FILO`와 `LIFO`라는 특징을 가졌다.
+ FILO : First In Last Out
    + 가장 먼저 들어온 값이 가장 늦게 나간다.
+ LIFO : Last In First Out
    + 가장 늦게 들어온 값이 가장 먼저 나간다.

#### 주요기능
+ pop : 가장 위에 있는 데이터를 꺼낸다.
+ push : 데이터를 스택에 넣는다.
+ peek : 가장 위에 있는 데이터를 반환한다.(stack에는 남아있는다. **값만 반환**)


![img](https://velog.velcdn.com/images%2Fbye9%2Fpost%2Ff8b77042-7b8b-4086-b153-eee6e4f9b61f%2Fimage.png)

<hr>

## Tree🌳
정점과 간점을 이용한 사이클이 존재하지 않은 그래프로, 계층이 있는 데이터를 표현하기에 좋다.
+ 비선형 자료구조이다
+ 계층적 관계를 표현한다.
+ 노드와 간선으로 연결되어있따.

![tree](https://i.imgur.com/6UeCp8t.png)

위에 있는 검정색 동그라미를 `노드`라고 부른다. 보통 이 노드에 데이터의 정보가 담긴다. 그리고 그 노드를 연결해주는 선을 `간선(edge)`이라고 부른다.<br>

### 트리 관련 용어
![tree](https://blog.kakaocdn.net/dn/Vw14V/btq9LqaPkJn/GK5HUpRCqgdQ7wqZOKTBkK/img.png)

+ 루트 노드(root node) : 부모가 없는 단 하나의 노드를 `루트 노드`라고 부른다.<br> 위에 그림에서는 `A`가 루트노드이다. 

+ 단말 노드(leaf node) : 자식이 없는 노드로 terminal 노드라고도 부른다.<br>
위에 그림에서는 `D,E,C`가 단말노드이다.

+ 내부 노드(internal node) : 단말노드가 아닌 노드, 위에 그림에서는 `A,B`가 내부 노드이다.

+ 간선(edge) : 노드와 노드를 이어주는 선

+ 형제(sibling) : 부모가 같은 노드들, 위에 그림에서는 `D,E`가 형제관계이다.

+ 노드의 깊이(depth) : 어떤 노드에 도달하기 위해 필요한 간선의 수.
위에 그림을 보면 `D의 깊이는 2이다`.

+ 노드의 레벨(level) : 트리의 특정 깊이를 가지는 노드의 집합.
위에 그림에서는 `Level 1 : B,C`이다.

+ 노드의 차수(degree) : 자식 노드의 `개수`. 위에 그림에서 B의 차수는 `2개`이다.

+ 트리의 차수(degree of tree) : 트리의 최대 차수


## 트리의 종류
### 이진트리(Binary Tree)
이진트리는 각 노드가 자식이 없거나 2개이상 있는 트리를 말한다.

![tree](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbUHUvy%2Fbtq9LrgvaEk%2F25BNRf1t3inHC7uijWfepk%2Fimg.png)

### 완전 이진트리, 전 이진 트리, 포화 이진 트리
**완전 이진 트리**

![img](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fb7BofG%2Fbtq9Eilu1J5%2F0HNO2KiWkBxTvERSJGHla0%2Fimg.png)

+ 완전이진트리는 트리의 마지막 레벨을 제외하고는 완전히 채워져야 한다.
+ 마지막 레벨에서는 왼쪽부터 채워져야 한다. 
+ 완전이진트리는 배열로 표현가능하다.

**전 이진 트리**

![img](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdSwyWw%2Fbtq9KmfrOlf%2F37ctrWKZKRSQJEZA7C9UMK%2Fimg.png)

+ 전이진트리는 모든 노드가 0개 또는 2개의 자식을 가지는 트리를 말한다.


**포화 이진 트리**

![img](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdfWC2R%2Fbtq9LqomTS7%2Frt4Io0pCfqBCckCs92CNz0%2Fimg.png)

+ 포화이진트리는 모든 레벨의 노드가 가득 채워져 있는 트리를 말한다.
+ 전이진트리의 특징인 노드가 0개 이거나 2개의 자식을 가졌다.

<hr>

### 이진 탐색 트리

![img](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcycePn%2Fbtq9IZY6CZx%2FT5jBed5A535HHx1GwnJLWk%2Fimg.png)

```
1. 각 노드에 중복되지 않은 키가 있다
2. 루트 노드를 기준으로 왼쪽에는 루트노드보다 작은 수, 오르쪽에는 큰 수 가 위치한다.
3. 좌우 서브 트리도 모두 이진 탐색 트리여야 한다.
```

#### 특징
이진 트리 탐색은 기존의 이진트리보다 탐색이 빠르다. 이진탐색트리의 탐색 연산은 트리의 높이가 `h`라면 `O(h)`의 시간 복잡도를 가진다.

### 이진 탐색 트리 탐색(Search)
다음과 같은 과정을 거친다.

```
1. 루트노드와 자신이 찾고자 하는 값을 비교한다. 자신이 찾는 값이 루트노드이면 탐색을 종료한다.
2. 자신이 찾는 값이 루트노드보다 작으면 왼쪽서브트리로 탐색을 한다.
3. 자신이 찾는 값이 루트노드보다 크면 오른쪽서브트리로 탐색을 한다.
```

위의 과정을 값을 찾을때까지 반복한다.

![img](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FpEBxn%2Fbtq9ReoXZUX%2F7zobmK5yQPPupKqGRgdHcK%2Fimg.png)

**위와같은 트리에서 5를 찾는 과정**
```
1. 5와 루트노드인 7을 비교한다. 5가 7보다 작으니 왼쪽서브트리로 이동한다.
2. 왼쪽서브트리인 3과 5를 비교한다. 5가 더 크니 오른쪽서브트리로 이동한다.
3. 키가 5인 노드를 찾았음으로 탐색을 종료한다.
```

### 이진 탐색 트리 삽입(Insert)
다음과 같은 과정을 거친다.

```
1. 삽입할 값이 루트노드와 비교해 같다면 오류가 발생한다.(중복 허용X)
2. 삽입할 값이 루트노드보다 작다면 왼쪽서브트리를 탐색하여 비었다면 값을 추가하고 값이 비어있지 않다면 다시 비교한다.
3. 삽입할 값이 루트노드보다 크다면 오른쪽서브트리를 탐색하여 비었다면 값을 추가하고 값이 비어있지 않다면 다시 비교한다.
```

다음 트리에 6을 삽입한다고 가정하자

![img](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FczCET0%2Fbtq9Ov57XGz%2F7HO8dK5PcnF24WwHYwjOOK%2Fimg.png)

```
1. 6이 7보다 작으니 왼쪽서브트리로 탐색을 한다.
2. 6이 3보다 크니 오른쪽서브트리로 탐색을 한다.
3. 6이 5보다 크니 오른쪽서브트리로 탐색을 한다.
3. 값이 비었으니 5의 오른쪽서브트리 위치에 6을 삽입한다.
```

![img](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdpBA2w%2Fbtq9RdRgKoI%2Flf9C3qqbPZtLCFYNSnJGXk%2Fimg.png)

6을 삽입하면 위의 그림과 같이 트리가 완성이 된다.

### 이진 탐색 트리의 삭제(delete)
삭제는 탐색과 삽입에 비해 조금 더 복잡하다. 삭제할 경우 3가지의 상황을 나누어서 구현해야한다.
```
1. 삭제하려는 노드가 단말노드인 경우
2. 삭제하려는 노드의 서브 트리가 하나인 경우(왼쪽 혹은 오른쪽 서브 트리)
3. 삭제하려는 노드의 서브 트리가 두 개인 경우
```


#### 삭제하려는 노드가 단말노드인 경우
![img](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FHjtkT%2Fbtq92w3hhp7%2Fpfi0hfaay4sj9MFMRU5rM0%2Fimg.png)

삭제하려는 노드가 단말노드(자식이 없다)인 경우에 삭제는 간단하다.

#### 삭제하려는 노드의 서브 트리가 하나인 경우(왼쪽 혹은 오른쪽 서브 트리)
![img](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fc2iif8%2Fbtq9Y5ZSC52%2FH5CewcVD4MvdsLBxI9QPm1%2Fimg.png)

이것도 간단하다. 8을 지우고 자식인 10을 부모자리에 위치시키면 된다.


#### 삭제하려는 노드의 서브트리가 두 개인 경우
![img](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FFa6xf%2Fbtq91pDx9u5%2FOiTC9pKYBxmjasKKTtzuK0%2Fimg.png)

이거는 조금 복잡하다. 두 가지 방법이 있다.

1) 삭제할 노드의 왼쪽서브트리에서 가장 큰 값을 해당 노드자리에 위치시킨다.

![img](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbcTUrX%2Fbtq92Q1tw0m%2FtyYJcuLUtWj7kD5k3qAeMK%2Fimg.png)

2) 삭제할 노드의 오른쪽서브트리에서 가장 작은 값을 해당 노드자리에 위치시킨다.

![img](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbI3IEY%2Fbtq9Rc54r92%2FnDvEWCXdq9qVmYaYiHKAAK%2Fimg.png)
<hr>


### Heap(힙)
최댓값 및 최솟값을 찾아내는 연산을 빠르게 하기 위해 고안된 완전 이진 트리를 기본으로 한 자료구조

힙에는 두가지 종류가 있다.
```
1. 부모노드의 키값이 자식노드보다 항상 큰 힙
2. 부모노드의 키값이 자식노드보다 항상 작은 힙
```

![img](https://velog.velcdn.com/images%2Fbye9%2Fpost%2F08c26c9b-6150-4ffd-96f8-ead915a9b783%2F%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-03-18%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%203.17.57.png)