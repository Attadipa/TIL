# 미로탐색(DFS)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

상하좌우로 dfs 4번씩 돌리면 해결.

내 풀이

```java
import java.util.Scanner;

public class Main {
	
	static int cnt = 0;
	static int[][] arr = new int[9][9];
	static int[][] check = new int[9][9];

	public static void dfs(int m, int n) {
		if(arr[m][n]==1 || check[m][n]==1 || m==8 || n==8 || m==0 || n==0 ) return;
		if(m==7 && n==7) cnt++;
		else {
				check[m][n]=1;
				dfs(m+1,n);
				check[m][n]=0;
				check[m][n]=1;
				dfs(m-1,n);
				check[m][n]=0;
				check[m][n]=1;
				dfs(m,n+1);
				check[m][n]=0;
				check[m][n]=1;
				dfs(m,n-1);
				check[m][n]=0;
		}
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		for(int i = 1 ; i<8 ; i++) {
			for(int j = 1 ; j<8 ; j++) {
				arr[i][j]=sc.nextInt();
			}
		}
		dfs(1,1);
		System.out.println(cnt);
	}
} 
```

해설

```java
import java.util.Scanner;

public class Main {
	static int[] dx = {-1,0,1,0};
	static int[] dy = {0,-1,0,1};
	static int cnt = 0;
	static int[][] board;

	public static void dfs(int x, int y) {
		if(x==7 && y==7) cnt++;
		else {
			for(int i = 0 ; i<4 ; i++) {
				int nx = x+dx[i];
				int ny = y+dy[i];
				if(nx>=1 && nx<=7 && ny>=1 && ny<=7 && board[nx][ny]==0) {
					board[nx][ny]=1;
					dfs(nx,ny);
					board[nx][ny]=0;
				}
			}
		}
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		for(int i = 1 ; i<8 ; i++) {
			for(int j = 1 ; j<8 ; j++) {
				board[i][j]=sc.nextInt();
			}
		}
		board = new int[8][8];
		dfs(1,1);
		System.out.println(cnt);
	}
} 
```