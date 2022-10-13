# 종이의 개수

### 백준 1780번

-------


### 문제

    N×N크기의 행렬로 표현되는 종이가 있다. 종이의 각 칸에는 -1, 0, 1 중 하나가 저장되어 있다. 
    우리는 이 행렬을 다음과 같은 규칙에 따라 적절한 크기로 자르려고 한다.

    만약 종이가 모두 같은 수로 되어 있다면 이 종이를 그대로 사용한다.
    (1)이 아닌 경우에는 종이를 같은 크기의 종이 9개로 자르고, 각각의 잘린 종이에 대해서 (1)의 과정을 반복한다.
    이와 같이 종이를 잘랐을 때, -1로만 채워진 종이의 개수, 0으로만 채워진 종이의 개수, 
    1로만 채워진 종이의 개수를 구해내는 프로그램을 작성하시오.

### 입력

    첫째 줄에 N(1 ≤ N ≤ 37, N은 3k 꼴)이 주어진다. 다음 N개의 줄에는 N개의 정수로 행렬이 주어진다.

### 출력

    첫째 줄에 -1로만 채워진 종이의 개수를, 
    둘째 줄에 0으로만 채워진 종이의 개수를, 
    셋째 줄에 1로만 채워진 종이의 개수를 출력한다.

### 예제 입력 1 

    9
    0 0 0 1 1 1 -1 -1 -1
    0 0 0 1 1 1 -1 -1 -1
    0 0 0 1 1 1 -1 -1 -1
    1 1 1 0 0 0 0 0 0
    1 1 1 0 0 0 0 0 0
    1 1 1 0 0 0 0 0 0
    0 1 -1 0 1 -1 0 1 -1
    0 -1 1 0 1 -1 0 1 -1
    0 1 -1 1 0 -1 0 1 -1

### 예제 출력 1 

    10
    12
    11

### 내 풀이(Scanner보다 BufferedReader가 훨씬 빠르다)

```java

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {
	static int n,result,cnt1,cnt0,cnt_1;
	static int[][] graph;
	static int[] dx = {0,1,2,0,1,2,0,1,2};
	static int[] dy = {0,0,0,1,1,1,2,2,2};
	
	public static int check(int leng, int x, int y) {
		int start = graph[x][y];
		boolean split = false;
		for(int i = x ; i<x+leng ; i++) {
			for(int j = y ; j<y+leng ; j++) {
				 if(start!=graph[i][j]) split=true;
				 
			}
		}
		if(split) return 999;
		else return start;
	}
	public static void dfs(int leng, int x, int y) {
		if((result = check(leng,x,y))!=999) {
			if(result==1) cnt1++;
			else if(result==0) cnt0++;
			else if(result==-1) cnt_1++;
		}else {
			int newLeng = leng/3;
			for(int i = 0 ; i<9 ; i++) {
				int nx = x+dx[i]*(newLeng);
				int ny = y+dy[i]*(newLeng);
				dfs(newLeng,nx,ny);
			}
		}
	}
	
	public static void main(String[] args) throws NumberFormatException, IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int n = Integer.parseInt(br.readLine());
		graph = new int[n][n];
		StringTokenizer st;
 
		for (int i = 0; i < n; i++) {
			st = new StringTokenizer(br.readLine(), " ");
			for (int j = 0; j < n; j++) {
				graph[i][j] = Integer.parseInt(st.nextToken());
			}
		}
		dfs(n,0,0);
		System.out.println(cnt_1);
		System.out.println(cnt0);
		System.out.println(cnt1);
	}
}

```