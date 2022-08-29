# 단지번호붙이기

### 백준 2667번 문제


내 풀이(섬찾기 문제와 유사)

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.Scanner;

public class Main {
	static int n,cnt, size;
	static int[][] graph;
	static ArrayList<Integer> sizeList = new ArrayList<>();
	static int[] dx = {1,-1,0,0};	
	static int[] dy = {0,0,1,-1};	
	
	public static void dfs(int x, int y) {
		for(int i = 0 ; i<4 ; i++) {
			int nx = x+dx[i];
			int ny = y+dy[i];
			if(nx>=0 && nx<n && ny>=0 && ny<n && graph[nx][ny]==1) {
				graph[nx][ny]=0;
				size++;
				dfs(nx,ny);
			}
		}
	}
	
    public static void main(String[] args) {
    	Scanner sc = new Scanner(System.in);
    	n = sc.nextInt();
    	graph = new int[n][n];
    	for(int i = 0 ; i<n ;i++) {
    		String line = sc.next();
    		for(int j = 0 ; j<n ;j++) {
        		graph[i][j] = line.charAt(j)-'0';
        	}
    	}
    	for(int i = 0 ; i<n ;i++) {
        	for(int j = 0 ; j<n ;j++) {
        		if(graph[i][j]==1) {
        			cnt++;
        			graph[i][j]=0;
        			size=1;
        			dfs(i,j);
        			sizeList.add(size);
        		}
        	}
    	}
    	System.out.println(cnt);
    	Collections.sort(sizeList);
    	for(int i : sizeList) System.out.println(i);
    }
}
```