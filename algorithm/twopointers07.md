# 연속된 자연수의 합

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

풀이
 
```java
import java.util.Scanner;

public class Main {
    public static int solution(int n) { 
    	int sum = 1;
    	int p1 = 1;
    	int p2 = 1;
        int cnt = 0;
        while(p2<=(n+1)/2) {
        	if(sum<n) sum+=(++p2);
        	else if(sum>n) sum-=(p1++);
        	else {
        		cnt++;
        		sum-=(p1++);
        	}
        }
        return cnt;
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        System.out.println(solution(n));
        
    }
}
```