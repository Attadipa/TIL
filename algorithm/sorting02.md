# 버블정렬(Bubble Sort)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

내 풀이

```java
import java.util.Scanner;

public class Main {
	public static String Solution(int n, int[] arr) {	
		for(int j = n-1 ; j>0 ; j--) {
			for(int i = 0; i<j ;i++) {
				if(arr[i]>arr[i+1]) {
					int tmp = arr[i];
					arr[i] = arr[i+1];
					arr[i+1] = tmp;
				}
			}
		}
		String answer = "";
		for(int i : arr) {
			answer += i+" ";
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