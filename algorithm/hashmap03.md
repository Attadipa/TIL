# 매출액의 종류

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

HashMap과 sliding window 복합문제

```java
import java.util.ArrayList;
import java.util.HashMap;
import java.util.Scanner;

public class Main {
	
	public static ArrayList<Integer> Solution(int n, int k, int[] arr) {
		ArrayList<Integer> list = new ArrayList<>();
		HashMap<Integer,Integer> map = new HashMap<>();
		for(int i=0;i<k-1 ;i++) {
			map.put(arr[i], map.getOrDefault(arr[i], 0)+1);
		}
		int lt=0;
		for(int rt=k-1; rt<n; rt++) {
			map.put(arr[rt], map.getOrDefault(arr[rt], 0)+1);
			list.add(map.size());
			map.put(arr[lt], map.get(arr[lt])-1);
			if(map.get(arr[lt])==0) map.remove(arr[lt]);
			lt++;
		} return list;
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int k = sc.nextInt();
		int[] arr = new int[n];
		for(int i =0; i<n ;i++) {
			arr[i] = sc.nextInt();
		}
		for(int i : Solution(n,k,arr))
		System.out.print(i+" ");
	} 
}
```