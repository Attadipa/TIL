# Tree 가장 말단노드까지의 가장 짧은 경로(BFS)

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
	
	public static int bfs(Node root) {
		Queue<Node> q = new LinkedList<>();
		q.offer(root);
		int lev = 0;
		while(!q.isEmpty()) {
			int leng = q.size();
			for(int i = 0 ; i<leng ; i++) {
				Node node = q.poll();
				if(node.lt==null && node.rt==null) return lev;
				if(node.lt!=null) q.offer(node.lt);
				if(node.rt!=null) q.offer(node.rt);
			}
			lev++;
		}
		return lev;
	}
	
	public static void main(String[] args) {
		Node root = new Node(1);
		root.lt = new Node(2);
		root.rt = new Node(3);
		root.lt.lt = new Node(4);
		root.lt.rt = new Node(5);
		int lev =0;
		bfs(root);
	}
}
```