# 특정 문자 뒤집기

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

풀이(직접 뒤집기)

```java
import java.util.Scanner;

public class Main {
	public static void solution(String str) {
		char[] arr = str.toCharArray();
		int lt = 0;
		int rt = str.length()-1;
		while(lt<rt) {
			if(!Character.isAlphabetic(arr[lt])) lt++;
			else if(!Character.isAlphabetic(arr[rt])) rt--;
			else {
				char tmp =arr[lt];
				arr[lt] = arr[rt];
				arr[rt] = tmp;
				lt++;
				rt--;				
			}

		}
		System.out.println(new String(arr));
	}
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		String str = sc.nextLine();
		solution(str);
	}
}
```