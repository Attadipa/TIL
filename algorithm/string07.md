# 회문 문자열

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

풀이(lt,rt 포인터 이용)

```java
import java.util.Scanner;

public class Main {
    public static String solution(String str) {
    	str = str.toUpperCase();
    	int lt = 0;
    	int rt = str.length()-1;
    	while(lt<rt) {
    		if(str.charAt(lt)!=str.charAt(rt)) return "NO";
    		else{
        		lt++;
        		rt--;
    		}
    	}
    	return "YES";
    	
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String str = sc.nextLine();
        System.out.println(solution(str));
    }
}
```

풀이2(StringBuilder이용)

```java
import java.util.Scanner;

public class Main {
    public static String solution(String str) {
    	str = str.toUpperCase();
    	String rev = new StringBuilder(str).reverse().toString();
    	if(!str.equals(rev)) return "NO";
    	return "YES";
    	
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String str = sc.nextLine();
        System.out.println(solution(str));
    }
}
```