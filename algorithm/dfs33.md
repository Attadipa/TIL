# 미로 탈출하기

### 백준 17090번

-------

### 문제

	크기가 N×M인 미로가 있고, 미로는 크기가 1×1인 칸으로 나누어져 있다. 미로의 각 칸에는 문자가 하나 적혀있는데, 적혀있는 문자에 따라서 다른 칸으로 이동할 수 있다.

	어떤 칸(r, c)에 적힌 문자가

	U인 경우에는 (r-1, c)로 이동해야 한다.
	R인 경우에는 (r, c+1)로 이동해야 한다.
	D인 경우에는 (r+1, c)로 이동해야 한다.
	L인 경우에는 (r, c-1)로 이동해야 한다.
	미로에서 탈출 가능한 칸의 수를 계산해보자. 탈출 가능한 칸이란, 그 칸에서 이동을 시작해서 칸에 적힌대로 이동했을 때, 미로의 경계 밖으로 이동하게 되는 칸을 의미한다.

### 입력

	첫째 줄에 미로의 크기 N, M(3 ≤ N, M ≤ 500)이 주어진다. 둘째 줄부터 N개의 줄에는 미로의 각 칸에 적힌 문자가 주어진다.

### 출력

	첫째 줄에 탈출 가능한 칸의 수를 출력한다.

### 예제 입력 1 

	3 3
	DDD
	DDD
	DDD

### 예제 출력 1 

	9

### 예제 입력 2 

	3 3
	DDR
	DLU
	LLL

### 예제 출력 2 

	9

### 예제 입력 3 

	3 3
	RRD
	RDD
	ULL

### 예제 출력 3 

	0

### 예제 입력 4 

	3 4
	RRDD
	RRDR
	DULU

### 예제 출력 4 

	4



### 내 풀이(시간초과 문제때문에 check배열 적극활용해야함)

```java

import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main{

import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.StringTokenizer;

public class Main{
	
	
	public static int n,m;
	public static int cnt=0;
	
	public static char[][] graph;
	public static int[][] check;
	
	public static boolean move(int i, int j) {
		if(i<0 || i>=n || j<0 || j>=m || check[i][j]==7) {
			cnt++;
			return true;	
		}
		if(check[i][j]==1 || check[i][j]==-1) {
			return false;
		}
		else {
			check[i][j]=1;
			if(graph[i][j]=='U') check[i][j] = move(i-1,j) ? 7 : -1;
			else if(graph[i][j]=='R') check[i][j] = move(i,j+1) ? 7 : -1;
			else if(graph[i][j]=='D') check[i][j] = move(i+1,j) ? 7 : -1;
			else if(graph[i][j]=='L') check[i][j] = move(i,j-1) ? 7 : -1;
			
			return check[i][j] == 7 ? true : false;
		}
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
			}
		}
		for (int i = 0; i < n; i++) {
			for (int j = 0; j < m; j++) {
				move(i,j);
			}
		}
		System.out.println(cnt);
		br.close();
		
	}
}



```