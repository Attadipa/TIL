# Tree 가장 말단노드까지의 가장 짧은 경로(DFS)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비


풀이

```java
class Node {
	int value;
	Node lt;
	Node rt;
	
	Node(int value){
		this.value = value;
	}
}

public class Main {
	
	public static int recursive(int lev, Node root) {
		if(root.lt==null && root.rt==null) return lev;
		else return Math.min(recursive(lev+1,root.lt), recursive(lev+1,root.rt));
		
	}
	
	public static void main(String[] args) {
		Node root = new Node(1);
		root.lt = new Node(2);
		root.rt = new Node(3);
		root.lt.lt = new Node(4);
		root.lt.rt = new Node(5);
		int lev =0;
		recursive(lev,root);
	}
}
```