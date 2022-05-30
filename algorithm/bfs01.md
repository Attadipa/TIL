# 이진트리 레벨탐색(BFS : Breadth-First search)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비


풀이

```java
import java.util.LinkedList;
import java.util.Queue;

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
		Queue<Node> q = new LinkedList<>();
		q.offer(root);
		int L = 0;
		while(!q.isEmpty()) {
			System.out.print("L"+L+" : ");
			int leng = q.size();
			for(int i = 0 ; i<leng; i++) {
				Node node = q.poll();
				System.out.print(node.value+" ");
				if(node.lt!=null) q.offer(node.lt);
				if(node.rt!=null) q.offer(node.rt);
			}
			L++;
			System.out.println();
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