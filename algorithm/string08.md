# 유효한 팰린드롬

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

풀이 (lt,rt 포인터 이용)

```java
import java.util.Scanner;

public class Main {
    public static String solution(String str) {
    	str = str.toUpperCase();
    	int lt = 0;
    	int rt = str.length()-1;
    	while(lt<rt) {
    		if(!Character.isAlphabetic(str.charAt(lt))) lt++;
    		else if(!Character.isAlphabetic(str.charAt(rt))) rt--;
    		else if(str.charAt(lt)!=str.charAt(rt)) return "NO";
    		else {
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

풀이2 (replaceAll 정규식이용)

```java
import java.util.Scanner;

public class Main {
    public static String solution(String str) {
    	str = str.toUpperCase().replaceAll("[^A-Z]", "");
    	String rev = new StringBuilder(str).reverse().toString();
    	if(rev.equals(str)) return "YES";
    	else return "NO";
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String str = sc.nextLine();
        System.out.println(solution(str));
    }
}
```