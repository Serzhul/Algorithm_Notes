# 스택(Stacks)

# 스택이란?

- LIFO의 특성을 가진 자료구조이다.
    - LIFO(Last In First Out) : 후입선출, 즉 나중에 들어간 item이 먼저 나오는 구조를 말한다. (예: 책 쌓기)
- 스택에 마지막으로 추가된 요소는 스택에서 제거되는 첫 번째 요소가 된다.

# 스택이 사용되는 곳

- 함수 요청들을 관리하는 용도 ⇒ Call Stack
- Undo / Redo ⇒ 실행 순서에 따라 취소하거나 재실행
- 라우팅 역시 스택처럼 취급됨.

## 스택을 배열로 구현하기

- 배열로 스택을 구성하는 것은 index를 이동해야 하기 때문에 비효율적이다.
- 따라서 자바스크립트에서 일반적으로는 링크드 리스트를 이용해 구현하며, 굳이 배열을 사용하고 싶다면 push(), pop()같은 내장함수를 이용해 마지막 인덱스에서 데이터를 컨트롤하는 것이 좋다.

## Pushing 메소드 의사코드

- 이 메소드는 값을 인자로 받는다.
- 그 값으로 새로운 노드를 만든다.
- 스택에 노드가 없으면, first 와 last 속성은 새로 만든 노드로 한다.
- 만약 하나의 노드라도 있으면 변수를 만들어 현재 스택의 first 속서을 저장한다.
- 새로 만든 노드의 first속성은 초기화 한다.
- 이전에 만든 변수의 노드를 노드의 next 속성으로 한다.
- 스택의 크기를 1 증가한다.

```jsx
push (val) {
	var newNode = new Node(val);
	if(!this.first) {
		this.first = newNode;
		this.last = newNode;
	}
	else {
		var temp = this.first;
		this.first = newNode;
		this.first.next = temp;
	}
	return ++this.size;
}
```

## Pop 메소드 의사코드

- 스택에 노드가 없으면 null을 반환한다.
- 임시 변수를 만들어 스택의 first 속성을 저장한다.
- 하나의 노드만 있다면 first와 last 속성을 null로 한다.
- 하나 이상의 노드만 있다면 first 속성을 현재 first의 next 속성으로 한다.
- 리스트의 크기를 1만큼 줄인다.
- 제거된 노드를 반환한다.

```jsx
pop() {
        if(!this.first) return null;
        var temp = this.first;
        if(this.first === this.last) {
            this.last = null;
        }
        this.first = this.first.next;
        this.size--;
        return temp.value;
    }
```

## 스택의 Big O

- 삽입(**Insertion) - $O(1)$**
- 삭제(**Removal) - $O(1)$**
- 탐색(Searching) - $O(N)$
- 접근(Access) - $O(N)$

## 요약

- 스택은 LIFO 자료구조이며 이는 마지막에 들어간 값이 첫 번째로 나오는 것을 의미한다.
- 스택은 콜 스택이라 불리는 함수의 호출을 관리하는 등에 사용되며, 그 외에도 undo/redo 기능, 라우팅(방문했던 페이지를 다시 돌아가는 기능) 등 많은 곳에서 사용된다.
- 자바스크립트에는 내장되어 있지 않지만, 비교적 간단하게 구현할 수 있다.