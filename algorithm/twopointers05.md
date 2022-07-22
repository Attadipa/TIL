# 최대매출

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

풀이1(two pointers 사용);

```java
import java.util.Scanner;

public class Main {
	public static int solution(int n, int k, int[] arr) {
		int sum = 0;
		for(int i = 0 ; i<k ; i++) {
			sum+=arr[i];
		}
		int p1 = 0;
		int p2 = k-1;
		int max = sum;
		while(p2<n-1) {
			p2++;
			sum = sum-arr[p1]+arr[p2];
			max = Math.max(max, sum);
			p1++;
		}
		return max;
	}
	public static void main(String[] args) {
		Scanner sc =  new Scanner(System.in);
		int n = sc.nextInt();
		int k = sc.nextInt();
		int[] arr = new int[n];
		for(int i = 0 ; i<n ; i++) {
			arr[i] = sc.nextInt();
		}
		System.out.println(solution(n,k,arr));
	}
}
```



풀이2

```java
public class Main {
	public static int solution(int n, int k, int[] arr) {
		int sum = 0;
		for(int i = 0 ; i<k ; i++) {
			sum+=arr[i];
		}
		int max = sum;
		for(int i = k ; i<n ; i++) {
			sum = sum+arr[i]-arr[i-k];
			max = Math.max(max, sum);
		}
		return max;
	}
	public static void main(String[] args) {
		Scanner sc =  new Scanner(System.in);
		int n = sc.nextInt();
		int k = sc.nextInt();
		int[] arr = new int[n];
		for(int i = 0 ; i<n ; i++) {
			arr[i] = sc.nextInt();
		}
		System.out.println(solution(n,k,arr));
	}
}
```