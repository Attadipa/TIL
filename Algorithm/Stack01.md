# 올바른 괄호

### Stack 활용문제

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

해설

```java
import java.util.Scanner;
import java.util.Stack;

public class Main {
	
	public static String Solution(String s) {
		String answer = "YES";
		Stack<Character> stack = new Stack<>();
		for(char c : s.toCharArray()) {
			if(c=='(') stack.push(c);
			else {
				if(stack.isEmpty()) return "NO";
				stack.pop();
			}
		}
		if(!stack.isEmpty()) return "NO";
		else return answer;
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		String s = sc.next();
		System.out.print(Solution(s));
	} 
}
```