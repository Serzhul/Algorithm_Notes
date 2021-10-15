# 큐(Queues)

# 프로그래밍에서 사용되는 큐

- 백그라운드 작업
- 리소스 업로딩
- 프린팅, 작업 프로세싱

## 배열로 큐 구현하기

- FIFO 조건을 만족시키려면 자바스크립트 내장함수인 unshift와 pop을 이용해 구현할 수 있다.

## 클래스로 큐 만들기

```jsx
class Queue {
  constructor() {
    this.first = null;
    this.last = null;
    this.size = 0;
  }
}

class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}
```

## Enqueue 의사 코드

- 특정 값을 인자로 받는다.
- 전달 받은 값으로 새로운 노드를 만든다.
- 큐에 노드가 없으면, 새로 만든 노드를 큐의 first, last 속성으로 한다.
- 노드가 있으면, 새로 만든 노드를 큐의 마지막 노드의 next 속성으로 하고, 큐의 last 속성을 새로 만든 노드로 한다.
- queue의 사이즈를 1만큼 증가시킨다.

```jsx
enqueue(val) {
    let newNode = new Node(val);
    if (!this.first) {
      this.first = newNode;
      this.last = newNode;
    } else {
      this.last.next = newNode;
      this.last = newNode;
    }

    return ++this.size;
  }
```

## Dequeue 의사 코드

- 큐의 first 속성 값이 없다면 null을 반환한다.
- first 속성 값을 변수로 저장한다.
- first와 last 속성이 같다면(큐에 노드가 하나밖에 없다면), first와 last는 null로 한다.
- 노드가 1개 이상 있다면, first 속성은 next의 first가 된다.
- 사이즈를 1만큼 감소한다.
- dequeue된 노드의 값을 반환한다.

```jsx
dequeue() {
    if (!this.first) return null;
    let temp = this.first.val;

    if (this.first === this.last) {
      this.last = null;
    }
    this.first = this.first.next;
    this.size--;
    return temp.value;
  }
}
```

## 큐의  Big O

- 삽입(Insertion) - $O(1)$
- 삭제(Removal) - $O(1)$
- 탐색(Searching) - $O(N)$
- 접근(Access) - $O(N)$

## 요약

- 큐는 FIFO 자료구조이며, 모든 요소들은 먼저 들어간 것이 먼저 나온다.
- 큐는 작업을 프로세싱 하고, 좀 더 복잡한 자료구조들을 설계하는데 유용하다.
- 삽입과 삭제의 시간 복잡도는 $O(1)$이 된다.
