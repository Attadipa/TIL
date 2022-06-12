# 섬나라아일랜드(DFS)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

섬 갯수 출력.

내 풀이

```java
import java.util.Scanner;


public class Main {
	static int n =0;
	static int[] dx = {1,-1,0,0,1,1,-1,-1};
	static int[] dy = {0,0,1,-1,1,-1,1,-1};
	static int[][] arr;

	public static void dfs(int x, int y) {
		for(int i = 0 ; i<8 ; i++) {
			int nx = x+dx[i];
			int ny = y+dy[i];
			if(nx>=1 && nx<=n && ny>=1 && ny<=n && arr[nx][ny]==1) {
				arr[nx][ny]=0;
				dfs(nx,ny);
			}
		}

	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		n = sc.nextInt();
		arr = new int[n+1][n+1];
		for(int i = 1 ; i<=n ; i++) {
			for(int j = 1; j<=n ;j++) {
				arr[i][j]=sc.nextInt();
			}
		}
		int cnt = 0;
		for(int i = 1 ; i<=n ; i++) {
			for(int j = 1; j<=n ;j++) {
				if(arr[i][j]==1) {
					cnt++;
					dfs(i,j);
				}
			}
		}
		System.out.println(cnt);
	}
} 
```

해설

```java
import java.util.Scanner;


public class Main {
	static int n =0;
	static int[] dx = {1,-1,0,0,1,1,-1,-1};
	static int[] dy = {0,0,1,-1,1,-1,1,-1};
	static int[][] arr;

	public static void dfs(int x, int y) {
		for(int i = 0 ; i<8 ; i++) {
			int nx = x+dx[i];
			int ny = y+dy[i];
			if(nx>=1 && nx<=n && ny>=1 && ny<=n && arr[nx][ny]==1) {
				arr[nx][ny]=0;
				dfs(nx,ny);
			}
		}

	}
	public static int solution(int[][] arr) {
		int cnt = 0;
		for(int i = 1 ; i<=n ; i++) {
			for(int j = 1; j<=n ;j++) {
				if(arr[i][j]==1) {
					cnt++;
					dfs(i,j);
				}
			}
		}
		return cnt;
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		n = sc.nextInt();
		arr = new int[n+1][n+1];	
		for(int i = 1 ; i<=n ; i++) {
			for(int j = 1; j<=n ;j++) {
				arr[i][j]=sc.nextInt();
			}
		}
		System.out.println(solution(arr));
		
	}
} 
```