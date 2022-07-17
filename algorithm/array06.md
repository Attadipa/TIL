# 등수 구하기

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

풀이1 (이중반복문 => 시간복잡도 : O(n^2))

```java
import java.util.Scanner;

public class Main {
    public static String solution(int n, int[] arr) {
    	int[] answer = new int[n];
    	for(int i = 0 ; i<n ; i++) {
    		int cnt = 0;
        	for(int j = 0 ; j<n ; j++) {
        		if(arr[i]<arr[j]) cnt++;
        	}
        	answer[i] = cnt+1;
    	}
    	String tmp = "";
    	for(int num : answer) tmp += num + " ";
    	return tmp;
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] arr = new int[n+1];
        for(int i  = 0 ;  i<n ; i++) {
        	arr[i] = sc.nextInt();
        }
        System.out.println(solution(n,arr));
    }
}
```

풀이2(시간복잡도 : O(n))

```java
import java.util.Scanner;

public class Main {
    public static String solution(int n, int[] arr, int[] cnt) {
        int[] rank = new int[101];
		int sum = 1;
    	for(int i = cnt.length-1 ; i>=0 ; i--) {
    		if(cnt[i]!=0) {
    			rank[i] = sum;
    			sum += cnt[i];
    		}
    	}
    	String answer = "";;
    	for(int num : arr) {
    		answer += rank[num] + " ";
    	}
    	return answer;
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] arr = new int[n];
        int[] cnt = new int[101];
        for(int i  = 0 ;  i<n ; i++) {
        	arr[i] = sc.nextInt();
        	cnt[arr[i]]++;
        }
        System.out.println(solution(n,arr,cnt));
    }
}
```