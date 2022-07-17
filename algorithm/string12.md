# 암호(replace(),parseInt(string,2))

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

풀이1 (이진수 shifting원리 이용)

```java
import java.util.Scanner;

public class Main {
    public static void solution(int n, String str) {
    	String[] words = new String[n];
    	for(int i = 0 ; i<n ; i++) {
    		String tmp = str.substring(0,7);
    		words[i] = tmp;
    		str= str.substring(7);
    	}
    	for(String w : words) {
    		int askii = 0;
        	for(int i = 0 ; i<w.length() ; i++) {
        		if(w.charAt(i)=='#') askii = askii*2+1;
        		else askii = askii*2;
        	}
        	System.out.print((char)askii);
    	}
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        String str = sc.next();
        solution(n,str);
    }
}
```

풀이2(replace(),parseInt(string,2) 활용)

```java
import java.util.Scanner;

public class Main {
    public static String solution(int n, String str) {
    	String answer = "";
    	for(int i = 0 ; i<n ; i++) {
    		String tmp = str.substring(0,7).replace('#', '1').replace('*','0');
    		str = str.substring(7);
    		int num = Integer.parseInt(tmp,2);
    		char ch = (char)num;
    		answer += ch;
    	}
    	return answer;
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        String str = sc.next();
        System.out.println(solution(n,str));
    }
}
```