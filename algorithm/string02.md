# 대소문자 변환

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

풀이

```java
import java.util.Scanner;

public class Main {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		String str = sc.nextLine();
		String answer = "";
		for(char c : str.toCharArray()) {
			if(c>=65 && c<=90) answer += (char)(c+32);
			else answer += (char)(c-32);
		}
		System.out.println(answer);
	}
}
```
