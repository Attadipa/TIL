# 이진트리순회(DFS : Depth-First Search)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

아래 예시는 전위순회를 표현한 것이고

sysout문이 recursive(root.lt)와 recursive(root.rt) 사이에 있으면 중위순회,

sysout문이 recursive(root.rt) 아래에 있으면 후위순회이다


풀이

```java
package ExMy;

class Node {
	int value;
	Node lt;
	Node rt;
	
	Node(int value){
		this.value = value;
	}
}

public class Main {
	
	public static void recursive(Node root) {
		if(root == null) return;
		else {
			System.out.print(root.value + " ");
			recursive(root.lt);
			recursive(root.rt);
		}
	}
	
	public static void main(String[] args) {
		Node root = new Node(1);
		root.lt = new Node(2);
		root.rt = new Node(3);
		root.lt.lt = new Node(4);
		root.lt.rt = new Node(5);
		root.rt.lt = new Node(6);
		root.rt.rt = new Node(7);
		recursive(root);
	}
}
```