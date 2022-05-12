#TwoPointers & Sliding window
TwoPointers와 Sliding window을 모두 사용한 복합문제이다 
for문의 i만 사용하면 굉장히 풀기 어렵다. Pointer를 적절히 사용해야 한다.

```java
import java.util.Scanner;

public class Main {
	
	public static int Solution(int n) {
		int cnt = 0;
		int sum = 0;
		int lt = 0;
		int m = n/2+1;
		
		int[] arr = new int[m];
		for(int i = 0 ; i<m ; i++) arr[i] = i+1;
		for(int rt = 0 ; rt<m ; rt++) {
			sum+=arr[rt];
			while(sum>=n) {
				if(sum==n) cnt++;
				sum-=arr[lt];
				lt++;
			}
		} return cnt;
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		System.out.println(Solution(n));
	} 
}
```



