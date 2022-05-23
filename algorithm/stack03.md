# 크레인 인형뽑기(카카오 기출)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

풀이

```java
import java.util.Scanner;
import java.util.Stack;

public class Main {
	
	public static int Solution(int n, int[][] arr, int m, int[] moves) {
		Stack<Integer> stack = new Stack<>();
		int cnt = 0;
		for(int j : moves) {
			for(int i=0 ; i<n ; i++) {
				if(arr[i][j-1]!=0) {
					if(stack.isEmpty() || arr[i][j-1]!=stack.get(stack.size()-1)) {
						stack.push(arr[i][j-1]);
					} else {
						stack.pop();
						cnt+=2;
					}
					arr[i][j-1]=0;
					break;
				}
			}
		} 
		return cnt;
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int[][] arr = new int[n][n];
		for(int i = 0 ; i<n ; i++) {
			for(int j = 0 ; j<n ; j++) {
				arr[i][j] = sc.nextInt();
			}
		}
		int m = sc.nextInt();
		int[] moves = new int[m];
		for(int i = 0 ; i<m ; i++) {
			moves[i] = sc.nextInt();
		}
		System.out.print(Solution(n,arr,m,moves));
	} 
}
```