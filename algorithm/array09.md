# 임시반장 정하기

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

풀이

```java
import java.util.HashSet;
import java.util.Scanner;
import java.util.Set;

public class Main {
    public static int solution(int n, int[][] arr) {
    	Set<Integer> set = new HashSet<>();
    	int[] fc = new int[n+1];
    	int max = 0;
    	int answer = 0;
        for(int i = 1 ; i<=n; i++) {
            for(int j = 1 ; j<=5; j++) {
                for(int k = 1 ; k<=n; k++) {
                	if(arr[i][j]==arr[k][j]) set.add(k);
                }
            }
            fc[i] = set.size()-1;
            if(max<fc[i]) {
            	max = fc[i];
            	answer = i;
            }
            set.clear();
        }
        return answer;
        
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[][] arr = new int[n+1][n+1];
        for(int i = 1 ; i<=n; i++) {
            for(int j = 1 ; j<=n; j++) {
                arr[i][j] = sc.nextInt();
            }
        }
        System.out.println(solution(n,arr));
    }
}
```