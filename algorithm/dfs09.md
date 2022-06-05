# 중복순열

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

모든 경우의 수 구하기

내 풀이

```java
import java.util.Scanner;

public class Main {

	static int n,m = 0;
	public static void dfs(int level, String sum) {
		if(level==m) System.out.println(sum); 
		else {
			for(int i = 1 ; i<=n ; i++) {
				dfs(level+1,sum+i+" ");
			}
		}
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		n = sc.nextInt();
		m = sc.nextInt();
		dfs(0,"");
	}
}
```

해설(배열 사용)

```java
import java.util.Scanner;

public class Main {

	static int n,m = 0;
	static int[] arr;
	public static void dfs(int level) {
		if(level==m) {
			for(int i : arr) System.out.print(i+" ");
			System.out.println();
		}
		else {
			for(int i = 1 ; i<=n ; i++) {
				arr[level] = i;
				dfs(level+1);
			}
		}
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		n = sc.nextInt();
		m = sc.nextInt();
		arr=new int[m];
		dfs(0);
	}
}
```