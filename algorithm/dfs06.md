# 합이 같은 부분집합(DFS : 아마존 인터뷰)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

해설

```java
import java.util.Scanner;

public class Main {

	static int total, n = 0;
	static String answer = "NO";
	static boolean flag = false;
	
	public static void dfs(int L, int sum, int[] arr) {
		if(flag) return;
		if(sum>total/2) return;
		if(L==n) {
			if((total-sum)==sum) {
				answer = "YES";
				flag = true;
			}  
		}
		else {
			dfs(L+1,sum+arr[L],arr);
			dfs(L+1,sum,arr);
		}
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		n = sc.nextInt();
		int[] arr = new int[n];
		for(int i = 0 ; i<n; i++) {
			arr[i] = sc.nextInt();
			total+=arr[i];
		}
		dfs(0,0,arr);
		System.out.println(answer);
		
	}
}
```
