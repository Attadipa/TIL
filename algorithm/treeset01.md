# K번째 큰 수

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비


### 내 풀이

```java
import java.util.ArrayList;
import java.util.Comparator;
import java.util.HashSet;
import java.util.Scanner;

public class Main {
	
	public static int Solution(int n, int k, int[] arr) {
		
		HashSet<Integer> set = new HashSet<>();
		int sum = 0;
		for(int i = 0 ; i<n-2 ; i++) {
			for(int j = i+1 ; j<n-1 ; j++) {
				for(int m = j+1 ; m<n ; m++) {
					sum = arr[i]+arr[j]+arr[m];
					set.add(sum);
				}
			}
		}
		
		ArrayList<Integer> list = new ArrayList<>(set);
		list.sort(Comparator.reverseOrder());
		int cnt = 0;
		for(int i : list) {
			cnt++;
			if(cnt==k) return i;
		} return -1;
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int k = sc.nextInt();
		int[] arr = new int[n];
		for(int i =0;i<n;i++) {
			arr[i] = sc.nextInt();
		}
		System.out.print(Solution(n,k,arr));
	} 
}
```
