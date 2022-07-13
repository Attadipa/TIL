# 문자 찾기

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

풀이

```java
import java.util.Scanner;

public class Main {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		String str = sc.nextLine().toLowerCase();
		char ch = sc.nextLine().toLowerCase().charAt(0);
		int cnt = 0;
		for(char c : str.toCharArray()) {
			if(c==ch) cnt++;
		}
		System.out.println(cnt);
	}
}
```