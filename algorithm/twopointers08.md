# 연속된 자연수의 합(수학)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

풀이1
 
```java
import java.util.Scanner;

public class Main {
    public static int solution(int n) { 
    	int sum = 1;
    	int num = 1;
    	int cnt = 0;
    	while(sum<n) {
    		sum += (++num);
    		if((n-sum)%num==0) cnt++;
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

풀이2
```java
import java.util.Scanner;

public class Main {
    public static int solution(int n) { 
    	int num = 1;
    	int cnt = 0;
    	n--;
    	while(n>0) {
    		n -= (++num);
    		if(n%num==0) cnt++;
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