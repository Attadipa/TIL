# 뮤직비디오(결정알고리즘)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

1. 사실상 UpDown게임의 확장판이다.
2. 지정된 용량의 CD 최소필요갯수를 찾는 로직만 빼서 메서드로 만드는 방법도 있다.

내 풀이

```java
import java.util.Scanner;


public class Main {

	public static int solution(int n, int m, int[] arr) {
		int answer = 0;
		int lt = arr[0];
		for(int i : arr) {
			if(lt<i) lt=i;
		}
		int rt = 0;
		for(int i : arr) rt += i;

		while(lt<=rt) {
			int size = (lt+rt)/2;
			int sum = 0;
			int cnt = 1;
			for(int i : arr) {
				sum+=i;
				if(sum>size) {
					cnt++;
					sum=i;
				}
			}
			System.out.println(cnt);
			if(cnt<=m) {
				if(cnt==m) answer = size;
				rt=size-1;
			} else lt=size+1;
		}
		return answer;
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int m = sc.nextInt();
		int[] arr = new int[n];
		for(int i = 0; i<n ; i++) {
			arr[i] = sc.nextInt();
		}
		System.out.println(solution(n,m,arr));
	}
}
```