# 유효한 팰린드롬

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

풀이1 (replaceAll 정규식이용)

```java
import java.util.Scanner;

public class Main {
    public static int solution(String str) {
    	str = str.toUpperCase().replaceAll("[^0-9]", "");
    	int num = Integer.parseInt(str);
    	return num;
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String str = sc.nextLine();
        System.out.println(solution(str));
    }
}
```

풀이2 (isDigit()이용)

```java
import java.util.Scanner;

public class Main {
    public static int solution(String str) {
    	String tmp = "";
    	for(int i = 0 ; i<str.length();i++) {
    		if(Character.isDigit(str.charAt(i))) tmp += str.charAt(i);
    	}
    	int answer = Integer.parseInt(tmp);
    	return answer;
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String str = sc.nextLine();
        System.out.println(solution(str));
    }
}
```

풀이3 (메서드 최대한 안쓰기)

```java
import java.util.Scanner;

public class Main {
    public static int solution(String str) {
    	int answer = 0;
    	for(char c :str.toCharArray()) {
    		if(c>=48 && c<=57) answer = answer*10 + (c-48);
    	}
    	return answer;
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String str = sc.nextLine();
        System.out.println(solution(str));
    }
}
```