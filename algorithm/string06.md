# 중복문자제거

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

풀이1 (HashSet을 활용한 중복제거)

```java
import java.util.HashSet;
import java.util.Scanner;
import java.util.Set;

public class Main {
	public static void solution(String str) {
		Set<Character> set = new HashSet<>();
		char[] arr = str.toCharArray();
		String answer = "";
		for(int i = 0 ; i<arr.length ; i++) {
			if(!set.contains(arr[i])) {
				answer+= arr[i];
				set.add(arr[i]);
			}
		}
		System.out.println(answer);
		
		
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		String str = sc.nextLine();
		solution(str);
	}
}
```

풀이2 (indexOf()활용)
```java

public class Main {
	public static void solution(String str) {
		String answer = "";
		for(int i = 0 ; i<str.length() ; i++) {
			if(str.indexOf(str.charAt(i))==i) answer += str.charAt(i);
		}
		System.out.println(answer);
		
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		String str = sc.nextLine();
		solution(str);
	}
}
```