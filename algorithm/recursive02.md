# 피보나치 수열 (배열과 재귀함수 활용 비교)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

성능자체는 배열을 활용하는 것이 낫다. 재귀함수는 스택프레임도 써야되고 자원낭비도 심하고 무거움.

여기서는 재귀함수로도 풀이할 수 있다는 것만 연습.


풀이(배열)

```java
import java.util.Scanner;

public class Main {
	
	public static void solution(int n) {
		int[] arr = new int[n];
		arr[0] = 1;
		arr[1] = 1;
		for(int i = 2 ; i<n ; i++) {
			arr[i] = arr[i-1] + arr[i-2];
		}
		for(int i : arr) System.out.print(i+" ");
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		solution(n);
	}
}
```


풀이(재귀함수)

```java
import java.util.Scanner;

public class Main {
	
	public static int recursive(int n) {
		if(n==1) return 1;
		else if(n==2) return 1;
		else return recursive(n-1) + recursive(n-2);
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		for(int i = 1 ; i<=n ; i++) System.out.print(recursive(i)+" ");
	}
}
```