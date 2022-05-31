# 송아지 찾기1(BFS)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비


풀이(몫과 나머지 활용)

```java
import java.util.Scanner;

public class Main {
	
	public static int solution(int s, int e) {
		int cnt = 0;
		int dis = e-s;
		if(dis<=0) return -dis;
		
		cnt+=dis/5;
		if(dis%5==4) cnt+=2;
		else cnt+=dis%5;
		
		return cnt;
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int s = sc.nextInt();
		int e = sc.nextInt();
		System.out.println(solution(s,e));
	}
}
```

풀이(BFS)

```java
import java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;

public class Main {
	
	public static int solution(int s, int e) {
		Queue<Integer> q = new LinkedList<>();
		int[] dis = {1,-1,5};
		int[] check = new int[10001];
		int L = 0;
		q.offer(s);
		check[s] = 1;
		while(!q.isEmpty()) {
			int leng = q.size();
			for(int i = 0 ; i<leng ; i++) {
				int n = q.poll();
				if(n==e) return L;
				for(int j = 0 ; j<3 ; j++) {
					int nx = n+dis[j];
					if(nx>=1 && nx<=10000 && check[nx]!=1) {
						q.offer(nx);
						check[nx]=1;
					}
				}
			} 
			L++;
		}
		return 0;
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int s = sc.nextInt();
		int e = sc.nextInt();
		System.out.println(solution(s,e));
	}
}
```