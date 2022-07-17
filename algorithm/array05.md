# 뒤집은 소수

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

풀이

```java
import java.util.Scanner;

public class Main {
    public static int solution(int n, int[] arr) {
    	int sum = 0;
    	int val = 0;
    	for(int num : arr) {
    		if(num == 1) {
    			val++;
    			sum+=val;
    		}
    		else val=0;
    	}
    	return sum;
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] arr = new int[n];
        for(int i  = 0 ;  i<n ; i++) {
        	arr[i] = sc.nextInt();
        }
        System.out.println(solution(n,arr));
    }
}
```