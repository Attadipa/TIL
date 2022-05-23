# 올바른 괄호

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

내 풀이

```java
import java.util.Scanner;

public class Main {
	
	public static String Solution(String s) {
		int sum = 0;
		for(char c : s.toCharArray()) {
			if(c=='(') sum++;
			else sum--;
			if(sum<0) return "NO";
		}
		if(sum==0) return "YES";
		else return "NO";
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		String s = sc.next();
		System.out.print(Solution(s));
	} 
}
```
