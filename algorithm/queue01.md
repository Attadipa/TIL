# 공주 구하기

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비


Queue활용(구현체는 LinkedList)

내 풀이

```java
import java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;

public class Main {
	
	public static int Solution(int n, int k) {
		Queue<Integer> q = new LinkedList<>();
		for(int i = 1 ; i<=n ; i++) q.offer(i);
		int cnt = 0;
		while(q.size()>1) {
			cnt++;
			if(cnt==k) {
				q.poll();
				cnt=0;
				continue;
			}
			q.offer(q.poll());
		}
		return q.poll();
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int k = sc.nextInt();
		System.out.print(Solution(n,k));
	} 
}
```