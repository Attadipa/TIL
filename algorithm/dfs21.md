# 영역 구하기

### 백준 2583번 문제

------------

### 문제

	눈금의 간격이 1인 M×N(M,N≤100)크기의 모눈종이가 있다. 이 모눈종이 위에 눈금에 맞추어 K개의 직사각형을 그릴 때, 
	이들 K개의 직사각형의 내부를 제외한 나머지 부분이 몇 개의 분리된 영역으로 나누어진다.

	예를 들어 M=5, N=7 인 모눈종이 위에 <그림 1>과 같이 직사각형 3개를 그렸다면, 그 나머지 영역은 <그림 2>와 
	같이 3개의 분리된 영역으로 나누어지게 된다.

<img src="https://www.acmicpc.net/upload/images/zzJD2aQyF5Rm4IlOt.png"></img><br/>

	<그림 2>와 같이 분리된 세 영역의 넓이는 각각 1, 7, 13이 된다.

	M, N과 K 그리고 K개의 직사각형의 좌표가 주어질 때, K개의 직사각형 내부를 제외한 나머지 부분이 몇 개의 
	분리된 영역으로 나누어지는지, 그리고 분리된 각 영역의 넓이가 얼마인지를 구하여 이를 출력하는 프로그램을 작성하시오.

### 입력

	첫째 줄에 M과 N, 그리고 K가 빈칸을 사이에 두고 차례로 주어진다. M, N, K는 모두 100 이하의 자연수이다. 
	둘째 줄부터 K개의 줄에는 한 줄에 하나씩 직사각형의 왼쪽 아래 꼭짓점의 x, y좌표값과 오른쪽 위 꼭짓점의 x, y좌표값이 
	빈칸을 사이에 두고 차례로 주어진다. 모눈종이의 왼쪽 아래 꼭짓점의 좌표는 (0,0)이고, 오른쪽 위 꼭짓점의 좌표는(N,M)이다.
	입력되는 K개의 직사각형들이 모눈종이 전체를 채우는 경우는 없다.

### 출력

	첫째 줄에 분리되어 나누어지는 영역의 개수를 출력한다. 
	둘째 줄에는 각 영역의 넓이를 오름차순으로 정렬하여 빈칸을 사이에 두고 출력한다.

### 예제 입력 1 

	5 7 3
	0 2 4 4
	1 1 2 5
	4 0 6 2

### 예제 출력 1 

	3
	1 7 13

### 내 풀이

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.Scanner;

public class Main {
	static int m,n,k,cnt,areaCnt;
	static int[][] graph;
	static ArrayList<Integer> area = new ArrayList<>();
	static int[] dx = {1,-1,0,0};	
	static int[] dy = {0,0,1,-1};	
	
	public static void dfs(int x, int y) {
		if(graph[x][y]==1) return;
		else {
			graph[x][y]=1;
			areaCnt++;
			for(int i = 0 ; i<4 ; i++) {
				int nx = x+dx[i];
				int ny = y+dy[i];
				if(nx>=0 && nx<m && ny>=0 && ny<n) {
					dfs(nx,ny);
				}
				
			}
		}
	}
	
    public static void main(String[] args) {
    	Scanner sc = new Scanner(System.in);
    	m = sc.nextInt();
    	n = sc.nextInt();
    	k = sc.nextInt();
    	graph = new int[m][n];
    	//그림 뒤집기
    	for(int i = 0 ; i<k ;i++) {
    		int lx = sc.nextInt();
    		int ly = sc.nextInt();
    		int rx = sc.nextInt();
    		int ry = sc.nextInt();
    		for(int j = ly ; j< ry ; j++) {
    			for(int h = lx ; h< rx ; h++) {
        			graph[j][h] = 1;
        		}
    		}
    	}
    	for(int i = 0 ; i<m ; i++) {
        	for(int j = 0 ; j<n ; j++) {
        		if(graph[i][j]==0) {
        			cnt++;
        			areaCnt=0;
        			dfs(i,j);
        			area.add(areaCnt);
        		}
        	}
    	}
    	System.out.println(cnt);
    	Collections.sort(area);
    	for(int i : area) System.out.print(i+" ");

    }
}
```