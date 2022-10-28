# 탈출

### 백준 3055번 문제

------------

### 문제

    사악한 암흑의 군주 이민혁은 드디어 마법 구슬을 손에 넣었고, 그 능력을 실험해보기 위해 근처의 티떱숲에 홍수를 
    일으키려고 한다. 이 숲에는 고슴도치가 한 마리 살고 있다. 고슴도치는 제일 친한 친구인 비버의 굴로 가능한 빨리 
    도망가 홍수를 피하려고 한다.

    티떱숲의 지도는 R행 C열로 이루어져 있다. 비어있는 곳은 '.'로 표시되어 있고, 물이 차있는 지역은 '*', 
    돌은 'X'로 표시되어 있다. 비버의 굴은 'D'로, 고슴도치의 위치는 'S'로 나타내어져 있다.

    매 분마다 고슴도치는 현재 있는 칸과 인접한 네 칸 중 하나로 이동할 수 있다. 
    (위, 아래, 오른쪽, 왼쪽) 물도 매 분마다 비어있는 칸으로 확장한다. 
    물이 있는 칸과 인접해있는 비어있는 칸(적어도 한 변을 공유)은 물이 차게 된다. 물과 고슴도치는 돌을 통과할 수 없다. 
    또, 고슴도치는 물로 차있는 구역으로 이동할 수 없고, 물도 비버의 소굴로 이동할 수 없다.

    티떱숲의 지도가 주어졌을 때, 고슴도치가 안전하게 비버의 굴로 이동하기 위해 필요한 최소 시간을 구하는 
    프로그램을 작성하시오.

    고슴도치는 물이 찰 예정인 칸으로 이동할 수 없다. 즉, 다음 시간에 물이 찰 예정인 칸으로 고슴도치는 이동할 수 없다. 
    이동할 수 있으면 고슴도치가 물에 빠지기 때문이다. 

### 입력

    첫째 줄에 50보다 작거나 같은 자연수 R과 C가 주어진다.

    다음 R개 줄에는 티떱숲의 지도가 주어지며, 문제에서 설명한 문자만 주어진다. 'D'와 'S'는 하나씩만 주어진다.

### 출력

    첫째 줄에 고슴도치가 비버의 굴로 이동할 수 있는 가장 빠른 시간을 출력한다. 만약, 안전하게 비버의 굴로 이동할 수 
    없다면, "KAKTUS"를 출력한다.

### 예제 입력 1 

    3 3
    D.*
    ...
    .S.

### 예제 출력 1 

    3

### 예제 입력 2 

    3 3
    D.*
    ...
    ..S

### 예제 출력 2 

    KAKTUS

### 예제 입력 3 

    3 6
    D...*.
    .X.X..
    ....S.

### 예제 출력 3 

    6

### 예제 입력 4 

    5 4
    .D.*
    ....
    ..X.
    S.*.
    ....

### 예제 출력 4 

    4


### 내 풀이

```java

import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.LinkedList;
import java.util.Queue;
import java.util.StringTokenizer;

class Node{
	int x;
	int y;
	int lev;
	
	public Node() {
	}
	public Node(int x, int y, int lev) {
		this.x = x;
		this.y = y;
		this.lev = lev;
	}
}

public class Main{
	
	public static int n,m,srow,scol;
	public static int[] dx = {1,-1,0,0};
	public static int[] dy = {0,0,1,-1};
	
	public static ArrayList<Node> list = new ArrayList<>();
	public static char[][] graph;
	public static int[][] check;
	
	public static void bfs() {
		Queue<Node> q = new LinkedList<>();
		Queue<Node> waterQ = new LinkedList<>();
		
		q.add(new Node(srow,scol,0));
		for(Node node : list) {
			waterQ.add(node);
			check[node.x][node.y]=2;
		}
		
		while(!q.isEmpty()) {
			
			int leng = waterQ.size();
			for(int i = 0 ; i<leng ; i++) {
				Node now = waterQ.poll();
				for(int j = 0; j<4 ; j++) {
					int nx = now.x + dx[j];
					int ny = now.y + dy[j];
					if(nx>=0 && nx<n && ny>=0 && ny<m &&
					    check[nx][ny]!=2 && graph[nx][ny] != 'X' && graph[nx][ny]!='D') {
						check[nx][ny]=2;
						waterQ.add(new Node(nx,ny,now.lev+1));
					}
				}
			}
			
			int size = q.size();
			for(int i = 0 ; i<size ; i++) {
				Node now = q.poll();
				for(int j = 0; j<4 ; j++) {
					int nx = now.x + dx[j];
					int ny = now.y + dy[j];
					if(nx>=0 && nx<n && ny>=0 && ny<m && check[nx][ny]==0 && graph[nx][ny] != 'X') {
						if(graph[nx][ny]=='D') {
							System.out.println(now.lev+1);
							return;
						}
						check[nx][ny]=1;
						q.add(new Node(nx,ny,now.lev+1));
					}
					
				}
			}

		}
		System.out.println("KAKTUS");
	}
	
	public static void main(String[] args) throws Exception{
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());
        
		n = Integer.parseInt(st.nextToken());
		m = Integer.parseInt(st.nextToken());
		
		graph = new char[n][m];
		check = new int[n][m];

		for (int i = 0; i < n; i++) {
			String line = br.readLine();
			for (int j = 0; j < m; j++) {
				graph[i][j] = line.charAt(j);
				if(graph[i][j]=='S') {
					srow = i;
					scol = j;
				}
				else if(graph[i][j]=='*') {
					list.add(new Node(i,j,0));
				}
			}
		}
		bfs();
		br.close();
		
	}
}

```