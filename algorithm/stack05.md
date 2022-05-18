# 쇠막대기(한국정보올림피아드)

Stack활용문제

내 풀이

```java
import java.util.Scanner;
import java.util.Stack;

public class Main {
	
	public static int Solution(String s) {
		Stack<Character> stack = new Stack<>();
		int answer = 0;
		char[] arr = s.toCharArray();
		for(int i=0 ; i<arr.length ; i++) {
			if(arr[i]=='(') stack.push(arr[i]);
			else {
				stack.pop();
				if(arr[i-1]=='(') {
					answer += stack.size();
				} else {
					answer += 1;
				}
			}
		} return answer;
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		String s = sc.next();
		System.out.print(Solution(s));
	} 
}
```