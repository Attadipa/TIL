# 장난꾸러기

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

내 풀이(원본과 정렬한 것을 서로 비교)

```java
import java.util.Arrays;
import java.util.Scanner;

public class Main {
	public static String Solution(int n, int[] arr) {
		int[] arr2 = new int[n];
		for(int i=0 ; i<n ; i++) arr2[i]=arr[i];
		Arrays.sort(arr2);
		String answer ="";
		for(int i=0 ; i<n ; i++) {
			if(arr[i]!=arr2[i]) answer += i+1+" ";
		}
		return answer;
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int[] arr = new int[n];
		for(int i = 0; i<n ; i++) {
			arr[i] = sc.nextInt();
		}
		System.out.print(Solution(n,arr));
	} 
}
```