# LRU 

### 카카오 기출 변형

내 풀이1 : LinkedList 추가로 사용

```java
import java.util.LinkedList;
import java.util.Scanner;

public class Main {
	public static String Solution(int s, int n, int[] arr) {
		LinkedList<Integer> q = new LinkedList<>();
		for(int i=0 ; i<n ; i++) {
			if(q.contains((Integer)arr[i])) {
				q.remove((Integer)arr[i]);
				q.offer((Integer)arr[i]);
			} else {
				q.offer((Integer)arr[i]);
				if(q.size()>s) q.poll();
			}
		}
		String answer = "";
		for(int i=q.size()-1 ; i>=0 ; i--) {
			answer += (int)q.get(i) + " ";
		} return answer;
		
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int s = sc.nextInt();
		int n = sc.nextInt();
		int[] arr = new int[n];
		for(int i = 0; i<n ; i++) {
			arr[i] = sc.nextInt();
		}
		System.out.print(Solution(s,n,arr));
	} 
}
```

내 풀이2 : 배열로만 풀이

```java
import java.util.Scanner;

public class Main {
	public static String Solution(int s, int n, int[] arr) {
		int[] cache = new int[s];
		for(int i = 0 ; i<n ;i++) {
			int p = s-1;
			for(int j = 0 ; j<s ;j++) {
				if(cache[j]==arr[i] || cache[j]==0) {
					p = j;
					break;
				}
			}
			for(int j = p ; j>0 ;j--) {
				cache[j] = cache[j-1];
			}
			cache[0]=arr[i];
		}
		String answer = "";
		for(int i : cache) answer += i+" ";
		return answer;
		
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int s = sc.nextInt();
		int n = sc.nextInt();
		int[] arr = new int[n];
		for(int i = 0; i<n ; i++) {
			arr[i] = sc.nextInt();
		}
		System.out.print(Solution(s,n,arr));
	} 
}

```