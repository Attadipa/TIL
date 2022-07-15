# 뒤집은 소수

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

풀이

```java
import java.util.Scanner;

public class Main {
	public static boolean isPrime(int num) {
    	int[] prime = new int[num+1];
        for(int i = 2 ; i<=num ; i++) {
        	if(prime[i]==0) {
        		prime[i]=1;
        		for(int j = i*2 ; j<=num ; j=j+i) {
        			prime[j]=-1;
        		}
        	}
        }
        if(prime[num]==1) return true;
        else return false;
	}
    public static void solution(int n, int[] arr) {
        for(int i = 0 ; i<n ; i++) {
        	int num = arr[i];
           	int temp = 0;
        	while(num>0) {
	            int t = num%10;
	            temp = temp*10+t; 
	            num = num/10;
        	}
        	if(isPrime(temp)) System.out.print(temp+" ");
        }
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] arr = new int[n];
        for(int i = 0 ; i<n ; i++) {
            arr[i] = sc.nextInt();
        }
        solution(n,arr);
    }
}
```