# 모든 아나그램 찾기

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

HashMap과 sliding window 복합문제  

### 내 풀이

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

