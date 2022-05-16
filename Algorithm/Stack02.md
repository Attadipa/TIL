# 괄호문자제거 

Stack 활용문제

풀이

```java
import java.util.Scanner;
import java.util.Stack;

public class Main {
	
	public static String Solution(String s) {
		Stack<Character> stack = new Stack<>();
		String answer = "";
		for(char c : s.toCharArray()) {
			if(c=='(') stack.push(c);
			else if(c==')') stack.pop();
			else if(stack.isEmpty()) answer+=c;
		}
		return answer;
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		String s = sc.next();
		System.out.print(Solution(s));
	} 
}
```
