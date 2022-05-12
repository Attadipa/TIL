# 연속부분수열

TwoPointers와 Sliding window을 모두 사용하는 복합문제

해설

```java
import java.util.Scanner;

public class Main {
	
	public static int Solution(int n, int k, int[] arr) {
		int cnt= 0;
		int lt = 0;
		int length = 0;
		for(int rt = 0 ; rt<n ; rt++) {
			if(arr[rt]==0)cnt++;
			while(k<cnt) {
				if(arr[lt]==0)cnt--;
				lt++;
			} 
			length = Math.max(length,rt-lt+1);
		}
		return length;
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int k = sc.nextInt();
		int[] arr = new int[n];
		for(int i = 0; i<n; i++) {
			arr[i] = sc.nextInt();
		}
		System.out.println(Solution(n,k,arr));
	} 
}
```

내 풀이

```java
import java.util.Scanner;

public class Main {
	
	public static int Solution(int n, int k, int[] arr) {
		int sum = 0;
		int lt = 0;
		int length =0;
		for(int rt = 0 ; rt<n ; rt++) {
			sum+=arr[rt];
			length = rt-lt+1;
			if(sum+k<length) {
				sum-=arr[lt];
				lt++;
			}
			length = rt-lt+1;
		}
		return length;
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int k = sc.nextInt();
		int[] arr = new int[n];
		for(int i = 0; i<n; i++) {
			arr[i] = sc.nextInt();
		}
		System.out.println(Solution(n,k,arr));
	} 
}
```
