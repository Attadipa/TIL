# 멘토링

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

풀이

```java
import java.util.Scanner;

public class Main {
    public static int solution(int n, int m, int[][] arr) {
    	int answer = 0;
    	for(int i = 1 ; i<=n ; i++) {
    		for(int j = 1 ; j<=n ; j++) {
    			boolean isMent = true;
    			for(int k = 1 ; k<=m ; k++) {
        			int ranki = 0;
        			int rankj = 0;
        			for(int s = 1 ; s<=n ; s++) {
	        			if(arr[k][s]==i) ranki = s;
	        			if(arr[k][s]==j) rankj = s;
        			}
        			if(ranki>=rankj) {
        				isMent = false;
        				break;
        			}
        		}
    			if(isMent) answer++;
    		}
    	}
        return answer;
        
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int m = sc.nextInt();
        int[][] arr = new int[m+1][n+1];
        for(int i = 1 ; i<=m; i++) {
            for(int j = 1 ; j<=n; j++) {
                arr[i][j] = sc.nextInt();
            }
        }
        System.out.println(solution(n,m,arr));
    }
}
```