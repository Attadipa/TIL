# 좌표 정렬

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

해설 참고한 풀이(별도의 클래스와 정렬기준 만들기)

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.Scanner;

class Pair implements Comparable<Pair>{
	public int x;
	public int y;
	
	public Pair(int x, int y) {
		this.x = x;
		this.y = y;
	}
	@Override
	public int compareTo(Pair p){
		if(this.x!=p.x) return this.x-p.x;
		else return this.y-p.y;
	}
	@Override
	public String toString() {
		return this.x+" "+this.y;
	}
	
}
public class Main {
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		ArrayList<Pair> list = new ArrayList<>();
		for(int i = 0; i<n ; i++) {
			int x = sc.nextInt();
			int y = sc.nextInt();
			list.add(new Pair(x,y));
		}
		Collections.sort(list);
		for(Pair p : list) System.out.println(p);
	}
}
```