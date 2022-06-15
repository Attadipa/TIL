# 최대 수입 스케쥴(PriorityQueue 응용문제)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

해설

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.PriorityQueue;
import java.util.Scanner;

class Lecture implements Comparable<Lecture>{
	int money;
	int time;
	public Lecture(int money, int time) {
		this.money = money;
		this.time = time;
	}
	@Override
	public int compareTo(Lecture o) {
		return o.time-this.time;
	}
	
}

public class Main {
	static int n,max,answer = 0;
	public static int solution(ArrayList<Lecture> list) { 
		PriorityQueue<Integer> pQ = new PriorityQueue<>(Collections.reverseOrder());
		Collections.sort(list);
		int j = 0;
		for(int i = max; i>0 ; i--) {
			for(; j<n ; j++) {
				if(list.get(j).time<i) break;
				pQ.offer(list.get(j).money);
			}
			if(!pQ.isEmpty()) answer += pQ.poll();
		}
		return answer;
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		n = sc.nextInt();
		ArrayList<Lecture> list = new ArrayList<Lecture>();
		for(int i = 0 ; i<n ; i++) {
			int m = sc.nextInt();
		    int t = sc.nextInt();
			list.add(new Lecture(m,t));
			if(max<t) max = t;
			
		}
		System.out.println(solution(list));
	}
}
```