# 원더랜드(최소스패닝트리 : 프림 - priorityQueue)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

내 풀이

```java
import java.util.PriorityQueue;
import java.util.Scanner;

class Edge implements Comparable<Edge>{
	int vex1;
	int vex2;
	int cost;
	public Edge(int vex1, int vex2, int cost) {
		super();
		this.vex1 = vex1;
		this.vex2 = vex2;
		this.cost = cost;
	}
	@Override
	public int compareTo (Edge e) {
		return this.cost - e.cost;
	}
	
}

public class Main {
	static int cnt,answer=0;
	static int[] unf;
	static PriorityQueue<Edge> pq = new PriorityQueue<>();
	public static int find(int v) {
		if(unf[v]==v) return v;
		else return unf[v] = find(unf[v]);
	}
	public static void Union(Edge edge) {
		int fa = find(edge.vex1);
		int fb = find(edge.vex2);
		if(fa!=fb) {
			unf[fa] = fb;
			answer+=edge.cost;
			cnt++;
		}
		
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int v = sc.nextInt();
		int e = sc.nextInt();
		unf = new int[v+1];
		for(int i = 1 ; i<=v ; i++) unf[i] = i;
		for(int i = 0 ; i<e ; i++) {
			int v1 = sc.nextInt();
			int v2 = sc.nextInt();
			int c = sc.nextInt();
			pq.offer(new Edge(v1,v2,c));
		}
		for(int i = 0 ; i<e ; i++) {
			Edge edge = pq.poll();
			Union(edge);
			if(cnt==v-1) break;
		}
		System.out.println(answer);
	}	
}
```

해설

```java
import java.util.ArrayList;
import java.util.PriorityQueue;
import java.util.Scanner;

class Edge implements Comparable<Edge>{
	int vex;
	int cost;
	public Edge(int vex, int cost) {
		super();
		this.vex = vex;
		this.cost = cost;
	}
	@Override
	public int compareTo (Edge e) {
		return this.cost - e.cost;
	}
}

public class Main {
	
	public static void main(String[] args) {	
		Scanner sc = new Scanner(System.in);
		int v = sc.nextInt();
		int e = sc.nextInt();
		int[] check = new int[v+1];
		PriorityQueue<Edge> pq = new PriorityQueue<>();
		ArrayList<ArrayList<Edge>> graph = new ArrayList<>();
		for(int i = 0 ; i<=v ; i++) {
			graph.add(new ArrayList<Edge>());
		}
		for(int i = 0 ; i<e ; i++) {
			int v1 = sc.nextInt();
			int v2 = sc.nextInt();
			int cost = sc.nextInt();
			graph.get(v1).add(new Edge(v2,cost));
			graph.get(v2).add(new Edge(v1,cost));
		}
		int answer = 0;
		pq.offer(new Edge(1,0));
		while(!pq.isEmpty()) {
			Edge temp = pq.poll();
			int now = temp.vex;
			int nowCost = temp.cost;
			if(check[now]==0) {
				check[now]=1;
				answer += nowCost;
				for(Edge edge : graph.get(now)){
					if(check[edge.vex]==0) pq.offer(edge);
				}
			}
		}
		System.out.println(answer);
	}	
}
```