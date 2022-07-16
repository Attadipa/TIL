# 가장 짧은 문자거리

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

풀이

```java
import java.util.Arrays;
import java.util.Scanner;

public class Main {
    public static String solution(String str, char ch) {
    	int[] arr = new int[str.length()];
    	int p = 1000;
    	for(int i = 0 ; i<str.length() ; i++) {
    		if(str.charAt(i)==ch) {
    			p=0;
    			arr[i] = p;
    		}
    		else {
    			p++;
    			arr[i] = p;
    		}
    	}
    	for(int i = str.length()-1 ; i>=0 ; i--) {
    		if(str.charAt(i)==ch) {
    			p=0;
    			arr[i] = p;
    		}
    		else {
    			p++;
    			arr[i] = Math.min(arr[i], p);
    		}
    	}
    	String answer = "";
    	for(int i : arr) answer += i+" ";
    	return answer;
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String str = sc.next();
        char ch = sc.next().charAt(0);
        System.out.println(solution(str,ch));
    }
}
```