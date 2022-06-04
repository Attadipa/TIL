# 바둑이 승차(DFS)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

부분집합 문제와 거의 유사.

내 풀이

```java
import java.util.Scanner;

public class Main {

	static int c,n,max= 0;
	static int[] arr;
	
	public static void dfs(int L, int sum) {
		if(sum>c) return;
		if(L==n-1) max = Math.max(max, sum);
		else {
			dfs(L+1,sum+arr[L+1]);
			dfs(L+1,sum);
		}
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		c = sc.nextInt();
		n = sc.nextInt();
		arr = new int[n];
		for(int i = 0 ; i<n; i++) {
			arr[i] = sc.nextInt();
		}
		dfs(-1,0);
		System.out.println(max);
	}
}
```