# 단어 뒤집기

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

풀이1

```java
import java.util.Scanner;

public class Main {
	public static void solution(int n, String[] arr) {
		for(String str : arr) {
			char[] chArr = str.toCharArray();
			for(int i = chArr.length-1 ; i>=0 ; i--) {
				System.out.print(chArr[i]);
			}
			System.out.println();
		}
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		sc.nextLine();
		String[] arr = new String[n];
		for(int i = 0 ; i<n ; i++) {
			arr[i] = sc.nextLine();
		}
		solution(n,arr);
		
	}
}
```

풀이2
```java
import java.util.Scanner;

public class Main {
	public static void solution(int n, String[] arr) {
		for(String str : arr) {
			str = new StringBuilder(str).reverse().toString();
			System.out.println(str);
		}
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		sc.nextLine();
		String[] arr = new String[n];
		for(int i = 0 ; i<n ; i++) {
			arr[i] = sc.nextLine();
		}
		solution(n,arr);
	}
}
```

풀이3
```java
import java.util.Scanner;

public class Main {
	public static void solution(int n, String[] arr) {
		for(String str : arr) {
			char[] chArr = str.toCharArray();
			int lt = 0;
			int rt = str.length()-1;
			while(lt<rt) {
				char tmp = chArr[lt];
				chArr[lt] = chArr[rt];
				chArr[rt] = tmp;
				lt++;
				rt--;
			}
			System.out.println(new String(chArr));
		}
		
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		sc.nextLine();
		String[] arr = new String[n];
		for(int i = 0 ; i<n ; i++) {
			arr[i] = sc.nextLine();
		}
		solution(n,arr);
	}
}
```