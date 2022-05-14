# 모든 아나그램 찾기

HashMap과 sliding window 복합문제  

내 풀이

1.isEquals()를 통해 map간의 비교가 가능하다는 걸 알게되었음

2.불필요한 연산을 줄이자. ex) s1의 char배열화


```java
import java.util.HashMap;
import java.util.Scanner;

public class Main {
	
	public static int Solution(String s1, String s2) {
		HashMap<Character,Integer> map1 = new HashMap<>();
		HashMap<Character,Integer> map2 = new HashMap<>();
		char[] arr1 = s1.toCharArray();
		char[] arr2 = s2.toCharArray();
		int n = s2.length();
		for(int i =0 ; i<n-1 ; i++) map1.put(arr1[i], map1.getOrDefault(arr1[i],0)+1);
		for(int i =0 ; i<n ; i++) map2.put(arr2[i], map2.getOrDefault(arr2[i],0)+1);
		
		int cnt=0;
		int rt=n-1;
		int lt=0;
		while(rt<s1.length()) {
			map1.put(arr1[rt], map1.getOrDefault(arr1[rt],0)+1);
			rt++;
			boolean isAn = true;
			for(char c : map2.keySet()) {
				if(!map1.containsKey(c) || map1.get(c)!=map2.get(c)) {
					isAn = false;
					break;
				}
			}
			if(isAn) cnt++;
			map1.put(arr1[lt], map1.get(arr1[lt])-1);
			if(map1.get(arr1[lt])==0) map1.remove(arr1[lt]);
			lt++;
		} return cnt;
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		String s1 = sc.next();
		String s2 = sc.next();
		System.out.print(Solution(s1,s2));
	} 
}
```

해설

```java
import java.util.HashMap;
import java.util.Scanner;

public class Main {
	
	public static int Solution(String s1, String s2) {
		int answer = 0;
		HashMap<Character,Integer> map1 = new HashMap<>();
		HashMap<Character,Integer> map2 = new HashMap<>();
		for(char c : s2.toCharArray()) map2.put(c,map2.getOrDefault(c, 0)+1);
		int L = s2.length()-1;
		for(int i=0 ; i<L ; i++) map1.put(s1.charAt(i),map1.getOrDefault(s1.charAt(i), 0)+1);
		int lt = 0;
		
		for(int rt=L ; rt<s1.length() ; rt++) {
			map1.put(s1.charAt(rt),map1.getOrDefault(s1.charAt(rt), 0)+1);
			if(map1.equals(map2)) answer++;
			map1.put(s1.charAt(lt),map1.get(s1.charAt(lt))-1);
			if(map1.get(s1.charAt(lt))==0) map1.remove(s1.charAt(lt));
			lt++;
		} return answer;
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		String s1 = sc.next();
		String s2 = sc.next();
		System.out.print(Solution(s1,s2));
	} 
}
```
