# 동전교환

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

경우의 수 구하기
시간복잡도를 최대한 줄이는 방법들을 고려해야함
1. 동전의 값이 큰 것부터 내림차순으로 정렬을 하고 for문 돌리기
2. 최소 동전개수로 탐색 수 제한
3. 기준값을 넘어갈 때 탐색 수 제한

내 풀이

```java
import java.util.Arrays;
import java.util.Collections;
import java.util.Scanner;

public class Main {

	static int n,m=0;
	static int min;
	static Integer[] arr;
	
	public static void dfs(int level, int m) {
		if(m<0 || level>=min) return;
		if(m==0) {
			min = Math.min(min, level);
		}
		else {
			for(int i = 0 ; i<n ; i++) {
				dfs(level+1,m-arr[i]);
			}
		}
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		n = sc.nextInt();
		arr = new Integer[n];
		for(int i = 0 ; i<n ; i++) {
			arr[i] = sc.nextInt();
		}
		Arrays.sort(arr,Collections.reverseOrder());
		m = sc.nextInt();
		min = m;
		dfs(0,m);
		System.out.println(min);
	}
}
```