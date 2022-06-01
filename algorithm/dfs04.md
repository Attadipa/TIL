# 경로탐색(DFS, 인접행렬)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

    모든 경로의 가지 수 출력 문제
    그래프를 2차원 배열을 활용하여 인접행렬로 표현하고
    이것을 DFS로 경로 수를 출력하는데
    요소의 개수 작을 땐 배열도 상관없지만 
    요소의 개수가 1만개, 10만개 있을 땐 비효율적.

풀이

```java
import java.util.Scanner;

public class Main {
	static int[][] arr;
	static int[] check;
	static int n, m, cnt;
	public static void dfs(int num) {
		if(num==n) cnt++;
		else {
			for(int i =1 ; i<=n ; i++) {
				if(arr[num][i]==1 && check[i]!=1) {
					check[i]=1;
					dfs(i);
					check[i]=0;
				}
			}
		}
	}
	
	public static void main(String[] args) {
		Scanner sc  = new Scanner(System.in);
		n = sc.nextInt();
		m = sc.nextInt();
		arr = new int[n+1][m+1];
		check = new int[n+1];
		for(int i =1 ; i<=m ; i++) {
			int a = sc.nextInt();
			int b = sc.nextInt();
			arr[a][b] = 1;
		}
		check[1]=1;
		dfs(1);
		System.out.println(cnt);
	}
}
```