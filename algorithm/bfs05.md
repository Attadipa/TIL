# 미로의 최단거리 통로 (BFS)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

최단거리 출력문제. 도착불가시 -1 출력.

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
	static int[] dx = {-1,0,1,0};
	static int[] dy = {0,-1,0,1};
	static int[][] board;

	public static int bfs(int n) {
		Queue<Node> q = new LinkedList<Node>();
		int level = n;
		board[1][1]=1;
		q.offer(new Node(1,1));
		while(!q.isEmpty()) {
			int leng = q.size();
			for(int i = 0 ; i<leng ; i++) {
				Node node = q.poll();
				if(node.x==7 && node.y==7) {
					return level;
				}
				for(int j = 0 ; j < 4 ; j++) {
					int nx = node.x + dx[j];
					int ny = node.y + dy[j];
					if(nx>=1 && nx<=7 && ny>=1 && ny<=7 && board[nx][ny]==0) {
						board[nx][ny]=1;
						q.offer(new Node(nx, ny));
					}
				}
			}
			level++;
		}
		return -1;
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		board = new int[8][8];
		for(int i = 1 ; i<8 ; i++) {
			for(int j = 1 ; j<8 ; j++) {
				board[i][j]=sc.nextInt();
			}
		}
		System.out.println(bfs(0));
	}
} 
```

해설(거리 2차원 배열 이용)

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
	static int[] dx = {-1,0,1,0};
	static int[] dy = {0,-1,0,1};
	static int[][] board, dis;

	public static void bfs(int x, int y) {
		Queue<Node> q = new LinkedList<Node>();
		board[x][y]=1;
		q.offer(new Node(x,y));
		while(!q.isEmpty()) {
			int leng = q.size();
			for(int i = 0 ; i<leng ; i++) {
				Node node = q.poll();
				for(int j = 0 ; j < 4 ; j++) {
					int nx = node.x + dx[j];
					int ny = node.y + dy[j];
					if(nx>=1 && nx<=7 && ny>=1 && ny<=7 && board[nx][ny]==0) {
						board[nx][ny]=1;
						q.offer(new Node(nx, ny));
						dis[nx][ny] = dis[node.x][node.y]+1;
					}
				}
			}
		}
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		board = new int[8][8];
		dis = new int[8][8];
		for(int i = 1 ; i<8 ; i++) {
			for(int j = 1 ; j<8 ; j++) {
				board[i][j]=sc.nextInt();
			}
		}
		bfs(1,1);
		if(board[7][7]==0) System.out.println(-1);
		else System.out.println(dis[7][7]);
	}
} 
```