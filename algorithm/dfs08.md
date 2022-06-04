# 최대점수 구하기(DFS)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

부분집합 문제와 거의 유사.

내 풀이

```java
import java.util.Scanner;

public class Main {

	static int n,m,max,qSum,tSum= 0;
	static int[] qArr, tArr;
	
	public static void dfs(int L, int qSum, int tSum) {
		if(tSum>m) return;
		if(L==n-1) max = Math.max(max, qSum);
		else {
			dfs(L+1,qSum+qArr[L+1],tSum+tArr[L+1]);
			dfs(L+1,qSum,tSum);
		}
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		n = sc.nextInt();
		m = sc.nextInt();
		qArr = new int[n];
		tArr = new int[n];
		for(int i = 0 ; i<n; i++) {
			qArr[i] = sc.nextInt();
			tArr[i] = sc.nextInt();
		}
		dfs(-1,0,0);
		System.out.println(max);
	}
}
```