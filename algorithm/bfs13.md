# 미로 탈출

### 백준 14923번 문제

------------

### 문제

    홍익이는 사악한 마법사의 꾐에 속아 N x M 미로 (Hx, Hy) 위치에 떨어졌다. 
    다행히도 홍익이는 마법사가 만든 미로의 탈출 위치(Ex, Ey)를 알고 있다. 
    하지만 미로에는 곳곳에 마법사가 설치한 벽이 있어 홍익이가 탈출하기 어렵게 하고 있다.

    홍익이는 마법사의 연구실에서 훔친 지팡이가 있어, 벽을 길로 만들 수 있다. 
    그렇지만, 안타깝게도 마법의 지팡이는 단 한 번만 사용할 수 있다.

    이때, 홍익이를 도와 미로에서 탈출할 수 있는지 알아보고, 할 수 있다면 가장 빠른 경로의 거리 D는 얼마인지 알아보자.

    인접한 칸으로 이동하는데 똑같은 시간이 들고, 벽을 부수는 데 시간이 걸리지 않는다.

### 입력

    N M
    Hx Hy
    Ex Ey
    N X M 행렬
    2 ≤ N ≤ 1000, 2 ≤ M ≤ 1000
    1 ≤ Hx, Hy, Ex, Ey ≤ 1000
    (Hx, Hy)≠ (Ex, Ey)
    행렬은 0과 1로만 이루어져 있고, 0이 빈 칸, 1이 벽이다.

 ### 출력

    D (탈출 할 수 없다면, -1을 출력한다.)

### 예제 입력 1 

    5 6
    1 1
    5 6
    0 1 1 1 0 0
    0 1 1 0 0 0
    0 1 0 0 1 0
    0 1 0 0 1 0
    0 0 0 1 1 0

### 예제 출력 1 

    11

### 내 풀이(3차원 체크배열 사용)

```java

import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.ArrayList;
import java.util.LinkedList;
import java.util.Queue;
import java.util.StringTokenizer;

class Node{
	int x;
	int y;
	int lev;
	int cnt;
	public Node() {
	}
	public Node(int x, int y, int lev, int cnt) {
		this.x = x;
		this.y = y;
		this.lev = lev;
		this.cnt = cnt;
	}
}

public class Main{
	
	public static int n,m,hx,hy,ex,ey;
	public static int min = Integer.MAX_VALUE;
	public static int[] dx = {1,-1,0,0};
	public static int[] dy = {0,0,1,-1};
	
	public static int[][] graph;
	public static int[][][] check;
	public static ArrayList<Node> walls = new ArrayList<>();

	
	public static void move() {
		Queue<Node> q = new LinkedList<>();
		check = new int[n+1][m+1][2];
		
		q.add(new Node(hx,hy,0,1));
		check[hx][hy][1] = 1;
		
		while(!q.isEmpty()) {
			int size = (q.size());
			for(int i = 0 ; i<size ; i++) {
				Node now = q.poll();
				for(int j = 0 ; j<4 ; j++) {
					int nx = now.x+dx[j];
					int ny = now.y+dy[j];
					if(nx==ex && ny==ey) {
						min = Math.min(min,now.lev+1);
					}
					if(nx>=1 && nx<=n && ny>=1 && ny<=m 
							 && check[nx][ny][now.cnt]==0 && graph[nx][ny]==0) {
						check[nx][ny][now.cnt]=1;
						q.add(new Node(nx,ny,now.lev+1,now.cnt));
					}
					if(nx>=1 && nx<=n && ny>=1 && ny<=m && now.cnt>0
							 && check[nx][ny][now.cnt-1]==0 && graph[nx][ny]==1) {
						check[nx][ny][now.cnt-1]=1;
						q.add(new Node(nx,ny,now.lev+1,now.cnt-1));
					}
				}
			}
		}
	}
	
	public static void main(String[] args) throws Exception{
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st;
		st = new StringTokenizer(br.readLine());
		n = Integer.parseInt(st.nextToken());
		m = Integer.parseInt(st.nextToken());
		st = new StringTokenizer(br.readLine());
		hx = Integer.parseInt(st.nextToken());
		hy = Integer.parseInt(st.nextToken());
		st = new StringTokenizer(br.readLine());
		ex = Integer.parseInt(st.nextToken());
		ey = Integer.parseInt(st.nextToken());
		
		graph = new int[n+1][m+1];
		
		for(int i = 1 ; i<=n ; i++) {
			st = new StringTokenizer(br.readLine());
			for(int j = 1 ; j<=m ; j++) {
				graph[i][j] = Integer.parseInt(st.nextToken());
				if(graph[i][j]==1) {
					walls.add(new Node(i,j,0,1));
				}
			}
		}
		move();
		
		System.out.println(min==Integer.MAX_VALUE ? -1 : min);
		
		
		
	}
}

```