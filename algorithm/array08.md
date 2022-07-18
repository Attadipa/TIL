# 봉우리

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

풀이

```java
import java.util.Scanner;

public class Main {
    public static int solution(int n, int[][] arr) {
    	int cnt = 0;
    	int[] dx = {1,-1,0,0};
    	int[] dy = {0,0,1,-1};
        for(int i = 1 ; i<=n; i++) {
            for(int j = 1 ; j<=n; j++) {
            	boolean isPeak = true;
            	for(int k = 0 ; k<4; k++) {
            		int nx = i+dx[k];
            		int ny = j+dy[k];
            		if(arr[i][j] <= arr[nx][ny]) {
            			isPeak = false;
            			break;
            			
            		}
                }
            	if(isPeak) cnt++;
            }
        }
        return cnt;
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[][] arr = new int[n+2][n+2];
        for(int i = 1 ; i<=n; i++) {
            for(int j = 1 ; j<=n; j++) {
                arr[i][j] = sc.nextInt();
            }
        }
        System.out.println(solution(n,arr));
    }
}
```