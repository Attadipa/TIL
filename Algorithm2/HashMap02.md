# 아나그램

HashMap 활용 문제

내 풀이 : 불필요한 연산은 최대한 배제할 수 있도록 고민필요
```java
import java.util.HashMap;
import java.util.Scanner;

public class Main {
	
	public static String Solution(String s1, String s2) {
		HashMap<Character, Integer> map1 = new HashMap<>();
		HashMap<Character, Integer> map2 = new HashMap<>();
		for(char c : s1.toCharArray()) map1.put(c, map1.getOrDefault(c, 0)+1);
		for(char c : s2.toCharArray()) map2.put(c, map2.getOrDefault(c, 0)+1);

		for(char c : map1.keySet()) {
			if(!map2.containsKey(c) || map1.get(c) != map2.get(c)) return "NO";
		}
		return "YES";
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		String s1 = sc.next();
		String s2 = sc.next();
		System.out.println(Solution(s1,s2));
	} 
}
```

해설
```java
import java.util.HashMap;
import java.util.Scanner;

public class Main {
	
	public static String Solution(String s1, String s2) {
		String answer = "YES";
		HashMap<Character, Integer> map = new HashMap<>();
		for(char c : s1.toCharArray()) {
			map.put(c, map.getOrDefault(c, 0)+1);
		}
		for(char c : s2.toCharArray()) {
			if(!map.containsKey(c) || map.get(c)==0) return "NO";
			map.put(c, map.get(c)-1);
		}
		return answer;
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		String s1 = sc.next();
		String s2 = sc.next();
		System.out.println(Solution(s1,s2));
	} 
}
```