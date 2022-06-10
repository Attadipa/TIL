# 토마토(BFS활용)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

최소날짜 출력문제. 안 익은 토마토 존재하면 -1출력.
미로문제와 거의 유사.

내 풀이(level활용)

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
	static int m,n =0;
	static int[] dx = {1,-1,0,0};
	static int[] dy = {0,0,1,-1};
	static int[][] arr;

	public static int bfs() {
		Queue<Node> q = new LinkedList<Node>();
		for(int i = 0 ; i<n ; i++) {
			for(int j = 0; j<m ; j++) {
				if(arr[i][j]==1) q.offer(new Node(i,j));
			}
		}
		int level = -1;
		while(!q.isEmpty()) {
			level++;
			int leng = q.size();
			for(int i = 0 ; i<leng ; i++) {
				Node node = q.poll();
				for(int j = 0; j<4 ; j++) {
					int nx = node.x+dx[j];
					int ny = node.y+dy[j];
					if(nx>=0 && nx<=n-1 && ny>=0 && ny<=m-1 && arr[nx][ny]==0) {
						arr[nx][ny]=1;
						q.offer(new Node(nx,ny));
					}
				}
			}
		}
		for(int i = 0 ; i<n ; i++) {
			for(int j = 0; j<m ; j++) {
				if(arr[i][j]==0) return -1;
			}
		}
		return level;
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		m = sc.nextInt();
		n = sc.nextInt();
		arr = new int[n][m];
		for(int i = 0 ; i<n ; i++) {
			for(int j = 0 ; j<m ; j++) {
				arr[i][j]=sc.nextInt();
			}
		}
		System.out.println(bfs());
	}
} 
```

해설(거리측정용 배열 활용)

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
	static int m,n =0;
	static int[] dx = {1,-1,0,0};
	static int[] dy = {0,0,1,-1};
	static int[][] arr, dis;

	public static int bfs() {
		Queue<Node> q = new LinkedList<Node>();
		for(int i = 0 ; i<n ; i++) {
			for(int j = 0; j<m ; j++) {
				if(arr[i][j]==1) q.offer(new Node(i,j));
			}
		}
		while(!q.isEmpty()) {
			int leng = q.size();
			for(int i = 0 ; i<leng ; i++) {
				Node node = q.poll();
				for(int j = 0; j<4 ; j++) {
					int nx = node.x+dx[j];
					int ny = node.y+dy[j];
					if(nx>=0 && nx<=n-1 && ny>=0 && ny<=m-1 && arr[nx][ny]==0) {
						arr[nx][ny]=1;
						q.offer(new Node(nx,ny));
						dis[nx][ny]=dis[node.x][node.y]+1;
					}
				}
			}
		}
		int answer=0;
		for(int i = 0 ; i<n ; i++) {
			for(int j = 0; j<m ; j++) {
				if(arr[i][j]==0) return -1;
				if(dis[i][j]>answer) answer=dis[i][j];
			}
		}
		return answer;
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		m = sc.nextInt();
		n = sc.nextInt();
		arr = new int[n][m];
		dis = new int[n][m];
		for(int i = 0 ; i<n ; i++) {
			for(int j = 0 ; j<m ; j++) {
				arr[i][j]=sc.nextInt();
			}
		}
		System.out.println(bfs());
	}
} 
```