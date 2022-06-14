# 결혼식

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

내 풀이 ( 시간대별로 존재하는 사람 카운팅해서 배열에 저장 )

```java
import java.util.ArrayList;
import java.util.Scanner;

class Person implements Comparable<Person>{
	int s;
	int e;
	Person(int s, int e){
		this.s = s;
		this.e = e;
	}
	@Override
	public int compareTo(Person o) {
		return this.s - o.s;
	}
}

public class Main {
	
	public static void solution(int n, ArrayList<Person> list) { 
		int[] arr = new int[72];
		for(Person m : list) {
			for(int i = m.s ; i<m.e ; i++) {
				arr[i]++;
			}
		}
		int max = 0;
		for(int i : arr) {
			max = Math.max(max, i);
		} System.out.println(max);
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		ArrayList<Person> list = new ArrayList<Person>();
		for(int i = 0 ; i<n ; i++) {
			int s = sc.nextInt();
			int e = sc.nextInt();
			list.add(new Person(s,e));
		}
		solution(n,list);
	}
}
```

해설

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.Scanner;

class Time implements Comparable<Time>{
	int t;
	char se;
	Time(int t, char se){
		this.t = t;
		this.se = se;
	}
	@Override
	public int compareTo(Time o) {
		if(this.t != o.t) return this.t - o.t;
		else return this.se-o.se;
	}
}

public class Main {
	
	public static void solution(ArrayList<Time> list) { 
		Collections.sort(list);
		int cnt = 0;
		int max = 0;
		for(Time time : list) {
			if(time.se=='s') {
				cnt++;
				max = Math.max(max, cnt);
			}
			else cnt--;
		}
		System.out.println(max);
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		ArrayList<Time> list = new ArrayList<Time>();
		for(int i = 0 ; i<n ; i++) {
			int t = sc.nextInt();
			list.add(new Time(t,'s'));
		    t = sc.nextInt();
			list.add(new Time(t,'e'));
		}
		solution(list);
	}
}
```