# 다익스트라 알고리즘

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

해설

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.PriorityQueue;
import java.util.Scanner;

class Edge implements Comparable<Edge>{
	int vex;
	int cost;
	public Edge(int vex, int cost) {
		this.vex = vex;
		this.cost = cost;
	}
	@Override
	public int compareTo(Edge o) {
		return this.cost-o.cost;
	}
	
}

public class Main {
	static ArrayList<ArrayList<Edge>> graph = new ArrayList<>();
	static int[] dis;
	public static void solution(int v) {
		PriorityQueue<Edge> pq = new PriorityQueue<>();
		pq.offer(new Edge(v,0));
		dis[v] = 0;
		while(!pq.isEmpty()) {
			Edge tmp = pq.poll();
			int now = tmp.vex;
			int nowCost = tmp.cost;
			if(nowCost>dis[now]) continue;
			for(Edge e : graph.get(now)) {
				
				if(dis[e.vex] > nowCost + e.cost) {
					dis[e.vex] = nowCost + e.cost;
					pq.offer(new Edge(e.vex,nowCost+e.cost));
				}
			}
		}
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int m = sc.nextInt();
		dis = new int[n+1];
		Arrays.fill(dis, Integer.MAX_VALUE);
		for(int i = 0 ; i<=n ; i++) {
			graph.add(new ArrayList<Edge>());
		}
		for(int i = 0 ; i<m ; i++) {
			int start = sc.nextInt();
			int end = sc.nextInt();
			int cost = sc.nextInt();
			graph.get(start).add(new Edge(end,cost));
		}
		solution(1);
		for(int i = 2 ; i<=n ; i++) {
			if(dis[i]==Integer.MAX_VALUE) System.out.println(i +" : impossible");
			else System.out.println(i + " : " + dis[i]);
		}
	}
}
```