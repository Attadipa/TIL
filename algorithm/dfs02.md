# 부분집합 구하기

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비


풀이

```java
import java.util.Scanner;

public class Main {
	
	static int n;
	static int[] arr;
	
	public static void recursive(int level) {
		if(level == n+1) {
			for(int i =1 ; i<=n ; i++) {
				if(arr[i]==1)System.out.print(i+" ");
			}System.out.println();
		} else {
			arr[level]=1;
			recursive(level+1);
			arr[level]=0;
			recursive(level+1);
		}
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		n = sc.nextInt();
		arr = new int[n+1];
		recursive(1);
	}
}
```