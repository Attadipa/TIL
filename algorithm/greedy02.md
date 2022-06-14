# 회의실 배정

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

정렬이 핵심이다.

해설

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.Scanner;

class Meeting implements Comparable<Meeting>{
	int s;
	int e;
	Meeting(int s, int e){
		this.s = s;
		this.e = e;
	}
	@Override
	public int compareTo(Meeting o) {
		if(this.e-o.e!=0) return this.e-o.e;
		else return this.s-o.s;
	}
}

public class Main {
	
	public static void solution(int n, ArrayList<Meeting> list) { 
		Collections.sort(list);
		int cnt = 0;
		int ns = 0;
		for(Meeting m : list) {
			if(ns<=m.s) {
				ns = m.e;	
				cnt++;
			}
		}
		System.out.println(cnt);
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		ArrayList<Meeting> list = new ArrayList<Meeting>();
		for(int i = 0 ; i<n ; i++) {
			int s = sc.nextInt();
			int e = sc.nextInt();
			list.add(new Meeting(s,e));
		}
		solution(n,list);
	}
}
```