# 이분 검색(Binary Search)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

내 풀이

```java
import java.util.Arrays;
import java.util.Scanner;

public class Main {
	public static int solution(int n, int m, int[] arr) {
		Arrays.sort(arr);
		int lt = 0;
		int rt = n-1;
		while(true) {
			int mid = (lt+rt)/2;
			if(arr[mid]==m) return mid+1;
			else if(arr[mid]>m) rt = mid-1;
			else lt = mid+1;
		}
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int m = sc.nextInt();
		int[] arr = new int[n];
		for(int i = 0; i<n ; i++) {
			arr[i] = sc.nextInt();
		}
		System.out.println(solution(n,m,arr));
	}
}
```