# 피보나치 수열 (배열과 재귀함수 활용 비교)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

성능자체는 배열을 활용하는 것이 낫다. 재귀함수를 사용하면 스택프레임도 쌓이고 자원낭비도 심하고 무거움.

여기서는 재귀함수로도 풀이할 수 있다는 것만 연습.


풀이(배열) 입력값 : 40, 소요시간 : 2ms

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
    long l1 = System.currentTimeMillis();
		solution(n);
    long l2 = System.currentTimeMillis();
		System.out.println("\n소요시간 : "+(l2-l1)+"ms");
	}
}
```


풀이(재귀함수) 입력값 : 40, 소요시간 : 1303ms

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
    long l1 = System.currentTimeMillis();
		for(int i = 1 ; i<=n ; i++) System.out.print(recursive(i)+" ");
    long l2 = System.currentTimeMillis();
		System.out.println("\n소요시간 : "+(l2-l1)+"ms");
	}
}
```

풀이(배열 + 재귀함수) 입력값 : 40, 소요시간 : 2ms


```java
import java.util.Scanner;

public class Main {
	public static int[] arr;
	public static int recursive(int n) {
		if(arr[n]>0) return arr[n];
		if(n==1) return arr[n] = 1;
		else if(n==2) return arr[n] = 1;
		else return arr[n] = recursive(n-1) + recursive(n-2);
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		arr = new int[n+1];
		long l1 = System.currentTimeMillis();
		recursive(n);
		for(int i = 1 ; i<=n ; i++) System.out.print(arr[i]+" ");
		long l2 = System.currentTimeMillis();
		System.out.println("\n소요시간 : "+(l2-l1)+"ms");
	}
}
```