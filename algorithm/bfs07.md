# 섬나라아일랜드(BFS)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

섬 갯수 출력.

내 풀이

```java
import java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;


class Node{
	int x;
	int y;
	Node(int x, int y){
		this.x = x;
		this.y = y;
	}
}

public class Main {
	static int n =0;
	static int[] dx = {1,-1,0,0,1,1,-1,-1};
	static int[] dy = {0,0,1,-1,1,-1,1,-1};
	static int[][] arr;

	public static void bfs(int x, int y) {
		Queue<Node> q = new LinkedList<Node>();
		q.offer(new Node(x,y));
		arr[x][y]=0;
		while(!q.isEmpty()) {
			int leng = q.size();
			for(int i = 0 ; i<leng ; i++) {
				Node node = q.poll();
				for(int j = 0 ; j<8 ; j++) {
					int nx = node.x+dx[j];
					int ny = node.y+dy[j];
					if(nx>=1 && nx<=n && ny>=1 && ny<=n && arr[nx][ny]==1) {
						arr[nx][ny]=0;
						q.offer(new Node(nx,ny));
					}
				}
			}
		}

	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		n = sc.nextInt();
		arr = new int[n+1][n+1];
		for(int i = 1 ; i<=n ; i++) {
			for(int j = 1 ; j<=n ; j++) {
				arr[i][j]=sc.nextInt();
			}
		}
		int cnt=0;
		for(int i = 1 ; i<=n ; i++) {
			for(int j = 1 ; j<=n ; j++) {
				if(arr[i][j]==1) {
					cnt++;
					bfs(i,j);
				}
			}
		}
		System.out.println(cnt);
	}
} 
```