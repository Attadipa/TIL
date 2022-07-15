# 소수(에라토스테네스 체)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

풀이

```java
import java.util.Scanner;

public class Main {
	public static void solution(int n, int[] arr) {
		int cnt = 0;
		for(int i = 2 ; i<=n ; i++) {
			if(arr[i]==0) {
				cnt++;
				for(int j = i ; j<=n ; j = j+i) {
					arr[j] = 1;
				}
			}
		}
		System.out.println(cnt);
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int[] arr = new int[n+1];
		solution(n,arr);
	}
}
```