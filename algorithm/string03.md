# 문장 속 단어

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

풀이

```java
import java.util.Scanner;

public class Main {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		String str = sc.nextLine();
		int max = 0;
		int pos = 0;
		String answer = "";
		while((pos=str.indexOf(' '))!=-1) {
			String temp = str.substring(0,pos);
			if(temp.length()>max) {
				max = temp.length();
				answer = temp;
			}
			str = str.substring(pos+1);
		}
		if(str.length()>max) System.out.println(str);
		else System.out.println(answer);
	}
}
```