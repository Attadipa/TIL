# 친구인가? (Disjoint-Set : Union&Find)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

내 풀이(bfs활용)

```java
import java.util.ArrayList;
import java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;

public class Main {
	public static String solution(int student, int friend, ArrayList<ArrayList<Integer>> graph) { 
		String answer ="NO";
		Queue<Integer> q = new LinkedList<>();
		for(int frn : graph.get(student)) {
			q.add(frn);
		}
		while(!q.isEmpty()) {
			int leng = q.size();
			for(int i = 0 ; i<leng ; i++) {
				int stu = q.poll();
				if(stu==friend) return "YES";
				for(int frn : graph.get(stu)) {
					if(!q.contains(frn)) q.offer(frn);
				}
			}
		}
		return answer;

	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int m = sc.nextInt();
		
		ArrayList<ArrayList<Integer>> graph = new ArrayList<>();
		for(int i = 0 ; i<=n ; i++) {
			graph.add(new ArrayList<Integer>());
		}
		for(int i = 0 ; i<m ; i++) {
			int student = sc. nextInt();
			int friend = sc. nextInt();
			graph.get(student).add(friend);
			graph.get(friend).add(student);
		}
		int student = sc. nextInt();
		int friend = sc. nextInt();
		System.out.println(solution(student, friend, graph));
	}
}
```

해설

```java
import java.util.Scanner;

public class Main {
	static int[] unf;
	public static int find(int v) {
		if(v==unf[v]) return v;
		else return unf[v] = find(unf[v]);
	}
	public static void union(int a, int b) {
		int fa = find(a);
		int fb = find(b);
		if(fa!=fb) unf[fa] = fb;
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int m = sc.nextInt();
		unf = new int[n+1];
		for(int i = 0 ; i<=n ; i++) unf[i] = i;
		for(int i = 0 ; i<m ; i++) {
			int a = sc.nextInt();
			int b = sc.nextInt();
			union(a,b);
		}
		int a = sc.nextInt();
		int b = sc.nextInt();
		int fa = find(a);
		int fb = find(b);
		if(fa!=fb) System.out.println("NO");
		else System.out.println("YES");
	}
}
```