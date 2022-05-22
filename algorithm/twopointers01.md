# 연속된 자연수의 합

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

풀이

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



