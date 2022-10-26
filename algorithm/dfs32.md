# 연구소3

### 백준 17142번

-------

### 문제

	인체에 치명적인 바이러스를 연구하던 연구소에 승원이가 침입했고, 바이러스를 유출하려고 한다. 
	승원이는 연구소의 특정 위치에 바이러스 M개를 놓을 것이고, 승원이의 신호와 동시에 바이러스는 퍼지게 된다.

	연구소는 크기가 N×N인 정사각형으로 나타낼 수 있으며, 정사각형은 1×1 크기의 정사각형으로 나누어져 있다. 
	연구소는 빈 칸, 벽으로 이루어져 있으며, 벽은 칸 하나를 가득 차지한다.

	일부 빈 칸은 바이러스를 놓을 수 있는 칸이다. 바이러스는 상하좌우로 인접한 모든 빈 칸으로 동시에 복제되며, 
	1초가 걸린다.

	예를 들어, 아래와 같이 연구소가 생긴 경우를 살펴보자. 0은 빈 칸, 1은 벽, 2는 바이러스를 놓을 수 있는 칸이다.

	2 0 0 0 1 1 0
	0 0 1 0 1 2 0
	0 1 1 0 1 0 0
	0 1 0 0 0 0 0
	0 0 0 2 0 1 1
	0 1 0 0 0 0 0
	2 1 0 0 0 0 2
	M = 3이고, 바이러스를 아래와 같이 놓은 경우 6초면 모든 칸에 바이러스를 퍼뜨릴 수 있다. 
	벽은 -, 바이러스를 놓은 위치는 0, 빈 칸은 바이러스가 퍼지는 시간으로 표시했다.

	6 6 5 4 - - 2
	5 6 - 3 - 0 1
	4 - - 2 - 1 2
	3 - 2 1 2 2 3
	2 2 1 0 1 - -
	1 - 2 1 2 3 4
	0 - 3 2 3 4 5
	시간이 최소가 되는 방법은 아래와 같고, 5초만에 모든 칸에 바이러스를 퍼뜨릴 수 있다.

	0 1 2 3 - - 2
	1 2 - 3 - 0 1
	2 - - 2 - 1 2
	3 - 2 1 2 2 3
	3 2 1 0 1 - -
	4 - 2 1 2 3 4
	5 - 3 2 3 4 5
	연구소의 상태가 주어졌을 때, 모든 빈 칸에 바이러스를 퍼뜨리는 최소 시간을 구해보자.

### 입력

	첫째 줄에 연구소의 크기 N(5 ≤ N ≤ 50), 놓을 수 있는 바이러스의 개수 M(1 ≤ M ≤ 10)이 주어진다.

	둘째 줄부터 N개의 줄에 연구소의 상태가 주어진다. 0은 빈 칸, 1은 벽, 2는 바이러스를 놓을 수 있는 칸이다.
	2의 개수는 M보다 크거나 같고, 10보다 작거나 같은 자연수이다.

### 출력

	연구소의 모든 빈 칸에 바이러스가 있게 되는 최소 시간을 출력한다. 
	바이러스를 어떻게 놓아도 모든 빈 칸에 바이러스를 퍼뜨릴 수 없는 경우에는 -1을 출력한다.

### 예제 입력 1 

	7 3
	2 0 0 0 1 1 0
	0 0 1 0 1 2 0
	0 1 1 0 1 0 0
	0 1 0 0 0 0 0
	0 0 0 2 0 1 1
	0 1 0 0 0 0 0
	2 1 0 0 0 0 2

### 예제 출력 1 

	5

### 예제 입력 2 

	7 3

	2 0 2 0 1 1 0
	0 0 1 0 1 2 0
	0 1 1 2 1 0 0
	2 1 0 0 0 0 2
	0 0 0 2 0 1 1
	0 1 0 0 0 0 0
	2 1 0 0 2 0 2

### 예제 출력 2 

	5

### 예제 입력 3 

	7 4
	2 0 2 0 1 1 0
	0 0 1 0 1 2 0
	0 1 1 2 1 0 0
	2 1 0 0 0 0 2
	0 0 0 2 0 1 1
	0 1 0 0 0 0 0
	2 1 0 0 2 0 2

### 예제 출력 3 

	4

### 예제 입력 4 

	7 2
	2 0 2 0 1 1 0
	0 0 1 0 1 0 0
	0 1 1 1 1 0 0
	2 1 0 0 0 0 2
	1 0 0 0 0 1 1
	0 1 0 0 0 0 0
	2 1 0 0 2 0 2

### 예제 출력 4 

	-1



### 내 풀이 (2차원배열의 얕은복사, 깊은복사 주의할것)

```java

import java.util.ArrayList;
import java.util.Arrays;
import java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;

class Node{
	int x;
	int y;
	public Node() {
		
	}
	public Node(int x, int y) {
		this.x = x;
		this.y = y;
	}
	@Override
	public String toString() {
		return "Node [x=" + x + ", y=" + y + "]";
	}
	
}

public class Main {
	static int n,m;
	static int min = Integer.MAX_VALUE;
	static int[] dx = {1,-1,0,0};
	static int[] dy = {0,0,1,-1};
	static ArrayList<Node> list = new ArrayList<>();
	static ArrayList<Node> temp = new ArrayList<>();
	static int[][] graph;
	static int[][] copy;

	public static boolean check() {
		boolean flag = true;
		for (int i = 0; i < n; i++) {
			for (int j = 0; j < n; j++) {
				if(copy[i][j]==0) flag = false;
			}
		}
		return flag;
	}
	public static void bfs() {
		for (int i = 0; i < n; i++) {
			for (int j = 0; j < n; j++) {
				if(graph[i][j]==1) copy[i][j] = 1;
				else copy[i][j] = 0;
			}
		}
		Queue<Node> q = new LinkedList<>();
		for(Node node : temp) {
			q.offer(node);
			copy[node.x][node.y] = 2;
		}
		int lev=0;
		while(!q.isEmpty()) {
			int size = q.size();
			for(int i = 0 ; i<size ; i++) {
				Node now = q.poll(); 
				for(int j = 0 ; j< 4 ; j++) {
					int nx = now.x+dx[j];
					int ny = now.y+dy[j];
					if(nx>=0 && nx<n && ny>=0 && ny<n && copy[nx][ny]==0) {
						copy[nx][ny] = 2;
						q.offer(new Node(nx,ny));
					}
				}
			}
			lev++;
			
		}
		if(check()) min = Math.min(lev-1, min);
	}
	public static void dfs(int lev, int start) {
		if(lev>=m) bfs();
		else {
			for(int i = start ; i<list.size() ; i++) {
				temp.add(list.get(i));
				dfs(lev+1,i+1);
				temp.remove(list.get(i));
			}
		}
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		n = sc.nextInt();
		m = sc.nextInt();
		graph = new int[n][n];
		copy = new int[n][n];

		for (int i = 0; i < n; i++) {
			for (int j = 0; j < n; j++) {
				graph[i][j] = sc.nextInt();
				if(graph[i][j]==2) list.add(new Node(i,j));
			}
		}
		dfs(0,0);
		if(min==Integer.MAX_VALUE) System.out.println(-1);
		else System.out.println(min);
		
	}

}


```