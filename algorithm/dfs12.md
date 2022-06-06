# 조합수(메모이제이션)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

메모이제이션의 유무는 속도면에서 극명한 차이를 가져온다.

풀이

```java
import java.util.Scanner;

public class Main {

	static int n,r=0
	static int[][] check;
	
	public static int dfs(int n, int r) {
		if(r==0 || n==r) return 1;
		else {
			if(check[n][r]==0) {
				check[n][r]=dfs(n-1,r-1) + dfs(n-1,r);
			} return check[n][r];
		}
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		n = sc.nextInt();
		r = sc.nextInt();
		check = new int[n+1][r+1];
		System.out.println(dfs(n,r));
	}
}
```