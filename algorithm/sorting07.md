# 마구간 정하기(결정알고리즘)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

풀이

```java
import java.util.Arrays;
import java.util.Scanner;


public class Main {
	public static int count(int[] arr, int mid) {
		int cnt = 1;
		int end = arr[0];
		for(int i = 0 ; i < arr.length ; i++) {
			if(arr[i]-end>=mid) {
				cnt++;	
				end = arr[i];
			}
		}
		return cnt;
	}
	
	public static int solution(int n, int c, int[] arr) {
		Arrays.sort(arr);
		int answer = 0;;
		int lt = 1;
		int rt = arr[n-1];
		while(lt<=rt) {
			int mid = (lt+rt)/2;
			if(count(arr, mid)>=c) {
				answer = mid;
				lt = mid+1;
			} else rt = mid-1;
		} return answer;
		
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int c = sc.nextInt();
		int[] arr = new int[n];
		for(int i = 0; i<n ; i++) {
			arr[i] = sc.nextInt();
		}
		System.out.println(solution(n,c,arr));
	}
}
```