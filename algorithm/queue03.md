# 응급실

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

Queue활용(구현체는 LinkedList)

내 풀이

1. 따로 person 클래스 만들어서 활용하는 방법도 생각해보자

```java
import java.util.HashMap;
import java.util.LinkedList;
import java.util.Map.Entry;
import java.util.Queue;
import java.util.Scanner;

public class Main {
	public static int Solution(int n, int m, int[] arr) {
		Queue<Entry<Integer,Integer>> q = new LinkedList<>();
		HashMap<Integer,Integer> map = new HashMap<>();
		for(int i = 0; i<n ; i++) map.put(i,arr[i]);
		for(Entry<Integer,Integer> e : map.entrySet()) q.offer(e);
		int cnt = 0;
		while(!q.isEmpty()) {
			boolean isMax = true;
			for(Entry<Integer,Integer> e : q) {
				if(q.peek().getValue()<e.getValue()) {
					q.offer(q.poll());
					isMax=false;
					break;
				}
			}	
			if(isMax) {
				cnt++; 
				if(q.poll().getKey()==m) return cnt;
			}
		}
		return cnt;
		
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int m = sc.nextInt();
		int[] arr = new int[n];
		for(int i = 0; i<n ; i++) {
			arr[i] = sc.nextInt();
		}
		System.out.print(Solution(n,m,arr));
	} 
}
```