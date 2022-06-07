# 수열추측하기

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

수열과 조합수의 복합문제

해설

```java
import java.util.Scanner;

public class Main {
	
	static int n,f,sum;
	static int[] com, arr, check1;
	static int[][] check2;
	static boolean isEnd = false;
	
	public static int combi(int n, int r) {
		if(check2[n][r]!=0) return check2[n][r];
		if(n==r || r==0) return 1;
		else {
			check2[n][r] = combi(n-1,r-1)+combi(n-1,r);
			return check2[n][r]; 
		}
	}
	
	public static void dfs(int lev, int sum) {
		if(isEnd) return;
		if(sum>f) return;
		if(lev==n) {
			if(sum==f) {
				for(int i :  arr) System.out.print(i+" ");
				isEnd=true;
			} else return;
		}
		else {
			for(int i = 1 ; i<=n ; i++ ) {
				if(check1[i]==0) {
					check1[i]=1;
					arr[lev] = i;
					dfs(lev+1,sum+(arr[lev]*com[lev]));
					check1[i]=0;
				}
			} 
		}
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		n = sc.nextInt();
		f = sc.nextInt();
		com = new int[n];
		arr = new int[n];
		check1 = new int[n+1];
		check2 = new int[n][n];
		for(int i = 0 ; i <n ; i++) {
			com[i] = combi(n-1,i);
		}
		dfs(0,0);
		
	}
}
```