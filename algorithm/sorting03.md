# 삽입정렬(Insertion Sort)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

내 풀이

```java
import java.util.Scanner;

public class Main {
	public static String Solution(int n, int[] arr) {
		for(int i =1 ; i<n ; i++) {
			for(int j =i ; j>0 ; j--) {
				if(arr[j-1]>arr[j]) {
					int tmp = arr[j-1];
					arr[j-1] = arr[j];
					arr[j] = tmp;
				} else break;
			}
		}
		String answer = "";
		for(int i : arr) answer += i + " ";
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