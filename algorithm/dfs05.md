# 경로탐색(DFS, 인접리스트)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

    모든 경로의 가지 수 출력 문제
    그래프를 ArrayList를 사용하여 인접리스트로 표현
    이것을 DFS로 경로 수를 출력하는데
    노드의 개수가 많을 때 효율적

풀이

```java
import java.util.ArrayList;
import java.util.Scanner;

public class Main {
	static ArrayList<ArrayList<Integer>> graph;
	static int[] check;
	static int n, m, cnt;
	public static void dfs(int num) {
		if(num==n) cnt++;
		else {
			for(int node : graph.get(num)) {
				if(check[node]==0) {
					check[node]=1;
					dfs(node);
					check[node]=0;
				}
			}
		}
	}
	
	public static void main(String[] args) {
		Scanner sc  = new Scanner(System.in);
		n = sc.nextInt();
		m = sc.nextInt();
		check = new int[n+1];
		graph = new ArrayList<ArrayList<Integer>>();	
		for(int i =0 ; i<=n ; i++) {
			graph.add(new ArrayList<Integer>());
		}
		for(int i =0 ; i<m ; i++) {
			int a = sc.nextInt();
			int b = sc.nextInt();
			graph.get(a).add(b);
		}
		check[1]=1;
		dfs(1);
		System.out.println(cnt);
	}
}
```