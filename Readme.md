# 목표: 진짜 골드

## 0. 개요
[Baekjoon Online Judge]([boj.kr](https://www.acmicpc.net/))에서 [제가 푼 문제들](https://www.acmicpc.net/user/twicedtna)의 코드를 저장하는 곳입니다. 틀린 코드도 있으며, 그 경우 코드 첫 부분에 틀렸다고 쓰여 있습니다. 같은 문제에 대해 여러 버전의 코드가 있을 수 있는데, 이 경우 보통 마지막 버전이 최종 버전입니다.

이 문서에는 제가 문제를 풀면서 염두에 두어야 할 것들을 따로 정리하고자 합니다. 제 편의를 위해 높임말을 쓸 수도 있고 쓰지 않을 수도 있으니 양해 부탁드립니다.


## 1. 알고리즘과 관련은 없지만 염두에 두어야 할 것들
### 1.1. 정답 출력 양식 꼼꼼히 확인하기(특히 구현에서). 
각 줄 맨 마지막에 공백이 허용되는지는 반드시 확인해 볼 것.
### 1.2. 문제 꼼꼼히 읽기
시키는 대로 안 해놓고 왜 안 되냐고 변명ㄴ
	
문제를 잘 읽어야 예외 상황 고려하기에도 편함.

### 1.3. 입력과 동시에 처리
계산에 있어서 점화식처럼 다음 입력값을 고려할 필요가 없을 때는 list에 미리 모든 입력을 다 저장한 후에 계산하는 것이 아니라 즉석에서 받으면서 처리하면 훨씬 효율적이다.
### 1.4. flag
두 subroutine을 번갈아서 하는 경우에는 flag를 사용하면 편하다.
### 1.5. 자주 참조되는 값은 새로운 변수에 할당
어떤 배열 형식 자료에서 같은 index의 값을 여러 번 사용하는 경우에는 새로운 변수를 만들어 값을 할당한 후 그 변수를 쓰는 것이 좋다.

왜? 정확하진 않지만 개인적인 생각을 써 본다.
```Python
a = 1
arr[i] = 1
```
위쪽은 a에 1 객체의 포인터가 들어 있고, 아래쪽은 arr 기본 주소에서 i만큼의 위치에 1 객체의 포인터가 들어 있다. 파이썬에서는 모든 것들이 reference type이니까 "i만큼의 위치"라는 말에서 'i' 역시 값이 아니라 포인터일 가능성이 높다고 본다. 그러면 arr[i]의 올바른 위치를 찾는 데 상대적으로 더 많은 시간이 걸릴 것이라 생각한다.


## 2. 슬라이딩 윈도우
재밌는 기법. 필요한 재료는 1. 창문의 크기, 2. 창문을 통해서 구하고자 하는 값(예를 들어 합계), 3. 경우에 따라 창문 양 끝의 원소를 기억하는 변수.


## 3. DFS/BFS
파이썬으로 풀 때 setrecursionlimit() 잊지 말기.

둘 중에 하나로 해서 안 되면 오기 부리지 말고 다른 걸로 해 보기.


## 4. Heap
insertion: O(log n)

pop: O(log n)

파이썬에서는 0번 index로 peek top 가능.

파이썬의 heapq 모듈은 최소 힙을 구현하기 때문에 최대 힙을 원하면 원소를 넣을 때 부호를 바꿔서 넣는 등의 추가 처리가 필요하다.


## 5. 그리디
그리디 문제의 핵심은 이 문제가 그리디 알고리즘으로 풀리는 문제임을 파악하는 것과 기준점을 찾는 것이다. 그리디 알고리즘의 증명법 세 가지 중 "Greedy Stays Ahead" 방법을 염두에 두고 어떤 값이 기준이 될 수 있는지 생각해야 한다. 이 기준점을 제대로 생각하지 못 하면 답을 볼 수밖에 없는 상황이 된다.