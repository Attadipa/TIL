# 학급회장

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

```java
import java.util.HashMap;
import java.util.Scanner;

public class Main {
	
	public static char Solution(int n, String s) {
		HashMap<Character, Integer> map = new HashMap<>();
		for(char c : s.toCharArray()) {
			map.put(c, map.getOrDefault(c, 0)+1);
		} 
		int max = 0;
		char answer = ' ';
		for(char c : map.keySet()) {
			if(max < map.get(c)){
				max = map.get(c);
				answer = c;
			}
		}return answer;
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		String s = sc.next();
		System.out.println(Solution(n,s));
	} 
}
```