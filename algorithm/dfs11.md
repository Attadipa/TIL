# 순열 구하기

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

경우의 수 구하기(중복불가)

내 풀이

```java
import java.util.Arrays;
import java.util.Scanner;

public class Main {

	static int n,m=0;
	static int[] arr,check,result;
	
	public static void dfs(int lev) {
		if(lev==m) {
			for(int i = 0 ; i<m; i++) {
				System.out.print(result[i]+" ");
			}
			System.out.println();
		} else {
			for(int i : arr) {
				if(check[i]==0) {
					check[i]=1;
					result[lev]=i;
					dfs(lev+1);
					check[i]=0;
				}
			}
		}
		
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		n = sc.nextInt();
		m = sc.nextInt();
		arr = new int[n];
		check = new int[11];
		result = new int[m];
		for(int i = 0 ; i<n ; i++) {
			arr[i] = sc.nextInt();
		}
		Arrays.sort(arr);
		dfs(0);
	}
}
```


해설(check배열의 길이가 더 짧다)

```java
import java.util.Arrays;
import java.util.Scanner;

public class Main {

	static int n,m=0;
	static int[] arr,check,result;
	
	public static void dfs(int lev) {
		if(lev==m) {
			for(int i = 0 ; i<m; i++) {
				System.out.print(result[i]+" ");
			}
			System.out.println();
		} else {
			for(int i = 0 ; i<n ; i++) {
				if(check[i]==0) {
					check[i]=1;
					result[lev]=arr[i];
					dfs(lev+1);
					check[i]=0;
				}
			}
		}
		
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		n = sc.nextInt();
		m = sc.nextInt();
		arr = new int[n];
		check = new int[n];
		result = new int[m];
		for(int i = 0 ; i<n ; i++) {
			arr[i] = sc.nextInt();
		}
		Arrays.sort(arr);
		dfs(0);
	}
}
```
