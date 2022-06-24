# 원더랜드(최소스패닝트리 : 크루스칼)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

해설

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.Scanner;

class Edge implements Comparable<Edge>{
	int v1;
	int v2;
	int cost;
	
	public Edge(int v1, int v2, int cost) {
		super();
		this.v1 = v1;
		this.v2 = v2;
		this.cost = cost;
	}

	@Override
	public int compareTo(Edge e) {
		return this.cost - e.cost;
	}
}

public class Main {
	static ArrayList<Edge> list = new ArrayList<>();
	static int[] unf;
	static int answer,cnt = 0;
	public static int find(int v) {
		if(v==unf[v]) return v;
		else {
			return unf[v] = find(unf[v]);
		}
	} 
	public static void union(int a, int b, int cost) {
		int fa = find(a);
		int fb = find(b);
		if(fa!=fb) {
			unf[fa] = fb;
			answer+=cost;
			cnt++;
		}
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int v = sc.nextInt();
		int e = sc.nextInt();
		unf = new int[v+1];
		for(int i = 0 ; i<=v ; i++) unf[i] = i;
		for(int i = 0 ; i<e ; i++) {
			int n1 = sc.nextInt();
			int n2 = sc.nextInt();
			int cost = sc.nextInt();
			list.add(new Edge(n1,n2,cost));
		}
		Collections.sort(list);
		for(Edge edge : list) {
			union(edge.v1, edge.v2, edge.cost);
			if(cnt==v-1) break;
		}
		System.out.println(answer);
	}
}
```