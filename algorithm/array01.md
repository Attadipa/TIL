# 구간 합 구하기4

### 백준 11659번

-------

### 문제

    수 N개가 주어졌을 때, i번째 수부터 j번째 수까지 합을 구하는 프로그램을 작성하시오.

### 입력

    첫째 줄에 수의 개수 N과 합을 구해야 하는 횟수 M이 주어진다. 둘째 줄에는 N개의 수가 주어진다. 수는 1,000보다 작거나 같은 자연수이다. 셋째 줄부터 M개의 줄에는 합을 구해야 하는 구간 i와 j가 주어진다.

### 출력

    총 M개의 줄에 입력으로 주어진 i번째 수부터 j번째 수까지 합을 출력한다.

### 풀이

```java
import java.util.Scanner;

public class Main {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int m = sc.nextInt();
		int[] arr = new int[n+1];
		int[] mem = new int[n+1];
		for(int i = 1 ; i<=n ; i++) {
			arr[i] = sc.nextInt();
			mem[i] = mem[i-1] + arr[i];
		}
		
		int[] start = new int[m];
		int[] end = new int[m];
		for(int i = 0 ; i<m ; i++) {
			start[i] = sc.nextInt();
			end[i] = sc.nextInt();
		}
		
		for(int i = 0 ; i<m ; i++) {
			int result = mem[end[i]] - mem[start[i]-1];
			System.out.println(result);
		}
	}
}
```