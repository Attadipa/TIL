# 로봇  

### 백준 1726번 문제

------------

### 문제

    많은 공장에서 로봇이 이용되고 있다. 우리 월드 공장의 로봇은 바라보는 방향으로 궤도를 따라 움직이며, 움직이는 방향은 동, 서, 남, 북 가운데 하나이다. 로봇의 이동을 제어하는 명령어는 다음과 같이 두 가지이다.

    명령 1. Go k: k는 1, 2 또는 3일 수 있다. 현재 향하고 있는 방향으로 k칸 만큼 움직인다.
    명령 2. Turn dir: dir은 left 또는 right 이며, 각각 왼쪽 또는 오른쪽으로 90° 회전한다.
    공장 내 궤도가 설치되어 있는 상태가 아래와 같이 0과 1로 이루어진 직사각형 모양으로 로봇에게 입력된다. 0은 궤도가 깔려 있어 로봇이 갈 수 있는 지점이고, 1은 궤도가 없어 로봇이 갈 수 없는 지점이다. 로봇이 (4, 2) 지점에서 남쪽을 향하고 있을 때,  이 로봇을 (2, 4) 지점에서 동쪽으로 향하도록 이동시키는 것은 아래와 같이 9번의 명령으로 가능하다.

<img src="https://upload.acmicpc.net/6d410e6d-cced-4f83-b9b8-75404e77b2b9/-/preview/"></img><br/>

    로봇의 현재 위치와 바라보는 방향이 주어졌을 때, 로봇을 원하는 위치로 이동시키고, 원하는 방향으로 바라보도록 하는데 최소 몇 번의 명령이 필요한지 구하는 프로그램을 작성하시오.

    ### 입력

    첫째 줄에 공장 내 궤도 설치 상태를 나타내는 직사각형의 세로 길이 M과 가로 길이 N이 빈칸을 사이에 두고 주어진다. 이때 M과 N은 둘 다 100이하의 자연수이다. 이어 M줄에 걸쳐 한 줄에 N개씩 각 지점의 궤도 설치 상태를 나타내는 숫자 0 또는 1이 빈칸을 사이에 두고 주어진다. 다음 줄에는 로봇의 출발 지점의 위치 (행과 열의 번호)와 바라보는 방향이 빈칸을 사이에 두고 주어진다. 마지막 줄에는 로봇의 도착 지점의 위치 (행과 열의 번호)와 바라보는 방향이 빈칸을 사이에 두고 주어진다. 방향은 동쪽이 1, 서쪽이 2, 남쪽이 3, 북쪽이 4로 주어진다. 출발지점에서 도착지점까지는 항상 이동이 가능하다.

### 출력

    첫째 줄에 로봇을 도착 지점에 원하는 방향으로 이동시키는데 필요한 최소 명령 횟수를 출력한다.

### 예제 입력 1 

    5 6
    0 0 0 0 0 0
    0 1 1 0 1 0
    0 1 0 0 0 0
    0 0 1 1 1 0
    1 0 0 0 0 0
    4 2 3
    2 4 1

### 예제 출력 1 

    9

### 내 풀이(continue할지 break할지 경우의 수를 잘 고려해야 함)

```java
package algo;

import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.LinkedList;
import java.util.Queue;
import java.util.StringTokenizer;

class Node{
	int x;
	int y;
	int lev;
	int dir;
	
	public Node() {
	}

	public Node(int x, int y, int lev, int dir) {
		this.x = x;
		this.y = y;
		this.lev = lev;
		this.dir = dir;
	}

	@Override
	public String toString() {
		return x +""+y + "" + lev + "" + dir ;
	}

}
public class Main{
	
	public static int m,n,sx,sy,sdir,ex,ey,edir;
	public static int answer;
	public static int[][] graph;
	public static int[][][] check;
	
	public static int[] dx = {0,0,0,1,-1};
	public static int[] dy = {0,1,-1,0,0};
	
	public static void bfs(){
		Queue<Node> q = new LinkedList<>();
		q.offer(new Node(sx,sy,0,sdir));
		check[sx][sy][sdir] = 1;
		
		while(!q.isEmpty()) {
			int size = q.size();
			for(int i = 0 ; i<size ; i++) {
				Node now = q.poll();
				if(now.x==ex && now.y==ey && now.dir==edir) {
					answer = now.lev;
					return;
				}
				for(int d = 1 ; d<=4 ; d++) {
					if(now.dir==d) {
						for(int go = 1 ; go<=3 ; go++) {
							int nx = now.x +dx[d]*go;
							int ny = now.y +dy[d]*go;
							
							if(nx<1 || nx>m || ny<1 || ny>n) continue;
							if(graph[nx][ny]==1) break;
							if(check[nx][ny][d]==1) continue;
							
							check[nx][ny][d] = 1;
							q.offer(new Node(nx,ny,now.lev+1,d));
						}	
					}else {
						if(now.dir%2==1 && now.dir+1 == d) continue;
						if(now.dir%2==0 && now.dir-1 == d) continue;
						if(check[now.x][now.y][d]==0) {
							check[now.x][now.y][d]=1;
							q.offer(new Node(now.x,now.y,now.lev+1,d));
						}
					}
					
				}
			}
		}
	}
	public static void main(String[] args) throws Exception{
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		m = Integer.parseInt(st.nextToken());
		n = Integer.parseInt(st.nextToken());
		
		graph = new int[m+1][n+1];
		check = new int[m+1][n+1][5];
		
		for(int i = 1 ; i<=m ; i++) {
			st = new StringTokenizer(br.readLine());
			for(int j = 1 ; j<=n ; j++) {
				graph[i][j] = Integer.parseInt(st.nextToken());
			}
		}

		st = new StringTokenizer(br.readLine());
		sx = Integer.parseInt(st.nextToken());
		sy = Integer.parseInt(st.nextToken());
		sdir = Integer.parseInt(st.nextToken());
		st = new StringTokenizer(br.readLine());
		ex = Integer.parseInt(st.nextToken());
		ey = Integer.parseInt(st.nextToken());
		edir = Integer.parseInt(st.nextToken());

		bfs();
		
		System.out.println(answer);
		
		
	}
}

```