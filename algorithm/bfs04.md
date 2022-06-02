# 그래프 최단거리(BFS)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

#### 1번 정점에서 각 정점으로 가는 최소 이동 간선수를 출력하는 문제


내 풀이(check배열에 level도 함께 입력)


```java
import java.util.ArrayList;
import java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;

public class Main {

	static ArrayList<ArrayList<Integer>> graph;
	static int[] check, dis;
	
	public static void bfs(int n) {
		Queue<Integer> q = new LinkedList<>();
		int level = 1; 
		q.offer(n);
		check[n] = -1;
		while(!q.isEmpty()) {
			for(int i = 0 ; i<q.size(); i++) {
				int cv = q.poll();
					for(int nv : graph.get(cv)) {
						if(check[nv]==0) {
							check[nv]=level;
							q.offer(nv);
						}
					} 
				}
			level++;
		}
		for(int i =2; i<check.length ; i++) {
			System.out.println(i+" : "+check[i]);
		}
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int m = sc.nextInt();
		check = new int[n+1];
		graph = new ArrayList<ArrayList<Integer>>();
		for(int i = 0 ; i<=n ; i++) {
			graph.add(new ArrayList<Integer>());
		}
		for(int i= 0 ; i<m ; i++) {
			int a = sc.nextInt();
			int b = sc.nextInt();
			graph.get(a).add(b);
		}
		bfs(1);
	}
}
```

풀이 (거리측정용 배열 별도이용)

```java
import java.util.ArrayList;
import java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;

public class Main {

	static ArrayList<ArrayList<Integer>> graph;
	static int[] check, dis;
	
	public static void bfs(int n) {
		Queue<Integer> q = new LinkedList<>();
		q.offer(n);
		check[n] = -1;
		dis[n] = 0;
		while(!q.isEmpty()) {
			for(int i = 0 ; i<q.size(); i++) {
				int cv = q.poll();
					for(int nv : graph.get(cv)) {
						if(check[nv]==0) {
							check[nv]=1;
							q.offer(nv);
							dis[nv] = dis[cv]+1;
						}
					} 
			}
		}
		for(int i =2; i<check.length ; i++) {
			System.out.println(i+" : "+dis[i]);
		}
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int m = sc.nextInt();
		check = new int[n+1];
		dis = new int[n+1];
		graph = new ArrayList<ArrayList<Integer>>();
		for(int i = 0 ; i<=n ; i++) {
			graph.add(new ArrayList<Integer>());
		}
		for(int i= 0 ; i<m ; i++) {
			int a = sc.nextInt();
			int b = sc.nextInt();
			graph.get(a).add(b);
		}
		bfs(1);
		
	}
}
```
