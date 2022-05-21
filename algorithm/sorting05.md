# 중복확인

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

내 풀이1 (HashMap을 이용해서 size와 배열의 크기를 비교)

```java
import java.util.HashSet;
import java.util.Scanner;

public class Main {
	public static char Solution(int n, int[] arr) {
		HashSet<Integer> set = new HashSet<>();
		for(int i : arr) set.add(i);
		if(set.size()<arr.length) return 'D';
		else return 'U';
		
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

내 풀이2 (정렬 후 인접한 수 끼리 비교하여 동일성 여부 판단)

```java
import java.util.Arrays;
import java.util.Scanner;

public class Main {
	public static char Solution(int n, int[] arr) {
		Arrays.sort(arr);
		char answer = 'U';
		for(int i = 0 ; i<n-1 ; i++) {
			if(arr[i]!=arr[i+1]) return 'D';
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