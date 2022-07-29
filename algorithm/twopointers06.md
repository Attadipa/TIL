# 연속부분수열

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비


풀이
 
 
```java
import java.util.Scanner;

public class Main {
    public static int solution(int n, int m, int[] arr) { 
    	int sum = arr[0];
    	int p1 = 0;
    	int p2 = 0;
    	int cnt = 0;
        while(p2<=n-1) {
        	if(sum<m) sum+=arr[++p2];
        	else if(sum>m) sum-=arr[p1++];
        	else {
        		cnt++;
        		sum-=arr[p1++];
        	}
        }
        return cnt;
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int m = sc.nextInt();
        int[] arr = new int[n+1];
        for(int i = 0 ; i<n ;i++) {
        	arr[i] = sc.nextInt();
        }
        System.out.println(solution(n,m,arr));
        
    }
}
```