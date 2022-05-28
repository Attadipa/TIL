# 교육과정 설계

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비


Queue활용(구현체는 LinkedList)

내 풀이

```java
import java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;

public class Main {
	
	public static String Solution(String s1, String s2) {
		String answer = "YES";
		Queue<Character> q = new LinkedList<>();
		for(char c : s1.toCharArray()) q.offer(c);
		for(char c : s2.toCharArray()) {
			if(q.contains(c)) {
				if(q.peek()==c) q.poll();
				else return "NO";
			} 
		}
		if(!q.isEmpty()) return "NO";
		return answer;
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		String s1 = sc.next();
		String s2 = sc.next();
		System.out.print(Solution(s1,s2));
	} 
}
```