# 씨름 선수

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비


내 풀이(이중 반복문 활용 but 시간복잡도가 n의 제곱으로 너무 커진다.)

```java
import java.util.Scanner;

class Person{
	int h;
	int w;
	Person(int h, int w){
		this.h = h;
		this.w = w;
	}
}

public class Main {
	
	static int[] check;
	
	public static void solution(int n, Person[] arr) { 
		for(int i = 0 ; i <n ; i++) {
			for(int j = 0; j < n ; j++) {
				if(arr[i].h<arr[j].h && arr[i].w<arr[j].w) {
					check[i]=-1;
				}
			}
		}
		int cnt = 0 ;
		for(int i : check) {
			if(i==0) cnt++;
		}
		System.out.println(cnt);
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		check = new int[n];
		Person[] arr = new Person[n];
		for(int i = 0 ; i<n ; i++) {
			int h = sc.nextInt();
			int w = sc.nextInt();
			arr[i] = new Person(h,w);
		}
		solution(n,arr);
	}
}
```

해설(키로 내림차순 정렬 후 몸무게의 최대값 갱신될 때 마다 카운팅)

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.Scanner;

class Person implements Comparable<Person>{
	int h;
	int w;
	Person(int h, int w){
		this.h = h;
		this.w = w;
	}
	
	@Override
	public int compareTo(Person o) {
		return	o.w-this.w;
	}
}

public class Main {
	
	public static void solution(int n, ArrayList<Person> list) { 
		Collections.sort(list);
		int max = Integer.MIN_VALUE;
		int cnt = 0 ;
		for(Person p : list) {
			if(p.w>max) {
				max = p.w;
				cnt++;
			}
		}
		System.out.println(cnt);
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		ArrayList<Person> list = new ArrayList<Person>();
		for(int i = 0 ; i<n ; i++) {
			int h = sc.nextInt();
			int w = sc.nextInt();
			list.add(new Person(h,w));
		}
		solution(n,list);
	}
}
```