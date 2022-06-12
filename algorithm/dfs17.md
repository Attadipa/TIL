# 피자 배달 거리(삼성 SW역량평가 기출문제 : DFS활용)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비


내 풀이(부분집합 활용)

```java
import java.util.ArrayList;
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
	static int n,m= 0;
	static ArrayList<Node> home = new ArrayList<>();
	static ArrayList<Node> pizza = new ArrayList<>();
	static int[][] board;
	static Node[] arr;
	static int min = Integer.MAX_VALUE;

	public static void dfs(int lev, int cnt) { 
		if(lev==pizza.size() && cnt!=m) return;
		if(cnt==m) {
			int cityLeng = 0;
			for(Node hom : home) {
				int homeLeng = Integer.MAX_VALUE;
				for(Node piz : arr) {
					int leng = Math.abs(hom.x-piz.x)+Math.abs(hom.y-piz.y);
					homeLeng = Math.min(homeLeng, leng);
				}
				cityLeng += homeLeng;
			}
			min = Math.min(min, cityLeng);
		}else {
			arr[cnt] = pizza.get(lev);
			dfs(lev+1,cnt+1);
			dfs(lev+1,cnt);
		}
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		n = sc.nextInt();
		m = sc.nextInt();
		arr = new Node[m];
		board = new int[n+1][n+1];	
		for(int i = 1 ; i<=n ; i++) {
			for(int j = 1; j<=n ;j++) {
				board[i][j]=sc.nextInt();
				if(board[i][j]==1) home.add(new Node(i,j));
				else if(board[i][j]==2) pizza.add(new Node(i,j));
			}
		}
		dfs(0,0);
		System.out.println(min);
		
	}
}
```

해설(조합 구하기 활용)

```java
import java.util.ArrayList;
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
	static int n,m= 0;
	static ArrayList<Node> home = new ArrayList<>();
	static ArrayList<Node> pizza = new ArrayList<>();
	static int[][] board;
	static int[] check;
	static int answer = Integer.MAX_VALUE;
	
	public static void dfs(int lev, int start) { 
		if(lev==m) {
			int sum = 0;
			for(Node hom : home) {
				int dis = Integer.MAX_VALUE;
				for(int i : check) {
					int tmp = Math.abs(hom.x-pizza.get(i).x)+Math.abs(hom.y-pizza.get(i).y);
					dis = Math.min(dis,tmp);
				}
				sum += dis;
			}
			answer = Math.min(answer, sum);
			
		} else {
			for(int i = start ; i<pizza.size() ; i++) {
				check[lev]=i;
				dfs(lev+1,i+1);
			}
		}
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		n = sc.nextInt();
		m = sc.nextInt();
		board = new int[n+1][n+1];	
		check = new int[m];
		for(int i = 1 ; i<=n ; i++) {
			for(int j = 1; j<=n ;j++) {
				board[i][j]=sc.nextInt();
				if(board[i][j]==1) home.add(new Node(i,j));
				else if(board[i][j]==2) pizza.add(new Node(i,j));
			}
		}
		dfs(0,0);
		System.out.println(answer);
	}
}
```

