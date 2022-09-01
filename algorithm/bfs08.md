# 스타트링크

### 백준 5014번 문제

------------

### 문제

    강호는 코딩 교육을 하는 스타트업 스타트링크에 지원했다. 오늘은 강호의 면접날이다. 
    하지만, 늦잠을 잔 강호는 스타트링크가 있는 건물에 늦게 도착하고 말았다.

    스타트링크는 총 F층으로 이루어진 고층 건물에 사무실이 있고, 스타트링크가 있는 곳의 위치는 G층이다. 
    강호가 지금 있는 곳은 S층이고, 이제 엘리베이터를 타고 G층으로 이동하려고 한다.

    보통 엘리베이터에는 어떤 층으로 이동할 수 있는 버튼이 있지만, 강호가 탄 엘리베이터는 버튼이 2개밖에 없다. 
    U버튼은 위로 U층을 가는 버튼, D버튼은 아래로 D층을 가는 버튼이다. 
    (만약, U층 위, 또는 D층 아래에 해당하는 층이 없을 때는, 엘리베이터는 움직이지 않는다)

    강호가 G층에 도착하려면, 버튼을 적어도 몇 번 눌러야 하는지 구하는 프로그램을 작성하시오. 
    만약, 엘리베이터를 이용해서 G층에 갈 수 없다면, "use the stairs"를 출력한다.

### 입력

    첫째 줄에 F, S, G, U, D가 주어진다. (1 ≤ S, G ≤ F ≤ 1000000, 0 ≤ U, D ≤ 1000000) 
    건물은 1층부터 시작하고, 가장 높은 층은 F층이다.

### 출력

    첫째 줄에 강호가 S층에서 G층으로 가기 위해 눌러야 하는 버튼의 수의 최솟값을 출력한다. 
    만약, 엘리베이터로 이동할 수 없을 때는 "use the stairs"를 출력한다.

### 예제 입력 1 

    10 1 10 2 1

### 예제 출력 1 

    6

### 예제 입력 2 

    100 2 1 1 0

### 예제 출력 2 

    use the stairs

### 내 풀이(bfs)

```java
import java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;

public class Main {
	static int f,s,g,u,d;
	static int[] check,dx;
	
	public static void bfs(int start) {
		Queue<Integer> q = new LinkedList<>();
		if(start==g) {
			System.out.println(0);
			return;
		}
		q.offer(start);
		check[start]=1;
		int lev = 0;
		while(!q.isEmpty()) {
			int leng = q.size();
			for(int i = 0 ; i<leng ; i++) {
				int now = q.poll();
				for(int j = 0 ; j<2 ;j++) {
					int nx = now+dx[j];
					if(nx==g) {
						System.out.println(lev+1);
						return;
					}
					if(nx>=1 && nx<=f && check[nx]==0) {
						check[nx] = 1;
						q.offer(nx);
					}
				}
			}
			lev++;
		}
		System.out.println("use the stairs");
	}
	
    public static void main(String[] args) {
    	Scanner sc = new Scanner(System.in);
    	f = sc.nextInt();
    	s = sc.nextInt();
    	g = sc.nextInt();
    	u = sc.nextInt();
    	d = sc.nextInt();
    	check = new int[f+1];
    	dx = new int[]{u,-d};
    	bfs(s);

    }
}
```


### 내 풀이2(dfs) - 값의 범위가 너무 크므로 dfs로 풀면 시간초과. 최소값 찾는 문제에서는 bfs로 풀자.

```java
import java.util.Scanner;

public class Main {
	static boolean flag = false;
	static int f,s,g,u,d;
	static int[] check,dx;
	static int min = Integer.MAX_VALUE;
	
	public static void dfs(int sum, int cnt) {
		if(sum<1 || sum>f) return;
		if(check[sum]==1) return;
		if(sum==g) {
			flag=true;
			min = Math.min(min, cnt);
		}else {
			check[sum]=1;
			dfs(sum+u,cnt+1);
			dfs(sum-d,cnt+1);
			check[sum]=0;
		}
	}
	
    public static void main(String[] args) {
    	Scanner sc = new Scanner(System.in);
    	f = sc.nextInt();
    	s = sc.nextInt();
    	g = sc.nextInt();
    	u = sc.nextInt();
    	d = sc.nextInt();
    	check = new int[f+1];

    	dfs(s,0);
    	
    	if(flag) System.out.println(min);
    	else System.out.println("use the stairs");
    }
}
```