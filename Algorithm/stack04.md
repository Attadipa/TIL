# 후위식 연산(postfix)

Stack활용문제

풀이

1.isDigit()사용 고려해보자
2.char->int 방법 아스키코드이용하여 -48하는 방법도 고려해보자

```java
import java.util.Scanner;
import java.util.Stack;

public class Main {
	
	public static int Solution(String s) {
		Stack<Integer> stack = new Stack<>();
		int answer = 0;
		int n1 =0;
		int n2 =0;
		for(char c : s.toCharArray()) {
			if(c=='+'||c=='-'||c=='*'||c=='/') {
				n2 = stack.pop();
				n1 = stack.pop();
					 if(c=='+') stack.push(n1+n2);
				else if(c=='-') stack.push(n1-n2);
				else if(c=='*') stack.push(n1*n2);
				else if(c=='/') stack.push(n1/n2);
			} else stack.push(c-'0');
		}
		answer = stack.pop();
		return answer;
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		String s = sc.next();
		System.out.print(Solution(s));
	} 
}
```