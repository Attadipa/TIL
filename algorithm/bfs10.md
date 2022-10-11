# 숨바꼭질2

### 백준 12851번 문제

------------

### 문제

    수빈이는 동생과 숨바꼭질을 하고 있다. 수빈이는 현재 점 N(0 ≤ N ≤ 100,000)에 있고, 동생은 점 K(0 ≤ K ≤ 100,000)에 있다. 수빈이는 걷거나 순간이동을 할 수 있다. 만약, 수빈이의 위치가 X일 때 걷는다면 1초 후에 X-1 또는 X+1로 이동하게 된다. 순간이동을 하는 경우에는 1초 후에 2*X의 위치로 이동하게 된다.

    수빈이와 동생의 위치가 주어졌을 때, 수빈이가 동생을 찾을 수 있는 가장 빠른 시간이 몇 초 후인지 그리고, 가장 빠른 시간으로 찾는 방법이 몇 가지 인지 구하는 프로그램을 작성하시오.

### 입력

    첫 번째 줄에 수빈이가 있는 위치 N과 동생이 있는 위치 K가 주어진다. N과 K는 정수이다.

### 출력

    첫째 줄에 수빈이가 동생을 찾는 가장 빠른 시간을 출력한다.

    둘째 줄에는 가장 빠른 시간으로 수빈이가 동생을 찾는 방법의 수를 출력한다.

### 예제 입력 1 

    5 17

### 예제 출력 1 

    4
    2

### 내 풀이

```java

import java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;

public class Main {
	
	static int[] dx = {1,-1};
	static int[] check = new int[100001];
	static int answer;
	static int cnt;
	static boolean isEnd = false;
	
	public static int next(int mode, int now) {
		if(mode==0) return now+1;
		else if(mode==1) return now-1;
		else return now*2;
	}
	public static void bfs(int n, int k) {
		Queue<Integer> q = new LinkedList<>();
		if(n==k) {
			answer = 0;
			cnt = 1;
			return;
		}
		q.offer(n);
		check[n] = 1;

		int lev = 1;
		while(!q.isEmpty()) {
			int size = q.size();
			for(int i = 0 ; i<size ;i++) {
				int now = q.poll();
				for(int j = 0 ; j<3 ;j++) {
					int nx = next(j,now);
					if(nx==k) {
						isEnd = true;
						cnt++;
						continue;
					}
					if(nx>=0 && nx<=100000 && (check[nx]==0 || check[nx]==lev)) {
						q.offer(nx);
						check[nx]=lev;
					}
				}
			}
			if(isEnd) {
				answer = lev;
				return;
			}
			lev++;
		}
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int k = sc.nextInt();
		bfs(n,k);
		System.out.println(answer);	
		System.out.println(cnt);	
	}
}

```