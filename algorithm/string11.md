# 문자열압축

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

풀이1

```java
import java.util.Scanner;

public class Main {
    public static String solution(String str) {
    	String answer = "";
    	char[] arr = str.toCharArray();
    	answer += arr[0];
    	int cnt = 1;
    	for(int i = 1 ; i<arr.length ; i++) {
    		if(arr[i] != arr[i-1]) {
    			if(cnt>1) answer+=cnt;
    			answer+=arr[i];
    			cnt=1;
    		}else {
    			cnt++;
    			if(i==arr.length-1) answer += cnt;
    		}
    	}
    	return answer;
    	
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String str = sc.next();
        System.out.println(solution(str));
    }
}
```

풀이2

```java
import java.util.Scanner;

public class Main {
    public static String solution(String str) {
    	String answer = "";
    	str  = str + " ";
    	int cnt = 1;
    	for(int i = 0 ;i<str.length()-1;i++) {
    		if(str.charAt(i)==str.charAt(i+1)) cnt++;
    		else {
    			answer += str.charAt(i);
    			if(cnt>1) answer += cnt;
    			cnt = 1;
    		}
    	}
    	return answer;
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String str = sc.next();
        System.out.println(solution(str));
    }
}
```